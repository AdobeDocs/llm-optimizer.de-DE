---
title: Optimize at Edge
description: Erfahren Sie, wie Sie in LLM Optimizer Optimierungen am CDN-Edge bereitstellen können, ohne dass Authoring-Änderungen erforderlich sind.
feature: Opportunities
source-git-commit: 1f665bd14349c15d92f8274742606abcf9b02000
workflow-type: tm+mt
source-wordcount: '4708'
ht-degree: 44%

---


# Optimize at Edge

Diese Seite bietet einen detaillierten Überblick darüber, wie Optimierungen am CDN-Edge ohne Authoring-Änderungen bereitgestellt werden können. Sie behandelt den Onboarding-Prozess, die verfügbaren Optimierungsmöglichkeiten und die automatische Optimierung am Edge.

>[!NOTE]
>Diese Funktion befindet sich derzeit im Early Access. Weitere Informationen zu Early-Access-Programmen finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Was ist „Optimize at Edge“?

„Optimize at Edge“ ist eine Edge-basierte Bereitstellungsfunktion in LLM Optimizer, die KI-freundliche Änderungen für LLM-Benutzer-Agents bereitstellt. Im aktuellen Kontext bedeutet „Edge“, dass die Optimierung auf der CDN-Ebene angewendet wird. Da die Optimierungen auf CDN-Ebene bereitgestellt werden, sind keine Authoring-Änderungen im Content-Management-System (CMS) erforderlich, sodass Ihr Ursprungs-CMS unverändert bleibt. Durch diese Trennung können Sie die LLM-Sichtbarkeit verbessern, ohne Ihre vorhandenen Veröffentlichungs-Workflows zu verändern. Ziel ist ausschließlich Agent-basierter Traffic, sodass menschliche Benutzende oder SEO-Bots nicht beeinflusst werden. Wenn LLM Optimizer Möglichkeiten zur Seitenoptimierung erkennt, können Benutzende Fehlerbehebungen direkt am CDN-Edge bereitstellen.

„Optimize at Edge“ ist eine schnellere, schlankere Alternative zu herkömmlichen Fehlerbehebungen, die komplexen technischen Aufwand erfordern. Wie bereits erwähnt, sind nach Abschluss einer einmaligen Einrichtung keine Plattformänderungen oder langen Entwicklungszyklen erforderlich, um die Änderungen anzuwenden. Sie können Verbesserungen in Minuten veröffentlichen, ohne dass Entwicklerinteraktionen erforderlich sind. Dies ist eine Methode ohne Programmierungsaufwand, mit der Sie Ihre Website für AI Agents optimieren können.

„Optimize at Edge“ wurde für Unternehmenskundschaft in den Bereichen Marketing, SEO, Content und digitale Strategien entwickelt. Unternehmenskundschaft erhält dadurch die Möglichkeit, die vollständige Journey in LLM Optimizer abzuschließen: Ermitteln von Möglichkeiten, Analysieren von Vorschlägen und einfaches Bereitstellen der Fehlerbehebungen. Mit „Optimize at Edge“ können Benutzende eine Vorschau der Änderungen anzeigen, diese schnell am CDN-Edge bereitstellen und überprüfen, ob die Optimierungen live sind. Die Leistung kann im LLM Optimizer-Ökosystem nachverfolgt werden.

### Wichtigste Vorteile

* **Bereitstellung nur für KI:** Optimiertes HTML wird ausschließlich für AI Agents ohne Auswirkungen auf menschliche Besuchende oder SEO-Bots bereitgestellt.
* **Schnellere Zyklen:** Veröffentlichen Sie Änderungen in Minuten statt Wochen. Plattformänderungen oder lange Entwicklungszyklen sind nicht erforderlich.
* **Umkehrbar:** Mit der Funktion für einen Rollback mit einem Klick können Sie die Seite innerhalb weniger Minuten zurücksetzen.
* **Keine Leistungsbeeinträchtigung:** Edge-basierte Optimierungen und Caching wirken sich nicht auf die Site-Latenz aus.
* **CDN- und CMS-unabhängig:** Funktioniert unabhängig vom Content-Management-System mit jeder CDN-Konfiguration und jedem Frontend-Setup.

### Welche Möglichkeiten werden durch „Optimize at Edge“ unterstützt?

„Optimize at Edge“ unterstützt Möglichkeiten zur Verbesserung des Agent-basierten Web-Erlebnisses. Weitere Informationen zu den einzelnen Möglichkeiten finden Sie sowohl auf der Seite [Dashboard „Möglichkeiten“](/help/dashboards/opportunities.md) als auch im Abschnitt „Möglichkeiten“ auf dieser Seite.

## Onboarding

Wenden Sie sich entweder an Ihr Adobe-Accountteam oder an das FDE-Team, um das Onboarding-Verfahren zu starten. Ihr IT- oder CDN-Team muss außerdem die Voraussetzungen erfüllen und das Einrichtungsverfahren abschließen. Darüber hinaus können Sie sich auch an `llmo-at-edge@adobe.com` wenden, um weitere Unterstützung beim Onboarding zu erhalten.

Voraussetzungen für das Onboarding von „Optimize at Edge“:

* Schließen Sie das Onboarding-Verfahren für LLM Optimizer ab.
* Schließen Sie das Protokollweiterleitungsverfahren für Ihre CDN-Protokolle ab.

