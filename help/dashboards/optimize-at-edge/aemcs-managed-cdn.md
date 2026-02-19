---
title: Optimieren bei Edge - AEM Cloud Service Managed CDN (Fastly)
description: Erfahren Sie, wie Sie das von AEM Cloud Service verwaltete CDN (Fastly) für „Optimize“ bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 12%

---


# AEM Cloud Service Managed CDN (Fastly)

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

So leiten Sie zunächst agenten Traffic an Edge weiter:

1. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

   ![Navigieren Sie zur Kundenkonfiguration](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Aktivieren **unter „KI-Traffic-Routing zur**&quot; das Kontrollkästchen **Optimierungen für KI-Agenten**. Das Adobe-Team übernimmt die Routing-Konfiguration in Ihrem Namen.

   ![Aktivieren Sie die Option Optimierungen für KI-Agenten bereitstellen](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Nach dem Aktivieren des Kontrollkästchens zeigt der Status an, dass die Einrichtung ausgeführt wird. Das Adobe-Team wird die Routing-Konfiguration für Sie abschließen.

   ![Einrichtung von KI-Traffic-Routing läuft](/help/assets/optimize-at-edge/prereq-traffic-routing-progress.png)

   Sobald das Routing konfiguriert und aktiv ist, wird der Status aktualisiert und ein grünes Häkchen angezeigt, das angibt, dass das Routing erfolgreich aktiviert wurde. Auf Ihrer Seite sind keine weiteren Maßnahmen erforderlich.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich außerdem an Ihr Adobe-Account-Team oder an Ihren `llmo-at-edge@adobe.com`.

**Self-Service-Routing über die Cloud Manager-Pipeline**

Wenn Sie das Routing lieber selbst über die Cloud Manager-Pipeline konfigurieren möchten, führen Sie die folgenden Schritte aus. Die Routing-Konfiguration erfolgt mithilfe einer [CDN-Regel „OriginSelector“](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). Folgende Voraussetzungen müssen erfüllt werden:

* Bestimmen Sie die Domain, die weitergeleitet werden soll.
* Legen Sie die zu verlegenden Pfade fest.
* Festlegen der zu rotierenden Benutzeragenten (empfohlener Regex)

Um die Regel bereitzustellen, müssen Sie Folgendes tun:

* Erstellen Sie eine [Konfigurations-Pipeline](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/config-pipeline).
* Übergeben Sie die `cdn.yaml` Konfigurationsdatei in Ihrem Repository.
* Ausführen der Konfigurations-Pipeline.

```
kind: "CDN"
version: "1"
data:
  # Origin selectors to route to Edge Optimize backend
  originSelectors:
    rules:
      - name: route-to-edge-optimize-backend
        when:
          allOf:
            - reqHeader: x-edgeoptimize-request
              exists: false # avoid loops when requests comes from Edge Optimize
            - reqHeader: user-agent
              matches: "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)" # routed user agents
            - reqProperty: domain
              equals: "example.com" # routed domain
            - reqProperty: originalPath
              matches: '(/[^./]+|\.html|/)$' # routed extensions, with .html extension or without extension
            - anyOf:
              - { reqProperty: originalPath, in: [ "/page.html" ] } # routed pages, exact path matching
              - { reqProperty: originalPath, like: "/dir/*" } # routed pages, wildcard path matching
        action:
          type: selectOrigin
          originName: edge-optimize-backend
    origins:
      - name: edge-optimize-backend
        domain: "live.edgeoptimize.net"
```

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

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

{{return-to-overview}}
