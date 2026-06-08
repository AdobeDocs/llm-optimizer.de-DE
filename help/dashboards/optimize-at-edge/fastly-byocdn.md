---
title: Optimize at Edge – Fastly (BYOCDN)
description: Erfahren Sie, wie Sie Fastly BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-05-15T17:51:24.924Z'
TQID: 'https://experienceleague.adobe.com/qXp1pbmZrxahHFOUzIuo-WEawdgNWIIQKDyy0yL2MLA'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: c5a8f033aac85913b56a40bb1560537da04847f2
workflow-type: tm+mt
source-wordcount: 350
ht-degree: 96%

---


# Fastly (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Bevor Sie die Fastly-VCL-Regeln einrichten, stellen Sie sicher, dass Sie Folgendes haben:

* Zugriff auf Fastly für Ihre Domain.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Konfiguration**

Fügen Sie die folgenden drei VCL-Snippets zu Ihrem Fastly-Service hinzu. Diese Snippets verarbeiten Agent-basierte Routing-Anfragen an Edge Optimizer, die Cache-Schlüsseltrennung und das Failover zu Ihrem standardmäßigen Ursprung.

![Fastly Backend-Konfiguration](/help/assets/optimize-at-edge/fastly-backend-config.png)

![Hinzufügen von VCL-Snippets](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**VCL_RECV-Snippet**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;
unset req.http.x-edgeoptimize-fetcher-key; # Optional (required only in case of WAF)

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User|ClaudeBot|Claude-User|Claude-SearchBot)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.http.x-edgeoptimize-fetcher-key = "<YOUR FETCHER KEY>"; # Optional (required only in case of WAF)
  set req.backend = F_EDGE_OPTIMIZE;
  return(lookup);
}
```

**VCL_HASH-Snippet**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**VCL_DELIVER-Snippet**

```
if (req.http.x-edgeoptimize-config && resp.status >= 400) {
  set req.http.x-edgeoptimize-request = "failover";
  restart;
}

if (req.http.x-edgeoptimize-config) {
  return(deliver);
}

if (!req.http.x-edgeoptimize-config && req.http.x-edgeoptimize-request == "failover") {
  set resp.http.x-edgeoptimize-fo = "1";
}
```

**Failover**

Das Snippet `vcl_deliver` wickelt ein Failover automatisch ab. Wenn Edge Optimize einen `4XX`- oder `5XX`-Fehler zurückgibt, wird die Anfrage neu gestartet und an Ihren Standardursprung zurückgeleitet, sodass der bzw. die Endbenutzende weiterhin eine Antwort erhält. Die Failover-Antworten enthalten den `x-edgeoptimize-fo: 1`-Header.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` zurück | Der Client erhält eine optimierte Antwort. |
| Edge Optimize gibt `4XX` oder `5XX` zurück | Anfrage wird neu gestartet und vom Standardursprung bereitgestellt. |
| Failover-Antwort | Enthält den `x-edgeoptimize-fo: 1`-Header. |

**Zulassen von „Optimize at Edge“ durch Firewall-Regeln (optional)**

{{waf-allowlist-setup}}

**Überprüfen des Setups**

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