Voraussetzungen für Ihr IT-/CDN-Team:
* Auf die Zulassungsliste setzen Fügen Sie `*AdobeEdgeOptimize/1.0*` user-agent zur Datei „robots.txt“ Ihrer Site hinzu oder verwalten Sie Bot-Traffic-Regeln.
* Stellen Sie sicher, dass Seiten nicht auf Domain- oder CDN-Ebene blockiert werden.
* Fügen Sie Routing-Regeln für „Optimize at Edge“ im CDN hinzu.
* Prüfen Sie das Routing für „Optimize at Edge“ in der Benutzeroberfläche von LLM Optimizer.

Im Folgenden finden Sie einige Beispielkonfigurationen für eine Reihe von CDN-Einrichtungen, die Ihnen als Anleitung für das Einrichtungsverfahren dienen sollen. Beachten Sie, dass diese Beispiele an Ihre tatsächliche Live-Konfiguration angepasst werden müssen. Wir empfehlen, Änderungen zuerst in den niedrigeren Umgebungen anzuwenden.

>[!BEGINTABS]

>[!TAB AEM Cloud Service Managed CDN (Fastly)]

**Edge Optimize - AEM Cloud Service Managed CDN (Fastly)**

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

Führen Sie zum Testen des Setups eine cURL aus. Folgendes wird erwartet:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

>[!TAB Fastly (BYOCDN)]

**Edge Optimize - Fastly (BYOCDN)**

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Fastly-VCL-Regeln einrichten, stellen Sie sicher, dass Sie Folgendes haben:

* Zugriff auf Fastly für Ihre Domain.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

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

Führen Sie zum Testen des Setups eine cURL aus. Folgendes wird erwartet:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Akamai (BYOCDN)]

**Edge Optimize - Akamai (BYOCDN)**

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Regeln für den Akamai Property Manager einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Zugriff auf den Akamai Property Manager für Ihre Domain.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

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

**Konfiguration**

Die folgende Akamai-Property-Manager-Regel leitet LLM-Benutzeragenten an Edge Optimizer weiter. Die Konfiguration umfasst die folgenden Schritte:

**1. Festlegen von Routing-Kriterien (Zuordnung von Benutzer-Agents)**

Legen Sie das Routing für die folgenden user-agents fest:

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

**Überprüfen Sie das Setup**

Führen Sie zum Testen des Setups eine cURL aus. Folgendes wird erwartet:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Cloudflare (BYOCDN)]

**Edge Optimize - Cloudflare (BYOCDN)**

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Routing-Regeln für Cloudflare-Worker einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Ein Cloudflare-Konto mit aktivierten Workers in Ihrer Domain.
* Zugriff auf die DNS-Einstellungen Ihrer Domain in Cloudflare.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

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

**Funktionsweise des Routings**

Bei korrekter Konfiguration wird eine Anfrage an Ihre Domain (z. B. `www.example.com/page.html`) von einem Agent-Benutzeragenten vom Cloudflare-Worker abgefangen und an das Edge Optimizer-Backend weitergeleitet. Die Backend-Anfrage enthält die erforderlichen Kopfzeilen.

**Testen der Backend-Anfrage**

Sie können das Routing überprüfen, indem Sie eine direkte Anfrage an das Backend von Edge Optimize stellen.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**Erforderliche Kopfzeilen**

Bei Anfragen an das Backend von Edge Optimize müssen die folgenden Kopfzeilen festgelegt werden:

| Kopfzeile | Beschreibung | Beispiel |
|--------|-------------|---------|
| `x-forwarded-host` | Der ursprüngliche Host der Anfrage. Erforderlich zum Identifizieren der Website-Domain. | `www.example.com` |
| `x-edgeoptimize-url` | Der ursprüngliche URL-Pfad und die Abfragezeichenfolge der Anfrage. | `/page.html` oder `/products?id=123` |
| `x-edgeoptimize-api-key` | Der von Adobe für Ihre Domain bereitgestellte API-Schlüssel. | `your-api-key-here` |
| `x-edgeoptimize-config` | Konfigurations-String zur Cache-Schlüsseldifferenzierung. | `LLMCLIENT=TRUE;` |

**Schritt 1: Erstellen des Cloudflare-Sekundärs**

1. Melden Sie sich bei Ihrem Cloudflare-Dashboard an.
2. Navigieren Sie in **Seitenleiste zu** Arbeiter und Seiten“.
3. Klicken Sie **Anwendung erstellen** und dann **Worker erstellen**.
4. Benennen Sie Ihren Worker (z. B. `edge-optimize-router`).
5. Klicken Sie **Bereitstellen**, um den Worker mit dem Standard-Code zu erstellen.

