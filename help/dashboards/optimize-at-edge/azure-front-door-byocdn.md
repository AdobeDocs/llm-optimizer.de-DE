---
title: Optimieren bei Edge - Azure-Haustür (BYOCDN)
description: Erfahren Sie, wie Sie Azure Front Door BYOCDN for Optimize bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-07-15T17:40:54.797Z'
TQID: 'https://experienceleague.adobe.com/fe-kultqzWQdRdcUjzfNs21UpL6m5zcoAmaQyMMv5kk'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 768
ht-degree: 24%

---


# Azure-Haustür (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

Azure Front Door führt keinen benutzerdefinierten Code am Edge aus. Das Routing wird mithilfe eines **Regelsatzes** zusammen mit einer dedizierten **Ursprungsgruppe** für Edge Optimizer konfiguriert. Das Failover wird durch die prioritätsbasierten Ursprungsgruppen-Konsistenzprüfungen der Azure-Fronttür durchgeführt.

**Voraussetzungen**

Bevor Sie die Azure-Routing-Regeln für die Haustür einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Zugriff auf Ihr Azure-Fronttürprofil.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Schritt 1: Erstellen einer Ursprungsgruppe für Edge Optimize

Ihr Azure-Haustürprofil verfügt bereits über eine standardmäßige Ursprungsgruppe, die auf Ihren Ursprung verweist. Erstellen Sie **neue** Ursprungsgruppe für Edge Optimize:

* **Name:** `edge-optimize-origin-group`
* **Ursprünge (prioritätsbasiertes Failover):**
   * **Priorität 1** — `live.edgeoptimize.net` (Ursprungs-Host-Kopfzeile: `live.edgeoptimize.net`)
   * **Priorität 2** - Ihr Domain-Endpunkt (z. B. `www.example.com`). Dies ist für ein Failover gedacht: Wenn Edge Optimize einen Fehler aufweist, werden Anfragen an Ihre Domain weitergeleitet, die dann wieder in die Azure-Haustür eintritt und von Ihrem standardmäßigen Ursprung aus bereitgestellt wird.
* **Konsistenzprüfungen:** **Aktiviert**
   * Pfad: `/health/<your-domain>` (z. B. `/health/www.example.com`)
   * Protokoll: HTTPS
   * Intervall: 225 Sekunden
* **Sitzungsaffinität:** **Deaktiviert**
* **Validierung des Antragstellernamens des Zertifikats:** **Aktiviert**

![Edge optimiert die Ursprungsgruppe mit zwei prioritätsbasierten Ursprüngen und Konsistenzprüfungen](/help/assets/optimize-at-edge/azure-front-door-origin-group.png)

>[!NOTE]
>
>Die Gruppe &quot;`edge-optimize-origin-group` Herkunft“ zeigt im Portal eine **„Nicht**&quot; an. Dies wird erwartet - es wird durch eine Regelsatz-Routenüberschreibungen referenziert, nicht direkt durch eine Route.

## Schritt 2: Konfigurieren der Route

Normalerweise wird eine Standardroute mit Ihrem Azure-Haustürprofil erstellt. Der Regelsatz (Schritt 3) überschreibt die Ursprungsgruppe für den authentischen Traffic, sodass für Edge Optimize keine separate Route erforderlich ist.

## Schritt 3: Regelsatz erstellen

Gehen Sie **Regelsätze** > **Regelsatz hinzufügen** und benennen Sie ihn `EORouting`. Drei Regeln in dieser Reihenfolge hinzufügen.

![EORouting-Regelsatz, der die Regeln für Header-Stripping und Bot-Routing anzeigt](/help/assets/optimize-at-edge/azure-front-door-ruleset-routing.png)

### Regel 1: StripIncomingEOHeaders01

Entfernt eingehende Edge Optimize-Kopfzeilen, um Spoofing zu verhindern. Keine Bedingungen - gilt für alle Anfragen. Auswertung beenden: **Aus**.

**Aktionen** - Anfrage-Header für jede der folgenden Aktionen löschen:

* `x-edgeoptimize-url`
* `x-edgeoptimize-config`
* `x-edgeoptimize-api-key`
* `x-edgeoptimize-fetcher-key`

