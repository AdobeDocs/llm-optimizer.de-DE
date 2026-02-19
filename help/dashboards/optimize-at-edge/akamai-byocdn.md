---
title: Optimieren bei Edge - Akamai (BYOCDN)
description: Erfahren Sie, wie Sie Akamai BYOCDN für „Optimieren“ bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 14%

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

Die Site-Failover-Konfiguration besteht aus zwei Teilen: dem Failover-Verhalten (konfiguriert innerhalb der Haupt-Routingregel „Optimize-at-Edge„) und einer separaten Header-Regel für den Failover-Test.

**9a. Site-Failover-Verhalten (innerhalb der Haupt-Routingregel „optimize-at-edge„)**

Konfigurieren Sie innerhalb der Haupt-Routing-Regel das Verhalten bei Site-Failover und das erweiterte XML-Snippet wie folgt:

![Site-Failover](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Fügen Sie die Anfrage-Header-`x-edgeoptimize-request` mit dem Wert hinzu, der über Erweiterte XML `fo` wird:

```
<forward:availability.fail-action2>
<add-header>
<status>on</status>
<name>x-edgeoptimize-request</name>
<value>fo</value>
</add-header>
</forward:availability.fail-action2>
```

![Failover-Verhalten](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

**9b. Failovertest-Header-Regel (gleichrangige Regel)**

>[!IMPORTANT]
>
>Erstellen Sie die **EdgeOptimize-Failover** Test-Header **Regel als gleichrangiges** (auf derselben Ebene) der Routing-Regeln - **nicht** in ihnen verschachtelt. In der Regelstruktur des Akamai Property Managers sollte die Hierarchie wie folgt aussehen:
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>Dadurch wird sichergestellt, dass die Header-Regel des Failovertests für **alle** Routingregeln und nicht nur für eine bewertet wird.

Wenn der `x-edgeoptimize-request` für die Anfrage `fo` ist, setzen Sie die `x-edgeoptimize-fo` für die ausgehende Antwort auf `true`.

![Failover-Regeln](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Site Failover stellt sicher, dass die Anfrage automatisch an Ihren Standardursprung zurückgeleitet wird, wenn Edge Optimize einen `4XX`- oder `5XX` zurückgibt, sodass der Endbenutzer weiterhin eine Antwort erhält.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` zurück | Der Client erhält eine optimierte Antwort. |
| Edge Optimize gibt `4XX` oder `5XX` zurück | Die Anfrage wird an den Standardursprung zurückgeleitet. |

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