![Cloudflare-Workers-Dashboard](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Schritt 2: Fügen Sie den Worker-Code hinzu**

Klicken Sie nach dem Erstellen des Workers auf **Code bearbeiten** und ersetzen Sie den Standard-Code durch Folgendes:

```javascript
/**
 * Edge Optimize BYOCDN - Cloudflare Worker
 *
 * This worker routes requests from agentic bots (AI/LLM user agents) to the
 * Edge Optimize backend service for optimized content delivery.
 *
 * Features:
 * - Routes agentic bot traffic to Edge Optimize backend
 * - Failover to origin on Edge Optimize errors (any 4XX or 5XX errors)
 * - Loop protection to prevent infinite redirects
 * - Human visitors and SEO bots are served from the origin as usual
 */

// List of agentic bot user agents to route to Edge Optimize
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User'
];

// Targeted paths for Edge Optimize routing
// Set to null to route all HTML pages, or specify an array of paths
const TARGETED_PATHS = null; // e.g., ['/', '/page.html', '/products']

// Failover configuration
// Failover on any 4XX client error or 5XX server error from Edge Optimize
const FAILOVER_ON_4XX = true; // Failover on any 4XX error (400-499)
const FAILOVER_ON_5XX = true; // Failover on any 5XX error (500-599)

export default {
  async fetch(request, env, ctx) {
    return await handleRequest(request, env, ctx);
  },
};

async function handleRequest(request, env, ctx) {
  const url = new URL(request.url);
  const userAgent = request.headers.get("user-agent")?.toLowerCase() || "";

  // Check if request is already processed (loop protection)
  const isEdgeOptimizeRequest = !!request.headers.get("x-edgeoptimize-request");

  // Construct the original path and query string
  const pathAndQuery = `${url.pathname}${url.search}`;

  // Check if the path matches HTML pages (no extension or .html extension)
  const isHtmlPage = /(?:\/[^./]+|\.html|\/)$/.test(url.pathname);

  // Check if path is in targeted paths (if specified)
  const isTargetedPath = TARGETED_PATHS === null
    ? isHtmlPage
    : (isHtmlPage && TARGETED_PATHS.includes(url.pathname));

  // Check if user agent is an agentic bot
  const isAgenticBot = AGENTIC_BOTS.some((ua) => userAgent.includes(ua.toLowerCase()));

  // Route to Edge Optimize if:
  // 1. Request is NOT already from Edge Optimize (prevents infinite loops)
  // 2. User agent matches one of the agentic bots
  // 3. Path is targeted for optimization
  if (!isEdgeOptimizeRequest && isAgenticBot && isTargetedPath) {

    // Build the Edge Optimize request URL
    const edgeOptimizeURL = `https://live.edgeoptimize.net${pathAndQuery}`;

    // Clone and modify headers for the Edge Optimize request
    const edgeOptimizeHeaders = new Headers(request.headers);

    // Remove any existing Edge Optimize headers for security
    edgeOptimizeHeaders.delete("x-edgeoptimize-api-key");
    edgeOptimizeHeaders.delete("x-edgeoptimize-url");
    edgeOptimizeHeaders.delete("x-edgeoptimize-config");

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

    try {
      // Send request to Edge Optimize backend
      const edgeOptimizeResponse = await fetch(new Request(edgeOptimizeURL, {
        headers: edgeOptimizeHeaders,
        redirect: "manual", // Preserve redirect responses from Edge Optimize
      }), {
        cf: {
          cacheEverything: true, // Enable caching based on origin's cache-control headers
        },
      });

      // Check if we need to failover to origin
      const status = edgeOptimizeResponse.status;
      const is4xxError = FAILOVER_ON_4XX && status >= 400 && status < 500;
      const is5xxError = FAILOVER_ON_5XX && status >= 500 && status < 600;

      if (is4xxError || is5xxError) {
        console.log(`Edge Optimize returned ${status}, failing over to origin`);
        return await failoverToOrigin(request, env, url);
      }

      // Return the Edge Optimize response
      return edgeOptimizeResponse;

    } catch (error) {
      // Network error or timeout - failover to origin
      console.log(`Edge Optimize request failed: ${error.message}, failing over to origin`);
      return await failoverToOrigin(request, env, url);
    }
  }

  // For all other requests (human users, SEO bots), pass through unchanged
  return fetch(request);
}

/**
 * Failover to origin server when Edge Optimize returns an error
 * @param {Request} request - The original request
 * @param {Object} env - Environment variables
 * @param {URL} url - Parsed URL object
 */
async function failoverToOrigin(request, env, url) {
  // Build origin URL
  const originURL = `${url.protocol}//${env.EDGE_OPTIMIZE_TARGET_HOST}${url.pathname}${url.search}`;

  // Prepare headers - clean Edge Optimize headers and add loop protection
  const originHeaders = new Headers(request.headers);
  originHeaders.set("Host", env.EDGE_OPTIMIZE_TARGET_HOST);
  originHeaders.delete("x-edgeoptimize-api-key");
  originHeaders.delete("x-edgeoptimize-url");
  originHeaders.delete("x-edgeoptimize-config");
  originHeaders.delete("x-forwarded-host");
  originHeaders.set("x-edgeoptimize-request", "fo");

  // Create and send origin request
  const originRequest = new Request(originURL, {
    method: request.method,
    headers: originHeaders,
    body: request.body,
    redirect: "manual",
  });

  const originResponse = await fetch(originRequest);

  // Add failover marker header to response
  const modifiedResponse = new Response(originResponse.body, {
    status: originResponse.status,
    statusText: originResponse.statusText,
    headers: originResponse.headers,
  });
  modifiedResponse.headers.set("x-edgeoptimize-fo", "1");
  return modifiedResponse;
}
```

Klicken Sie **Speichern und Bereitstellen**, um den Worker zu veröffentlichen.

![Cloudflare-Worker-Code-Editor](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Schritt 3: Konfigurieren von Umgebungsvariablen**

Umgebungsvariablen speichern vertrauliche Konfigurationen wie Ihren API-Schlüssel sicher.

1. Navigieren Sie in den Einstellungen Ihres Sekundärs zu **Einstellungen** > **Variablen**.
2. Klicken **unter &quot;**&quot; auf **Variable hinzufügen**.
3. Fügen Sie die folgenden Variablen hinzu:

   | Variablenname | Beschreibung | Erforderlich |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Ihr von Adobe bereitgestellter API-Schlüssel für Edge Optimize. | Ja |
   | `EDGE_OPTIMIZE_TARGET_HOST` | Der Ziel-Host für Edge Optimize-Anfragen (als `x-forwarded-host`-Header gesendet) und die Ursprungs-Domain für das Failover. Darf nur die Domain ohne Protokoll sein (z. B. `www.example.com`, nicht `https://www.example.com`). | Ja |

