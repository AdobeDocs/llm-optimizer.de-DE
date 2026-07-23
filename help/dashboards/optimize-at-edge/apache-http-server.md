---
title: Optimieren unter Edge - Apache HTTP-Server
description: Erfahren Sie, wie Sie Apache HTTP Server (selbst gehosteter Reverse-Proxy) BYOCDN für Optimize bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: d7e723161836027dcdde931378f5d0f776a1ecfc
workflow-type: tm+mt
source-wordcount: 585
ht-degree: 32%

---


# Apache HTTP Server

Diese Konfiguration gilt, wenn der Apache-HTTP-Server als Reverse-Proxy vor Ihrem Ursprung fungiert (ein selbst gehostetes Setup, **ohne** AEM Dispatcher). Agent-Traffic (Anfragen von KI-Bots und LLM-Benutzeragenten) wird an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weitergeleitet. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

Bei der Integration handelt es sich um einen Satz nativer Apache-`Include`-Dateien, für die kein Code oder Worker bereitgestellt werden muss. Sie laden drei Dateien herunter, legen Ihren API-Schlüssel fest und fügen Ihrem virtuellen Host zwei `Include` hinzu.

**Voraussetzungen**

Bevor Sie die Apache-Routing-Regeln einrichten, stellen Sie sicher, dass Sie Folgendes haben:

* Apache HTTP-Server 2.4 oder höher mit diesen Modulen aktiviert: `proxy`, `proxy_http`, `ssl`, `rewrite`, `headers`, `env` und `setenvif`.
* Zugriff auf Ihre Apache-Konfiguration (die `<VirtualHost>` für Ihre Site) und die Möglichkeit, Apache neu zu laden.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Konfiguration

**1. Laden Sie die Konfigurationsdateien herunter**

Laden Sie die drei Edge Optimize Include-Dateien aus dem [Optimize at Edge Code Samples-Repository](https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/apache) herunter und legen Sie sie in einem Verzeichnis auf Ihrem Apache-Server ab (z. B. `conf/oae/`):

| Datei | Zweck |
|------|---------|
| `oae-routing.conf` | Erkennt KI-Bots, fügt die Edge Optimize-Header ein, leitet HTML-Seitenanfragen an das Backend weiter und richtet die Cache-Isolierung und das Failover ein. |
| `oae-failover.conf` | Gibt die ursprüngliche Anfrage an Ihre Herkunft zurück, wenn Edge Optimize einen Fehler zurückgibt. |
| `domains.conf` | Aktiviert die Option „Optimieren bei Edge pro Domain“ und enthält Ihren API-Schlüssel. |

Sie müssen `oae-routing.conf` oder `oae-failover.conf` nicht ändern - verwenden Sie sie wie sie sind.

**2. Aktivieren Sie Ihre Domain und legen Sie den API-Schlüssel (`domains.conf`) fest**

Bearbeiten Sie `domains.conf` und fügen Sie pro Domain, die Sie aktivieren, eine Zeile hinzu. Ersetzen Sie den Host durch Ihre Domain und `YOUR_API_KEY` Sie durch den Schlüssel aus der LLM Optimizer-Benutzeroberfläche. Nicht aufgeführte Domains leiten den Ursprung unverändert weiter, sodass Sie jeweils nur eine Domain aktivieren können.

```
SetEnvIfExpr "%{HTTP_HOST} =~ m#(?i)^(www\.)?example\.com(:\d+)?$#" OAE_DOMAIN_ENABLED=1 OAE_API_KEY=YOUR_API_KEY
```

**3. Schließen Sie die Dateien in Ihren virtuellen Host ein**

Fügen Sie die beiden `Include` Zeilen zu Ihrem vorhandenen `<VirtualHost *:443>` hinzu. Die Routing-Datei wird **vor** Ihre Rewrite- und `ProxyPass`-Regeln; die Failover-Datei **nach)**. Im folgenden Beispiel sind die mit `#NEWLINE` markierten Zeilen die einzigen Zeilen, die Sie für „Optimieren“ bei Edge hinzufügen - alles andere (`ServerName`, `ProxyPass` und der Rest) ist Ihre bestehende, unveränderte Konfiguration.

```
Define OAE_CONF_DIR conf/oae                       #NEWLINE  directory holding the OAE include files

<VirtualHost *:443>
    ServerName www.example.com

    Include "${OAE_CONF_DIR}/oae-routing.conf"     #NEWLINE  OAE routing — BEFORE your Rewrite & ProxyPass rules

    # --- your existing rewrite rules and ProxyPass to origin ---
    ProxyPass        "/" "https://www.example.com/"
    ProxyPassReverse "/" "https://www.example.com/"

    Include "${OAE_CONF_DIR}/oae-failover.conf"    #NEWLINE  OAE failover — AFTER your ProxyPass rules
</VirtualHost>
```

**4. Apache neu laden**

Überprüfen Sie die Konfiguration und laden Sie Apache neu, um die Änderungen anzuwenden.

>[!NOTE]
>
>Bot-optimierte und menschliche Reaktionen werden automatisch in separaten Cache-Einträgen gespeichert (die Routing-Datei setzt `Vary: x-edgeoptimize-config`). Wenn Ihr Apache bereits `mod_cache` verwendet, stellen Sie sicher, dass dies `CacheQuickHandler Off` ist, sodass die Cache-Suche ausgeführt wird, nachdem die Edge Optimize-Header festgelegt wurden.

## Zulassen, dass bei Edge durch Firewall-Regeln optimiert wird (optional)

{{waf-allowlist-setup}}

## Überprüfen des Setups

Stellen Sie nach Abschluss des Setups sicher, dass Bot-Traffic an Edge Optimize weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

**1. Testen des Bot-Traffics (sollte optimiert werden)**

Simulieren Sie eine KI-Bot-Anfrage mithilfe eines Agent-basierten Benutzer-Agents:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Eine erfolgreiche Antwort enthält den `x-edgeoptimize-request-id`-Header, der bestätigt, dass die Anfrage über Edge Optimize weitergeleitet wurde:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Testen des menschlichen Traffics (sollte NICHT betroffen sein)**

Simulieren Sie eine normale menschliche Browser-Anfrage:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

Die Antwort sollte **nicht** den `x-edgeoptimize-request-id`-Header enthalten. Der Seiteninhalt und die Antwortzeit sollten nach der Aktivierung von „Optimize at Edge“ unverändert bleiben.

**3. So lassen sich die beiden Szenarien voneinander unterscheiden**

| Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Traffic (nicht betroffen) |
|---|---|---|
| `x-edgeoptimize-request-id` | Vorhanden – enthält eine eindeutige Anfrage-ID | Abwesend |
| `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover stattgefunden hat (Wert: `1`) | Abwesend |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