### Regel 2: EOGPTBotRootGET03

Leitet Bot-Anfragen auf HTML-Seitenpfaden an Edge Optimizer weiter. Auswertung stoppen: **Ein**.

**Bedingungen** (alle müssen übereinstimmen):

* Anfragemethode: **Gleich** `GET`
* Anfragepfad: **RegEx** `(^$|^.*/$|(^|.*/)[^./]+$|^.*\.html$)` (stimmt mit dem Website-Stamm, Pfaden, die in `/` enden, Pfaden ohne Erweiterung und `.html` Pfaden überein)
* Benutzeragent: **Enthält beliebige von** `chatgpt-user`, `gptbot`, `oai-searchbot`, `adobeedgeoptimize-ai`, `perplexitybot`, `perplexity-user`, `claudebot`, `claude-user`, `claude-searchbot`. Legen Sie die Zeichenfolgenumwandlung auf **in Kleinbuchstaben** fest.
* `x-edgeoptimize-monitor`: **Enthält nicht** `1`
* `x-edgeoptimize-request`: **enthält keine von** `failover`, `1`

**Aktionen**:

* Anfrage-Header überschreiben `x-edgeoptimize-url` = `/{url_path}?{query_string}`
* Anfrage-Header überschreiben `x-edgeoptimize-config` = `LLMCLIENT=TRUE;`
* Anfrage-Header überschreiben `x-edgeoptimize-api-key` = `YOUR_API_KEY`
* Anfrage-Header überschreiben `x-edgeoptimize-monitor` = `1`
* Überschreiben der Routenkonfiguration: Ursprungsgruppe → `edge-optimize-origin-group`, Weiterleitungsprotokoll → Übereinstimmung mit eingehender Anfrage, Zwischenspeicherung → **Deaktiviert**

### Regel 3: HealthProbeRewrite03

Schreibt Anfragen zur Konsistenzprüfung der Azure-Eingangstür neu, sodass sie als `/` anstatt als `/health/<domain>` zu Ihnen gelangen. Dadurch kann die Azure-Eingangstür die Verfügbarkeit von Edge Optimize überwachen, ohne dass ein dedizierter Konsistenzendpunkt in Ihrem Herkunftsland erforderlich ist. Auswertung stoppen: **Ein**.

![Neuschreibungsregel für Konsistenzprüfungen](/help/assets/optimize-at-edge/azure-front-door-ruleset-healthprobe.png)

**Bedingungen** (alle müssen übereinstimmen):

* Pfad der Anfrage-URL **(beginnt mit** `/health/`
* `x-fd-healthprobe`: **Enthält** `1`

**Aktionen**:

* URL-Umschreibung - Source-Muster: `/health/`, Ziel: `/`
* Antwort-Header überschreiben `custom-origin-health` = `routed` (Diagnose — kann nach der Überprüfung entfernt werden)
* Header anhängen `user-agent` = ` AdobeEdgeOptimize/1.0` (Leerzeichen am Anfang hinzufügen — Azure Front Door fügt den Wert unverändert hinzu)
* Überschreiben der Routenkonfiguration: Ursprungsgruppe → `default-origin-group`, Weiterleitungsprotokoll → Übereinstimmung mit eingehender Anfrage, Zwischenspeicherung → **Deaktiviert**

## Schritt 4: Regelsatz mit der Route verknüpfen

Öffnen Sie Ihre Route, scrollen Sie zum Abschnitt **Regeln** unten und wählen Sie den `EORouting` Regelsatz aus der Dropdown-Liste aus. Wenn Sie über vorhandene Regelsätze verfügen, verwenden Sie **Nach oben verschieben**, um `EORouting` bei **#1** zu positionieren. Die Regeln unter „Optimieren bei Edge&quot; fangen nur den agenten Traffic ab und Edge Optimize Loop-Back-Anfragen - jeder andere Traffic wird unbeeinflusst zu Ihren anderen Regeln durchgeleitet. Speichern und auf Weiterleitung warten (ca. 20 Minuten).

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

{{verify-routing-status-in-ui}}

{{return-to-overview}}