4. Klicken Sie für den API-Schlüssel auf **Verschlüsseln**, um ihn sicher zu speichern.
5. Klicken Sie **Speichern und bereitstellen**.

![Cloudflare-Umgebungsvariablen](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

**Schritt 4: Hinzufügen einer Route zu Ihrer Domain**

So aktivieren Sie den Worker in Ihrer Domain:

1. Navigieren Sie zu den **Einstellungen** > **Trigger**.
2. Klicken **unter „Routen** auf **Route hinzufügen**.
3. Geben Sie Ihr Domain-Muster ein (z. B. `www.example.com/*` oder `example.com/*`).
4. Wählen Sie Ihre Zone im Dropdown-Menü aus.
5. Klicken Sie auf **Speichern**.

Alternativ können Sie Routen auf Zonenebene konfigurieren:

1. Navigieren Sie zu Ihrer Domain in Cloudflare.
2. Gehen Sie zu **Arbeiter-Routen**.
3. Klicken Sie **Route hinzufügen** und geben Sie das Muster und den Worker an.

![Cloudflare-Arbeitsrouten](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Schritt 5: Überprüfen Sie die Einrichtung**

Testen Sie die Konfiguration nach der Bereitstellung, indem Sie eine -Anfrage mit einem Agent-Benutzeragenten stellen.

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Eine erfolgreiche Antwort enthält die `x-edgeoptimize-request-id`:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

Sie können auch überprüfen, ob der normale Traffic weiterhin funktioniert:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0"
```

Diese Anfrage sollte aus Ihrer Quelle ohne den `x-edgeoptimize-request-id`-Header bedient werden.

**Überprüfen des Failover-Verhaltens**

Wenn Edge Optimize nicht verfügbar ist oder einen Fehler zurückgibt, führt der Worker automatisch ein Failover zu Ihrer Herkunft durch. Die Failover-Antworten enthalten die `x-edgeoptimize-fo`:

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Sie können Failover-Ereignisse in den Cloudflare Workers-Protokollen überwachen, um Probleme zu beheben.

**Verstehen der Worker-Logik**

Der Cloudflare-Worker implementiert die folgende Logik:

1. **Erkennung von Benutzeragenten:** Prüft, ob der Benutzeragent der eingehenden Anfrage mit einem der definierten Agentbots übereinstimmt (ignoriert Groß-/Kleinschreibung).

2. **Pfad-Targeting** Filtert Anfragen optional nach Zielpfaden. Standardmäßig werden alle HTML-Seiten (URLs, die mit `/`, keiner Erweiterung oder `.html` enden) weitergeleitet. Sie können bestimmte Pfade mithilfe des `TARGETED_PATHS`-Arrays angeben.

3. **Schleifenschutz:** Der `x-edgeoptimize-request`-Header verhindert unendliche Schleifen. Wenn Edge Optimize Anfragen an Ihren Ursprung zurücksendet, wird diese Kopfzeile auf `"1"` festgelegt, und der Worker übergibt die Anfrage an , ohne sie zurück an Edge Optimize zu leiten.

4. **Header-Sicherheit:** Bevor Sie Edge Optimize-Header festlegen, entfernt der Worker alle vorhandenen `x-edgeoptimize-*`-Header aus der eingehenden Anfrage, um Header-Injection-Angriffe zu verhindern.

5. **Header-Zuordnung:** Der Worker legt die erforderlichen Header für Edge Optimize fest:
   * `x-forwarded-host` - Identifiziert die ursprüngliche Site-Domain.
   * `x-edgeoptimize-url` - Behält den ursprünglichen Anfragepfad und die Abfragezeichenfolge bei.
   * `x-edgeoptimize-api-key` - Authentifiziert die Anfrage mit Edge Optimize.
   * `x-edgeoptimize-config` - Stellt die Konfiguration des Cache-Schlüssels bereit.

6. **Failover-Logik:** Wenn Edge Optimize einen Fehlerstatus-Code (4XX-Client- oder 5XX-Server-Fehler) zurückgibt oder die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt, schlägt der Worker mithilfe von `EDGE_OPTIMIZE_TARGET_HOST` automatisch auf Ihren Ursprung fehl. Die Failover-Antwort enthält den `x-edgeoptimize-fo: 1`-Header, um anzugeben, dass ein Failover aufgetreten ist.

7. **Umleitungshandhabung:** Die Option &quot;`redirect: "manual"`&quot; stellt sicher, dass Umleitungsantworten von Edge Optimize an den Client weitergeleitet werden, ohne dass der Worker ihnen folgt.

**Anpassen der Konfiguration**

Sie können das Workerverhalten anpassen, indem Sie die Konfigurationskonstanten oben im Code ändern:

**Agent-Bot-Liste**

Ändern Sie das `AGENTIC_BOTS`-Array, um Benutzeragenten hinzuzufügen oder zu entfernen:

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  // Add additional user agents as needed
  'ClaudeBot',
  'Anthropic-AI'
];
```

**Zielpfade**

Standardmäßig werden alle HTML-Seiten an Edge Optimizer weitergeleitet. Um das Routing auf bestimmte Pfade zu beschränken, ändern Sie das `TARGETED_PATHS`-Array:

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Failover-Konfiguration**

Standardmäßig schlägt der Worker bei einem 4XX- oder 5XX-Fehler von Edge Optimize fehl. Dieses Verhalten anpassen:

```javascript
// Default: failover on any 4XX or 5XX error
const FAILOVER_ON_4XX = true;
const FAILOVER_ON_5XX = true;

// Failover only on 5XX server errors (not 4XX client errors)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = true;

// Disable automatic failover (not recommended)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = false;
```

**Wichtige Aspekte**

* **Failover-Verhalten:** Der Worker führt automatisch ein Failover zu Ihrem Ursprung durch, wenn Edge Optimize einen Fehler zurückgibt (Status-Codes 4XX oder 5XX) oder wenn die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt. Bei Failover wird `EDGE_OPTIMIZE_TARGET_HOST` als Ursprungs-Domain verwendet (ähnlich wie bei Fastly `F_Default_Origin` oder CloudFront `Default_Origin`). Failoverantworten enthalten den `x-edgeoptimize-fo: 1`-Header, den Sie zum Überwachen und Debuggen verwenden können.

* **Caching:** Cloudflare speichert Antworten standardmäßig basierend auf der URL zwischen. Da der Agent-Traffic andere Inhalte erhält als menschlicher Traffic, stellen Sie sicher, dass dies in der Cache-Konfiguration berücksichtigt wird. Erwägen Sie die Verwendung der Cache-API oder Cache-Kopfzeilen, um zwischengespeicherte Inhalte zu unterscheiden. Die `x-edgeoptimize-config`-Kopfzeile sollte in Ihrem Cache-Schlüssel enthalten sein.

* **Ratenbegrenzung:** Überwachen Sie die Nutzung von Edge Optimize und erwägen Sie bei Bedarf die Implementierung einer Ratenbegrenzung für den agenten Traffic.

* **Testen** Testen Sie die Konfiguration immer in einer Staging-Umgebung, bevor Sie sie in der Produktion bereitstellen. Stellen Sie sicher, dass sich der Traffic von Agenten und Menschen erwartungsgemäß verhält. Testen Sie das Failover-Verhalten durch Simulation von Edge Optimize-Fehlern.

* **Protokollierung:** Sie die Protokollierung von Cloudflare-Sekundären, um Anfragen zu überwachen und Probleme zu beheben. Navigieren Sie **Worker** > **Ihr Worker** > **Protokolle**, um Echtzeit-Protokolle anzuzeigen. Der Worker protokolliert Failover-Ereignisse zu Debugging-Zwecken.

**Fehlerbehebung**

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| Keine `x-edgeoptimize-request-id`-Kopfzeile in Antwort | Arbeitsroute nicht zugeordnet oder Benutzeragent nicht in der Agentenbots-Liste. | Stellen Sie sicher, dass Ihr Routenmuster mit der Anfrage-URL übereinstimmt. Prüfen Sie, ob sich der Benutzeragent im `AGENTIC_BOTS`-Array befindet. |
| 401- oder 403-Fehler von Edge Optimize | Ungültiger oder fehlender API-Schlüssel. | Stellen Sie sicher, dass `EDGE_OPTIMIZE_API_KEY` in Umgebungsvariablen korrekt festgelegt ist. Adobe kontaktieren, um zu bestätigen, dass Ihr API-Schlüssel aktiv ist. |
| Unendliche Weiterleitungen oder Schleifen | Schleifenschutz-Kopfzeile wird nicht richtig eingestellt oder überprüft. | Stellen Sie sicher, dass die `x-edgeoptimize-request` Kopfzeilenprüfung vorhanden ist. |
| Betroffener Menschenhandel | Routing-Logik für Worker ist zu breit angelegt. | Stellen Sie sicher, dass die Zuordnungslogik des Benutzeragenten korrekt ist und nicht zwischen Groß- und Kleinschreibung unterschieden wird. Überprüfen Sie, ob `TARGETED_PATHS` richtig konfiguriert ist. |
| Langsame Reaktionszeiten | Netzwerklatenz zum Edge Optimize-Backend. | Dies ist für die erste Anfrage zu erwarten. Nachfolgende Anfragen werden bei Edge Optimize zwischengespeichert. |
| `x-edgeoptimize-fo: 1` in Antwort | Edge Optimize hat einen Fehler zurückgegeben, und es ist ein Failover zum Ursprung aufgetreten. | Überprüfen Sie die Cloudflare Workers-Protokolle auf den spezifischen Fehler-Code. Überprüfen Sie den Service-Status von Edge Optimize mit Adobe. |
| Failover funktioniert nicht | Failover-Flags deaktiviert oder Fehler in der Failover-Logik. | Überprüfen Sie, ob `FAILOVER_ON_4XX` und `FAILOVER_ON_5XX` auf `true` eingestellt sind. Überprüfen Sie die Worker-Protokolle auf Fehlermeldungen. |
| Bestimmte Pfade werden nicht optimiert | Pfad stimmt nicht mit den Zielpfaden oder dem HTML-Seitenmuster überein. | Stellen Sie sicher, dass der Pfad in `TARGETED_PATHS` ist (falls angegeben) und mit dem HTML-Seiten-Regex-Muster übereinstimmt. |
| Fehlgeschlagene Anfragen mit ungültigem Host | `EDGE_OPTIMIZE_TARGET_HOST` umfasst das -Protokoll (z. B. `https://`). | Nur den Domain-Namen ohne Protokoll verwenden (z. B. `example.com`, nicht `https://example.com`). |
| 530-Fehler beim Failover | Cloudflare kann keine Verbindung zur Quelle herstellen, oder die Failover-Anfrage hat ungültige Kopfzeilen. | Stellen Sie sicher, dass die Failover-Funktion Edge Optimize-Kopfzeilen entfernt. Stellen Sie sicher, dass auf Ihre Herkunft zugegriffen werden kann und dass das DNS korrekt konfiguriert ist. |

>[!ENDTABS]

>[!NOTE]
>Wenden Sie sich für andere CDN-Anbieter an `llmo-at-edge@adobe.com`, um Unterstützung für Ihre IT-/CDN-Teams beim Onboarding zu erhalten. Sobald die Einrichtungskonfigurationen abgeschlossen sind, können Sie Empfehlungen für Möglichkeiten von „Optimize at Edge“ in LLM Optimizer bereitstellen.

## Möglichkeiten

In der folgenden Tabelle sind Möglichkeiten aufgeführt, die das Agent-basierte Web-Erlebnis verbessern können und durch „Optimize at Edge“ unterstützt werden.

| Möglichkeit | Typ | Automatische Identifikation | Automatische Vorschläge | Automatische Optimierung |
|---------|----------|----------|----------|----------|
| Inhaltssichtbarkeit wiederherstellen | Technische GEO | Erkennt Seiten, auf denen kritische Inhalte vor AI Agents verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die sichtbar gemacht werden können. | Hebt Inhalte hervor, die für AI Agents verfügbar gemacht werden können, und empfiehlt die Aktivierung von Vorab-Rendering für diese Seiten. | Stellt eine vollständig gerenderte, KI-freundliche HTML-Momentaufnahme für den Agent-basierten Traffic bereit, der den zuvor ausgeblendeten Inhalt sichtbar macht. |
| LLM-freundliche Zusammenfassungen hinzufügen | Inhaltsoptimierung | Identifiziert lange oder komplexe Seiten, denen kurze Zusammenfassungen auf Seiten- oder Abschnittsebene fehlen, was es der KI erschwert, die Seiten schnell zu durchsuchen und zu analysieren. | Empfiehlt kurze, KI-generierte Zusammenfassungen auf Seiten- und Abschnittsebene, die wichtige Inhalte erfassen. | Fügt die Zusammenfassungen in die entsprechenden HTML-Abschnitte ein, wodurch die Interpretation und Beschreibung des Seiteninhalts durch Modelle verbessert wird. |
| Relevante häufig gestellte Fragen hinzufügen | Inhaltsoptimierung | Erkennt Absichtslücken im vorhandenen Seiteninhalt, die durch häufig gestellte Fragen geschlossen werden könnten. | Schlägt KI-generierte Inhalte für häufig gestellte Fragen vor, die auf die Benutzerabsicht und vorhandene Themen abgestimmt sind. | Fügt Inhalte häufig gestellter Fragen in das HTML ein, sodass Seiten in KI-gestützten Antworten leichter auffindbar und relevanter werden. |
| Komplexe Inhalte vereinfachen | Inhaltsoptimierung | Kennzeichnet Seiten mit komplexem Text, der das Verständnis durch KI behindern kann. | Stellt KI-generierte vereinfachte Versionen von komplexem Text bereit, wobei die ursprüngliche Bedeutung erhalten bleibt. | Schreibt komplexe Abschnitte auf der Seite um, wodurch die Lesbarkeit für KI verbessert wird. |

### Weitere Tools

Die Chrome-Erweiterung [Adobe LLM Optimizer: Ist Ihre Web-Seite zitierbar?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) zeigt an, auf wie viele Inhalte Ihrer Web-Seite LLMs zugreifen können und was verborgen bleibt. Dieses Tool wurde als kostenloses und eigenständiges Diagnose-Tool entwickelt und erfordert keine Produktlizenz oder Einrichtung.

Mit einem einzigen Klick können Sie die Maschinenlesbarkeit jeder Site bewerten. Sie können direkt vergleichen, was AI Agents bzw. menschliche Benutzende sehen, und abschätzen, wie viel Inhalt mithilfe von LLM Optimizer sichtbar gemacht werden könnte. Auf der Seite [Kann KI Ihre Website lesen?](https://business.adobe.com/de/blog/introducing-the-llm-optimizer-chrome-extension) finden Sie für weitere Informationen.

## Details zu einzelnen Möglichkeiten

In den folgenden Abschnitten finden Sie zusätzliche Details zu jeder von „Optimize at Edge“ unterstützten Möglichkeit.

### Inhaltssichtbarkeit wiederherstellen

Diese Möglichkeit kennzeichnet Seiten, auf denen wichtige Inhalte aufgrund des Client-seitigen Renderings für AI Agents verborgen bleiben. Für jede identifizierte Seite wird genau angezeigt, welche Inhalte in der Ansicht des AI Agents fehlen. Sichtbarkeitslücken werden hervorgehoben und Sie können Änderungen direkt anwenden, um die verborgenen Inhalte sichtbar zu machen. Wenn Sie diese Möglichkeit mit „Optimize at Edge“ bereitstellen, wird den LLM-Benutzer-Agents eine vorab gerenderte KI-optimierte Version der Seite bereitgestellt, damit sie auf den vollständigen Kontext zugreifen können, ohne dass JavaScript ausgeführt werden muss.
Dadurch wird sichergestellt, dass die Seite zunächst für AI Agents vollständig sichtbar ist. Zusätzliche Verbesserungen werden auf dieses vorab gerenderte HTML angewendet.

>[!IMPORTANT]
>Diese Vorab-Rendering-Funktion wird auf alle unten dargestellten Möglichkeiten bei der Bereitstellung mit „Optimize at Edge“ angewendet, um sicherzustellen, dass die Seite für AI Agents vollständig sichtbar ist.

### LLM-freundliche Zusammenfassungen hinzufügen

Diese Möglichkeit identifiziert Seiten, die von knappen Zusammenfassungen profitieren können, damit LLMs schnell verstehen können, worum es bei dem Seiteninhalt geht. Für jede Seite erkennt die Möglichkeit, wo eine Zusammenfassung am meisten benötigt wird, und erstellt KI-generierte Zusammenfassungen entweder auf Seitenebene oder auf Abschnittsebene. Wenn Sie mit „Optimize at Edge“ bereitstellen, werden diese Zusammenfassungen in das von AI Agents abgerufene HTML eingefügt, wodurch sich die Chancen erhöhen, dass Ihre Inhalte genauer beschrieben werden.

### Relevante häufig gestellte Fragen hinzufügen

Diese Möglichkeit kennzeichnet Seiten, die mit zusätzlichen Inhalten aus Fragen und Antworten besser auf die Benutzerabsicht und Prompts in der KI-gestützten Entdeckung abgestimmt werden könnten. Für jede Seite werden KI-generierte Blöcke mit häufig gestellten Fragen vorgeschlagen, die mit der Benutzerabsicht und dem Inhalt auf der Seite verknüpft sind. Mit „Optimize at Edge“ werden diese häufig gestellten Fragen in das HTML eingefügt, sodass Ihre Seite KI-freundlicher wird und die Wahrscheinlichkeit wächst, dass KI-Antworten direkt Ihren Anleitungen folgen.

### Komplexe Inhalte vereinfachen

Bei dieser Möglichkeit werden Seiten mit langen, komplexen Absätzen ermittelt, die das Verständnis von KI reduzieren können. Für jede Seite, die die Lesbarkeitsschwellen überschreitet, wird KI-generierter Inhalt erstellt, der verständlicher und einfacher zu erfassen ist, während die ursprüngliche Bedeutung erhalten bleibt. Bei der Bereitstellung am Edge führen diese dem Agent-basierten Traffic bereitgestellten vereinfachten Inhalte dazu, dass LLMs Ihre Inhalte besser interpretieren und zusammenfassen können.

## Automatische Optimierung am Edge

Für jede Möglichkeit können Sie die Optimierungen am Edge in der Vorschau anzeigen, bearbeiten, bereitstellen, live anzeigen und zurücksetzen.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Vorschau

**Vorschau** zeigt die Wirkung eines Vorschlags an, bevor er veröffentlicht wird. Dadurch wird ein Unterschied zwischen der aktuellen Seite und der KI-optimierten Version angezeigt, die nach der Anwendung des Vorschlags erwartet wird. In dieser Ansicht wird dieselbe Logik von „Optimize at Edge“ verwendet, die auch bei Live-Traffic angewendet wird, jedoch in einem isolierten Vorschaumodus. Dies wirkt sich nicht auf den Live-Traffic aus, da es sich um eine schreibgeschützte Simulation zur Prüfung handelt.

![Vorschau](/help/assets/optimize-at-edge/preview.png)

### Bearbeiten

**Bearbeiten** ermöglicht es Ihnen, den automatisch generierten Vorschlag vor der Bereitstellung zu verfeinern oder vollständig neu zu schreiben. Anstatt den Vorschlag einfach zu akzeptieren, behalten Sie durch den Bearbeitungs-Workflow die volle Kontrolle. Die Ansicht zeigt vorgeschlagene Änderungen in einem strukturierten Editor an, in dem Sie den Text ändern können, damit er besser zu Ihrer ursprünglichen Absicht passt. Nach erfolgter Bereitstellung wird den AI Agents die bearbeitete Version bereitgestellt.

![Bearbeiten](/help/assets/optimize-at-edge/edit.png)

### Bereitstellen

**Bereitstellen** veröffentlicht die ausgewählten Vorschläge, damit die optimierten Erlebnisse den AI Agents vom Edge aus bereitgestellt werden können. Wenn ein Routing des gesamten CDN erfolgt, werden alle Seiten in der Domain mit den neuen Änderungen in der Regel innerhalb von Minuten live geschaltet. Wenn das Routing nur für ausgewählte Pfade konfiguriert wurde, werden nur die Seiten auf der Zulassungsliste mit den Optimierungen live geschaltet.

![Bereitstellen](/help/assets/optimize-at-edge/deploy.png)

### Live anzeigen

Mit **Live anzeigen** können Sie überprüfen, ob die Optimierung live ist und sich für den Agent-basierten Traffic wie erwartet verhält. Dies ist eine Ansicht, auf die sonst nur schwer zugegriffen werden könnte. Sie können die Live-Seite unter „Korrigierte Vorschläge“ so anzeigen, wie sie für AI Agents gerendert wird.

![Live anzeigen](/help/assets/optimize-at-edge/view-live.png)

### Rollback

„Rollback“ setzt eine bereits bereitgestellte Optimierung sicher zurück. Die KI-exklusive Version der Seite wird normalerweise innerhalb von Minuten in den vorherigen Status zurückversetzt, sodass Sie bei Bedarf problemlos mit Optimierungen experimentieren können.

![Rollback](/help/assets/optimize-at-edge/rollback.png)

## Häufig gestellte Fragen

F. Welche Arten von LLMs werden mit „Optimize at Edge“ angesprochen?

Die Liste der anzusprechenden Benutzer-Agents definieren Sie im Rahmen des Onboardings.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

F. Was passiert, wenn mein Onboarding für „Optimize at Edge“ noch nicht erfolgt ist?

Wenn Sie auf **Optimierungen bereitstellen** klicken, bevor Sie die erforderliche Einrichtung abgeschlossen haben, werden keinerlei Änderungen auf Ihre Site angewendet. Stattdessen werden Sie in einem Popup-Dialogfeld aufgefordert, sich unter `llmo-at-edge@adobe.com` an unser Team zu wenden, um Unterstützung beim Onboarding zu erhalten. Bis zum Abschluss des Onboardings können Sie weiter die erkannten Möglichkeiten und Vorschläge erkunden, der Bereitstellungs-Workflow mit einem Klick bleibt jedoch inaktiv.

F: Was passiert, wenn der Inhalt an der Quelle aktualisiert wird?

Wir bedienen die optimierte Version Ihrer Seite aus dem Cache, solange sich die zugrunde liegende Quellseite nicht geändert hat. Wenn sich die Quelle jedoch für **Content-Sichtbarkeit wiederherstellen** ändert, wird unser System automatisch aktualisiert, sodass KI-Agenten immer die aktuellsten Inhalte erhalten. Dies liegt daran, dass wir niedrige TTL-Einstellungen (Cache Time To Live) verwenden (in der Reihenfolge von Minuten), sodass jedes Inhaltsupdate auf Ihrer Site eine neue Optimierung innerhalb dieses Triggers ermöglicht. Bei Inhaltsmöglichkeiten wie **LLM-freundliche Zusammenfassungen hinzufügen** überwacht LLM Optimizer die Quellseite auf Änderungen. Wenn eine Änderung erkannt wird, pausieren wir die Optimierung und markieren sie für eine menschliche Überprüfung, um zu verhindern, dass der Inhalt zwischen der für den Agenten sichtbaren Seite und der für den Menschen sichtbaren Seite verschoben wird.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

F. Ist „Optimize at Edge“ nur für Sites gedacht, die Adobe Edge Delivery Service (EDS) verwenden?

Nein. „Optimize at Edge“ ist CDN-unabhängig und funktioniert mit jeder Frontend-Architektur, nicht nur mit der, die im EDS-Stack von Adobe bereitgestellt wird.

F. Wie unterscheidet sich das Vorab-Rendering bei „Optimize at Edge“ vom herkömmlichen Server-seitigen Rendering (SSR)?

Beide lösen unterschiedliche Probleme und können zusammenarbeiten. Herkömmliches SSR rendert Server-seitige Inhalte, schließt jedoch keine Inhalte ein, die später im Browser geladen werden. Das Vorab-Rendering von „Optimize at Edge“ erfasst die Seite nach dem Laden von JavaScript- und Client-seitigen Daten und erzeugt die vollständig aufgebaute Version am CDN-Edge. SSR konzentriert sich auf die Verbesserung des menschlichen Erlebnisses, „Optimize at Edge“ verbessert das Web-Erlebnis für LLMs.

F. Was passiert, wenn ich Optimierungen für einige, aber nicht alle URLs in meiner Domain bereitstelle?

Nur die URLs, die Sie explizit optimieren, werden geändert. Für URLs mit bereitgestellten Opportunitys erhalten KI-Agenten die optimierte Version. Für URLs ohne bereitgestellte Opportunitys leitet unser Service die Originalseite einfach wie vorliegend weiter, ohne Änderungen anzuwenden oder sie in unserer Optimierungs-Cache-Ebene zu speichern. Dadurch wird sichergestellt, dass Sie Optimierungen selektiv bereitstellen können, ohne den Rest Ihrer Site zu beeinträchtigen.
