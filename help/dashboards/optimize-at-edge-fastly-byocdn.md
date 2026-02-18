---
title: Optimieren bei Edge - Fastly (BYOCDN)
description: Erfahren Sie, wie Sie Fastly BYOCDN für Optimize bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 8cdd15413555057165f69ea4d5a15b243ab9098d
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

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

{{verify-setup-byocdn}}

{{return-to-overview}}
