---
title: Optimieren bei Edge - Fastly (BYOCDN)
description: Erfahren Sie, wie Sie Fastly BYOCDN für Optimize bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 5%

---


# Fastly (BYOCDN)

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Fastly-VCL-Regeln einrichten, stellen Sie sicher, dass Sie Folgendes haben:

* Zugriff auf Fastly für Ihre Domain.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

{{retrieve-byocdn-api-key}}

**Konfiguration**

Fügen Sie die folgenden drei VCL-Snippets zu Ihrem Fastly-Service hinzu. Diese Snippets behandeln Routing-Agent-Anfragen an Edge Optimizer, die Cache-Schlüsseltrennung und das Failover zu Ihrem standardmäßigen Ursprung.

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Hinzufügen von VCL-Snippets](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**VCL_RECV-Snippet**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
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
  set req.backend = F_Default_Origin;
  restart;
}

if (!req.http.x-edgeoptimize-config && req.http.x-edgeoptimize-request == "failover") {
  set resp.http.x-edgeoptimize-fo = "1";
}
```

**Failover**

Das `vcl_deliver`-Snippet verarbeitet Failover automatisch. Wenn Edge Optimize einen `4XX`- oder `5XX` zurückgibt, wird die Anfrage neu gestartet und an Ihren Standardursprung zurückgeleitet, sodass der Endbenutzer weiterhin eine Antwort erhält. Die Failover-Antworten enthalten die `x-edgeoptimize-fo: 1`.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` zurück | Der Client erhält eine optimierte Antwort. |
| Edge Optimize gibt `4XX` oder `5XX` zurück | Anfrage wird neu gestartet und von der Standardquelle bereitgestellt. |
| Failover-Antwort | Enthält die `x-edgeoptimize-fo: 1`. |

**Überprüfen Sie das Setup**

Stellen Sie nach Abschluss des Setups sicher, dass Bot-Traffic an Edge Optimize weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

**1. Bot-Traffic testen (sollte optimiert werden)**

Simulieren einer KI-Bot-Anfrage mithilfe eines agenten Benutzeragenten:

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

Die Antwort sollte **nicht** den `x-edgeoptimize-request-id`-Header enthalten. Seiteninhalt und Antwortzeit sollten vor der Aktivierung von Optimieren bei Edge identisch mit bleiben.

**3. Wie lassen sich die beiden Szenarien voneinander unterscheiden**

| Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Verkehr (nicht betroffen) |
|---|---|---|
| `x-edgeoptimize-request-id` | Präsenz - enthält eine eindeutige Anfrage-ID | Abwesend |
| `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover aufgetreten ist (Wert: `1`) | Abwesend |

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
