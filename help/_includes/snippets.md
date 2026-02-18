---
source-git-commit: beae935e7a34f5bccbe21578fa9a928912958710
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 2%

---
# Snippets

## Überprüfen des Setups - Adobe Managed CDN {#verify-setup-adobe-aem-cs-cdn}

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

## Überprüfen des Setups - BYOCDN {#verify-setup-byocdn}

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

## Schritte zum Abrufen von API-Schlüsseln {#retrieve-byocdn-api-key}

**Schritte zum Abrufen Ihres API-Schlüssels:**

1. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

   ![Navigieren Sie zur Kundenkonfiguration](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Aktivieren **unter „KI-Traffic-Routing zur**&quot; das Kontrollkästchen **Optimierungen für KI-Agenten**.

   ![Aktivieren Sie die Option Optimierungen für KI-Agenten bereitstellen](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Kopieren Sie den API-Schlüssel und fahren Sie mit den folgenden Schritten zur Routing-Konfiguration fort.

   ![Kopieren Sie den API-Schlüssel](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >In dieser Phase zeigt der Status möglicherweise ein rotes Kreuz an, das anzeigt, dass die Einrichtung noch nicht abgeschlossen ist. Dies wird erwartet - Sobald Sie die unten stehende Routing-Konfiguration abgeschlossen haben und der Traffic des KI-Bots fließt, wird der Status in ein grünes Häkchen geändert, wodurch bestätigt wird, dass das Routing erfolgreich aktiviert wurde.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich außerdem an Ihr Adobe-Account-Team oder an Ihren `llmo-at-edge@adobe.com`.

## Zurück zur Übersicht {#return-to-overview}

Weitere Informationen zu „Optimieren bei Edge&quot;, einschließlich verfügbarer Opportunitys, Workflows für die automatische Optimierung und häufig gestellte Fragen, finden Sie unter &quot;[ bei Edge - Überblick](/help/dashboards/optimize-at-edge.md).
