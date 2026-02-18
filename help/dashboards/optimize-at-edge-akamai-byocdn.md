---
title: Optimieren bei Edge - Akamai (BYOCDN)
description: Erfahren Sie, wie Sie Akamai BYOCDN für „Optimieren“ bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 26%

---


# Akamai (BYOCDN)

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Regeln für den Akamai Property Manager einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Zugriff auf den Akamai Property Manager für Ihre Domain.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

{{retrieve-byocdn-api-key}}

**Konfiguration**

Die folgende Akamai-Property-Manager-Regel leitet LLM-Benutzeragenten an Edge Optimizer weiter. Die Konfiguration umfasst die folgenden Schritte:

**1. Festlegen von Routing-Kriterien (Zuordnung von Benutzer-Agents)**

Legen Sie Routing für die folgenden user-agents.:image fest

```
 *AdobeEdgeOptimize-AI*,
 *ChatGPT-User*,
 *GPTBot*,
 *OAI-SearchBot*,
 *PerplexityBot*,
 *Perplexity-User*
```

![Festlegen von Routing-Kriterien](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Festlegen der Herkunft und des SSL-Verhaltens**

Herkunft als `live.edgeoptimize.net` festlegen und SAN an `*.edgeoptimize.net` anpassen

![Festlegen der Herkunft und des SSL-Verhaltens](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Festlegen der Cache-Schlüsselvariablen**

Legen Sie die Cache-Schlüsselvariable `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` auf `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}` fest.

![Festlegen der Cache-Schlüsselvariablen](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Caching-Regeln**

![Caching-Regeln](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Ändern der eingehenden Anfrage-Header**

Legen Sie die folgenden Header für eingehende Anfragen fest:
`x-edgeoptimize-api-key` zum von LLMO abgerufenen API-Schlüssel
`x-edgeoptimize-config` zu `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` zu `{{builtin.AK_URL}}`

![Ändern der eingehenden Anfrage-Header](/help/assets/optimize-at-edge/akamai-step5-request.png)

**6. Ändern der eingehenden Antwort-Header**

![Ändern der eingehenden Antwort-Header](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Cache-ID-Änderung**

![Cache-ID-Änderung](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Ausgehende Anfragekopfzeilen ändern**

`x-forwarded-host`-Header auf `{{builtin.AK_HOST}}` setzen

![Ausgehende Anfragekopfzeilen ändern](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Site-Failover**

![Site-Failover](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Failover-Verhalten](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

![Failover-Regeln](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Site Failover stellt sicher, dass die Anfrage automatisch an Ihren Standardursprung zurückgeleitet wird, wenn Edge Optimize einen `4XX`- oder `5XX` zurückgibt, sodass der Endbenutzer weiterhin eine Antwort erhält.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` zurück | Der Client erhält eine optimierte Antwort. |
| Edge Optimize gibt `4XX` oder `5XX` zurück | Die Anfrage wird an den Standardursprung zurückgeleitet. |

{{verify-setup-byocdn}}

{{return-to-overview}}
