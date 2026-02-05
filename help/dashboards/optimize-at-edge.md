---
title: Optimieren bei Edge
description: Erfahren Sie, wie Sie in LLM Optimizer am CDN-Edge Optimierungen bereitstellen können, ohne dass Authoring-Änderungen erforderlich sind.
feature: Opportunities
source-git-commit: eb8bdf9144aebb85171a529a3cc25034be5b076e
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 1%

---


# Optimieren bei Edge

Diese Seite bietet einen detaillierten Überblick darüber, wie Optimierungen am CDN-Edge ohne Authoring-Änderungen bereitgestellt werden können. Es behandelt den Onboarding-Prozess, die verfügbaren Optimierungsmöglichkeiten und die automatische Optimierung am Edge.

>[!NOTE]
>Auf diese Funktion wird derzeit frühzeitig zugegriffen. Weitere Informationen zu Early Access-Programmen finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Was ist Optimieren bei Edge?

Optimize at Edge ist eine Edge-basierte Bereitstellungsfunktion in LLM Optimizer, die KI-freundliche Änderungen an LLM-Benutzeragenten bereitstellt. Im aktuellen Kontext bedeutet &quot;Edge&quot;, dass die Optimierung auf der CDN-Ebene angewendet wird. Da dies zu Optimierungen auf CDN-Ebene führt, sind keine Authoring-Änderungen im Content Management System (CMS) erforderlich, sodass Ihr Ursprungs-CMS unverändert bleibt. Durch diese Trennung können Sie die LLM-Sichtbarkeit verbessern, ohne Ihre vorhandenen Publishing-Workflows zu verändern. Es zielt nur auf den Traffic von Agenten ab und hat keine Auswirkungen auf menschliche Benutzer oder SEO-Bots. Wenn LLM Optimizer Möglichkeiten zur Seitenoptimierung erkennt, können Benutzende Fehlerbehebungen direkt am CDN-Edge bereitstellen.

Optimize bei Edge ist eine schnellere, schlankere Alternative zu herkömmlichen Fehlerbehebungen, die einen komplexen technischen Aufwand erfordern. Wie bereits erwähnt, sind nach Abschluss einer einmaligen Einrichtung keine Plattformänderungen oder langen Entwicklungszyklen erforderlich, um die Änderungen anzuwenden. Sie können Verbesserungen in Minuten veröffentlichen, ohne dass Entwicklerinteraktionen erforderlich sind. Dies ist eine unkodierte Methode, um Ihre Website für KI-Agenten zu optimieren.

Optimize at Edge wurde für Business-Anwender in den Bereichen Marketing, SEO, Content und digitale Strategien entwickelt. Business-Anwendern wird so die Möglichkeit geboten, das vollständige Journey in LLM Optimizer abzuschließen: durch Ermittlung von Chancen, Verständnis von Vorschlägen und einfache Bereitstellung der Fehlerbehebungen. Mit Optimieren in Edge können Benutzende eine Vorschau der Änderungen anzeigen, diese schnell am CDN-Edge bereitstellen und überprüfen, ob die Optimierungen live sind. Die Leistung kann im LLM Optimizer-Ökosystem verfolgt werden.

### Die wichtigsten Vorteile

* **Nur-KI-Bereitstellung:** Bereitstellung von optimiertem HTML nur für KI-Agenten ohne Auswirkungen auf menschliche Besucher oder SEO-Bots.
* **Schnellere Zyklen:** Veröffentlichungsänderungen in Minuten, nicht Wochen. Es sind keine Plattformänderungen oder lange Entwicklungszyklen erforderlich.
* **Reversible:** Wird mit der Funktion „Rollback mit einem Klick“ unterstützt, mit der die Seite in Minuten zurückgesetzt werden kann.
* **Keine Leistungsbeeinträchtigung:** Edge-basierte Optimierungen und das Caching wirken sich nicht auf die Site-Latenz aus.
* **CDN- und CMS-unabhängig** Funktioniert mit jeder CDN-Konfiguration und jedem Frontend-Setup, unabhängig vom Content Management System.

### Welche Chancen werden bei Edge mit Optimize unterstützt?

Chancen zur Verbesserung des agenten Web-Erlebnisses werden von Optimize bei Edge unterstützt. Weitere Informationen zu den einzelnen Opportunitys finden Sie sowohl auf [&#x200B; Seite „Opportunitys-Dashboard](/help/dashboards/opportunities.md) als auch im Abschnitt „Opportunitys“ auf der aktuellen Seite.

## Onboarding

Wenden Sie sich entweder an Ihr Adobe-Account-Team oder an das FDE-Team, um den Onboarding-Prozess zu starten. Ihr IT- oder CDN-Team muss außerdem die Voraussetzungen und den Einrichtungsprozess abschließen. Darüber hinaus können Sie sich auch an `llmo-at-edge@adobe.com` wenden, um weitere Unterstützung beim Onboarding zu erhalten.

Voraussetzungen für das Onboarding von Optimizer bei Edge:

* Schließen Sie den Onboarding-Prozess bei LLM Optimizer ab.
* Schließen Sie den Protokollweiterleitungsprozess für Ihre CDN-Protokolle ab.

Anforderungen an Ihr IT-/CDN-Team:

* API-Schlüssel generieren.
* Fügen Sie unter Edge Routing-Regeln im CDN Optimieren hinzu.
* Zulassungsliste der benutzerdefinierten Pfade für die gesamte Domain.
* Fügen Sie Target eine benutzerdefinierte Liste von LLM-Benutzeragenten hinzu.
* Stellen Sie sicher, dass `robots.txt` keine Benutzeragenten blockiert, die angesprochen werden sollen.
* Bestätigen Sie die Option Optimieren beim Edge-Routing in der Benutzeroberfläche von LLM Optimizer.

Als Anleitung für den Einrichtungsprozess dienen im Folgenden Beispielkonfigurationen für eine Reihe von CDN-Setups. Beachten Sie, dass diese Beispiele an Ihre tatsächliche Live-Konfiguration angepasst werden sollten. Es wird empfohlen, Änderungen zuerst in den unteren Umgebungen anzuwenden.

>[!BEGINTABS]

>[!TAB Adobe Managed CDN]

**Adobe Managed CDN**

Der Zweck dieser Konfiguration besteht darin, Anfragen mit agenten Benutzeragenten zu konfigurieren, die an den Optimizer-Service (`live.edgeoptimize.net`-Backend) weitergeleitet werden. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

```
curl -svo page.html https://frescopa.coffee/about-us --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Die Routing-Konfiguration erfolgt mithilfe einer [OriginSelector-CDN-Regel](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). Die Voraussetzungen lauten wie folgt:

* Festlegen der zu rotierenden Domain
* Festlegen der zu verlegenden Pfade
* Festlegen, welche Benutzeragenten weitergeleitet werden sollen (empfohlener Regex)

Um die Regel bereitzustellen, ist Folgendes erforderlich:

* Erstellen einer [Konfigurations-Pipeline](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/config-pipeline)
* Übertragen Sie die `cdn.yaml` Konfigurationsdatei in das Repository
* Ausführen der Konfigurations-Pipeline


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

Führen Sie zum Testen des Setups eine cURL aus und erwarten Sie Folgendes:

```
curl -svo page.html https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

>[!TAB Fastly (BYOCDN)]

**Edge Optimize BYOCDN - Fastly - VCL**

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![VCL-Snippets hinzufügen](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**VCL_RECV Snippet**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-fowarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=true"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
}
```

**VCL_HASH Snippet**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**VCL_DELIVER Snippet**

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

>[!TAB Akamai (BYOCDN)]

**Edge Optimize BYOCDN - Akamai**

Diese Konfiguration dient der Weiterleitung von Anfragen von Agenten-Benutzeragenten an den Edge Optimizer-Service (`live.edgeoptimize.net`-Backend). Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.


**Die folgende Akamai Property Manager-JSON-Regel leitet LLM-Benutzeragenten an Edge Optimize weiter:**

Die Konfiguration umfasst die folgenden Schritte:

**1. Festlegen von Routing-Kriterien (Zuordnung von Benutzeragenten)**

![Routing-Kriterien festlegen](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Festlegen des Ursprungs- und SSL-Verhaltens**

![Festlegen des Ursprungs- und SSL-Verhaltens](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Cache-Schlüsselvariable festlegen**

![Cache-Schlüsselvariable festlegen](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Caching-Regeln**

![Zwischenspeicherungsregeln](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Eingehende Anfragekopfzeilen ändern**

![Eingehende Anfragekopfzeilen ändern](/help/assets/optimize-at-edge/akamai-step5-request.png)

**6. Eingehende Antwortkopfzeilen ändern**

![Eingehende Antwortkopfzeilen ändern](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Cache-ID-Änderung**

![Cache-ID-Änderung](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Standort-Failover**

![Standort-Failover](/help/assets/optimize-at-edge/akamai-step8-failover.png)

![Failover-Verhalten](/help/assets/optimize-at-edge/akamai-step8-failover-behaviors.png)

![Failover-Regeln](/help/assets/optimize-at-edge/akamai-step8-failover-rules.png)

![Verhaltensantwort](/help/assets/optimize-at-edge/akamai-step8-behaviors-response.png)

Führen Sie zum Testen des Setups eine cURL aus und erwarten Sie Folgendes:

```
curl -svo page.html https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

>[!ENDTABS]

>[!NOTE]
>Wenden Sie sich bei anderen CDN-Anbietern an `llmo-at-edge@adobe.com`, um Ihre IT-/CDN-Teams beim Onboarding zu unterstützen. Sobald die Einrichtungskonfigurationen abgeschlossen sind, können Sie bei den Opportunities von Edge in LLM Optimizer Optimierungsvorschläge bereitstellen.

## Möglichkeiten

In der folgenden Tabelle sind Möglichkeiten aufgeführt, die das agentische Web-Erlebnis verbessern können und die bei Edge von Optimize unterstützt werden.

| Möglichkeit | Typ | Automatisch identifizieren | Automatische Vorschläge | Automatische Optimierung |
|---------|----------|----------|----------|----------|
| Inhaltssichtbarkeit wiederherstellen | Technisches GEO | Erkennt Seiten, auf denen kritische Inhalte vor KI-Agenten verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die wiederhergestellt werden können. | Hebt Inhalte hervor, die für KI-Agenten verfügbar gemacht werden können, und empfiehlt, das Pre-Rendering für diese Seiten zu aktivieren. | Stellt einen vollständig gerenderten, KI-freundlichen HTML-Schnappschuss für den Agent-Traffic bereit, der den zuvor ausgeblendeten Inhalt wiederherstellt. |
| Optimieren von Überschriften für LLMs | Inhaltsoptimierung | Scannt Überschriften, um leere, doppelte, fehlende oder mehrdeutige Überschriften zu erkennen, die die Maschinenlesbarkeit beeinträchtigen können. | Schlägt eine sauberere Überschriftenhierarchie und verbesserte Beschriftungen vor und zeigt eine Vorschau der aktualisierten Struktur für jede Seite an. | Fügt die verbesserte Überschriftenstruktur für KI-Agenten ein, behält Ihr visuelles Design bei und macht die Seite für LLMs besser lesbar. |
| Hinzufügen von LLM-freundlichen Zusammenfassungen | Inhaltsoptimierung | kennzeichnet lange oder komplexe Seiten, denen kurze Zusammenfassungen auf Seiten- oder Abschnittsebene fehlen, was es KI erschwert, diese schnell zu durchsuchen und zu verstehen. | empfiehlt kurze, KI-generierte Zusammenfassungen auf Seiten- und Abschnittsebene, die wichtige Inhalte erfassen. | Fügt die Zusammenfassungen in die entsprechenden HTML-Abschnitte ein, wodurch die Interpretation und Beschreibung des Seiteninhalts durch Modelle verbessert wird. |
| Relevante FAQs hinzufügen | Inhaltsoptimierung | Erkennt Absichtslücken im vorhandenen Seiteninhalt, die von den häufig gestellten Fragen profitieren könnten. | Schreibt KI-generierte FAQ-Inhalte vor, die auf die Benutzerabsicht und vorhandene Themen abgestimmt sind. | Bringt FAQ-Inhalte in die HTML ein, sodass Seiten in KI-gestützten Antworten leichter auffindbar und relevanter werden. |
| Vereinfachung komplexer Inhalte | Inhaltsoptimierung | Kennzeichnet Seiten mit komplexem Text, der das Verständnis von KI behindern kann. | Stellt KI-generierte vereinfachte Versionen von komplexem Text bereit, wobei die ursprüngliche Bedeutung erhalten bleibt. | Schreibt komplexe Abschnitte auf der Seite neu, wodurch die Lesbarkeit der KI verbessert wird. |

### Weitere Tools

Die [Adobe LLM Optimizer: Ist Ihre Webseite zitierbar?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) Chrome-Erweiterung zeigt an, auf wie viel Ihrer Webseiteninhalte LLMs zugreifen können und was verborgen bleibt. Es wurde als kostenloses, eigenständiges Diagnosewerkzeug entwickelt und erfordert keine Produktlizenz oder Einrichtung.

Mit einem einzigen Klick können Sie die Maschinenlesbarkeit jeder Site bewerten. Sie können einen direkten Vergleich zwischen dem, was KI-Agenten sehen, und dem, was menschliche Benutzer sehen, anzeigen und schätzen, wie viel Inhalt mithilfe von LLM Optimizer wiederhergestellt werden könnte. Siehe die [Kann KI Ihre Website lesen?](https://business.adobe.com/de/blog/introducing-the-llm-optimizer-chrome-extension) Seite für weitere Informationen.

## Opportunities detailliert

In den folgenden Abschnitten können Sie zusätzliche Details zu jeder Opportunity anzeigen, die von Optimieren bei Edge unterstützt wird.

### Inhaltssichtbarkeit wiederherstellen

Diese Gelegenheit kennzeichnet Seiten, auf denen wichtige Inhalte für KI-Agenten aufgrund des Client-seitigen Renderings ausgeblendet sind. Für jede identifizierte Seite wird genau angezeigt, welche Inhalte in der KI-Agent-Ansicht fehlen, Sichtbarkeitslücken werden hervorgehoben und Sie können Änderungen direkt anwenden, um die ausgeblendeten Inhalte wiederherzustellen. Wenn Sie diese Opportunity mit Optimieren in Edge bereitstellen, wird eine vorgerenderte, KI-optimierte Version der Seite LLM-Benutzeragenten bereitgestellt, damit sie auf den vollständigen Kontext zugreifen können, ohne JavaScript auszuführen.
Dadurch wird sichergestellt, dass die Seite zunächst für KI-Agenten vollständig sichtbar ist. Zusätzliche Verbesserungen werden auf diese vorab gerenderte HTML angewendet.

>[!IMPORTANT]
>Diese Vorab-Rendering-Funktion gilt automatisch für alle unten dargestellten Opportunitys bei der Bereitstellung von Optimieren in Edge, um sicherzustellen, dass die Seite für KI-Agenten vollständig sichtbar ist.

### Optimieren von Überschriften für LLMs

Diese Opportunity erkennt Seiten, bei denen die Überschriftenstruktur es KI-Agenten erschwert, die Seite aufgrund leerer, doppelter, fehlender oder mehrdeutiger Überschriften zu verstehen. Für jede betroffene Seite zeigt die Opportunity die suboptimalen Überschriften und empfiehlt eine klarere Hierarchie. Bei der Bereitstellung mit „Optimieren“ in Edge werden die verbesserten Überschriften in dem HTML angewendet, das dem Agentdatenverkehr dient. Dies erleichtert die Maschinenlesbarkeit, während das Layout für Menschen unverändert bleibt.

### Hinzufügen von LLM-freundlichen Zusammenfassungen

Diese Opportunity identifiziert Seiten, die von knappen Zusammenfassungen profitieren können, damit LLMs schnell verstehen können, worum es bei dem Seiteninhalt geht. Für jede Seite erkennt die Opportunity, wo eine Zusammenfassung am meisten benötigt wird, und erstellt KI-generierte Zusammenfassungen entweder auf Seitenebene oder auf Abschnittsebene. Wenn Sie bei Edge mit Optimieren bereitstellen, werden diese Zusammenfassungen in die HTML eingefügt, die KI-Agenten abrufen, wodurch sich die Chancen erhöhen, dass Ihre Inhalte genauer beschrieben werden.

### Relevante FAQs hinzufügen

Diese Opportunity kennzeichnet Seiten, auf denen zusätzliche Q&amp;A-Inhalte besser mit der Benutzerabsicht und den Eingabeaufforderungen in der KI-gestützten Erkennung übereinstimmen. Für jede Seite werden von KI generierte FAQ-Blöcke vorgeschlagen, die mit der Benutzerabsicht und dem Inhalt auf der Seite verknüpft sind. Mit Optimize bei Edge werden diese FAQs in die HTML eingefügt, was Ihre Seite KI-freundlicher macht und die Wahrscheinlichkeit erhöht, dass KI-Antworten direkt Ihre Anleitung widerspiegeln.

### Vereinfachung komplexer Inhalte

Bei dieser Gelegenheit werden Seiten mit langen, komplexen Absätzen gefunden, die das Verständnis von KI reduzieren können. Für jede Seite, die die Lesbarkeitsschwellen überschreitet, wird ein KI-generierter Inhalt erstellt, der einfacher und einfacher zu scannen ist, während die ursprüngliche Bedeutung erhalten bleibt. Bei der Bereitstellung am Edge helfen die vereinfachten Inhalte, die für den Agent-Traffic bereitgestellt werden, LLMs, Ihre Inhalte besser zu interpretieren und zusammenzufassen.

## Automatische Optimierung bei Edge

Für jede Opportunity können Sie die Optimierungen am Edge in der Vorschau anzeigen, bearbeiten, bereitstellen, live anzeigen und zurücksetzen.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Vorschau

**Vorschau** zeigt die Wirkung eines Vorschlags an, bevor er veröffentlicht wird. Dadurch wird ein Unterschied zwischen der aktuellen Seite und der KI-optimierten Version angezeigt, die nach der Anwendung des Vorschlags erwartet wird. In dieser Ansicht wird dieselbe Logik von Optimize in Edge verwendet, die Live-Traffic steuert, jedoch in einem isolierten Vorschaumodus. Dies wirkt sich nicht auf den Live-Traffic aus, da es sich um eine schreibgeschützte Simulation zur Überprüfung handelt.

![Vorschau](/help/assets/optimize-at-edge/preview.png)

### Bearbeiten

**Bearbeiten** ermöglicht es Ihnen, den automatisch generierten Vorschlag vor der Bereitstellung zu verfeinern oder vollständig neu zu schreiben. Anstatt den Vorschlag zu akzeptieren, behalten Sie durch den Workflow „Bearbeiten“ die volle Kontrolle. Die Ansicht zeigt vorgeschlagene Änderungen in einem strukturierten Editor an, in dem Sie den Text ändern können, damit er besser zu Ihrem ursprünglichen Zweck passt. Die bearbeitete Version wird dann nach der Bereitstellung für KI-Agenten bereitgestellt.

![Bearbeiten](/help/assets/optimize-at-edge/edit.png)

### Bereitstellen

**Bereitstellen** veröffentlicht die ausgewählten Vorschläge, damit die optimierten Erlebnisse den KI-Agenten vom Edge aus bereitgestellt werden können. Wenn das CDN vollständig weitergeleitet wird, werden alle Seiten in der Domain mit den neuen Änderungen in der Regel innerhalb von Minuten live geschaltet. Auf die Zulassungsliste setzen Wenn das Routing nur für ausgewählte Pfade konfiguriert wurde, werden nur die ausgewählten Seiten mit den Optimierungen live geschaltet.

![Bereitstellen](/help/assets/optimize-at-edge/deploy.png)

### Live anzeigen

Mit **Live anzeigen** können Sie überprüfen, ob die Optimierung live ist und sich wie erwartet für den agenten Traffic verhält, eine Ansicht, auf die sonst schwer zugegriffen werden könnte. Sie können die Live-Seite unter Feste Vorschläge anzeigen. Dadurch wird die Seite wie für KI-Agenten gezeigt gerendert.

![Live anzeigen](/help/assets/optimize-at-edge/view-live.png)

### Rollback

Das Rollback setzt eine zuvor bereitgestellte Optimierung sicher zurück. Die Nur-KI-Version der Seite wird normalerweise innerhalb von Minuten in den vorherigen Status zurückversetzt, sodass Sie bei Bedarf problemlos mit Optimierungen experimentieren können.

![Rollback](/help/assets/optimize-at-edge/rollback.png)

## Häufig gestellte Fragen

F. Welche Arten von LLMs zielen Sie bei Edge mit Optimize ab?

Die Liste der Benutzeragenten, die angesprochen werden sollen, wird von Ihnen während des Onboarding-Prozesses definiert.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

F. Was passiert, wenn ich noch nicht zu Optimize bei Edge hinzugefügt habe?

Wenn Sie auf **Optimierungen bereitstellen** klicken, bevor Sie die erforderliche Einrichtung abgeschlossen haben, wird nichts auf Ihre Site angewendet. Stattdessen werden Sie in einem Popup-Dialogfeld aufgefordert, sich an unser Team unter `llmo-at-edge@adobe.com` zu wenden, um Unterstützung beim Onboarding zu erhalten. Bis zum Abschluss des Onboarding können Sie weiterhin die erkannten Opportunitys und Vorschläge erkunden, aber der Bereitstellungs-Workflow mit einem Klick bleibt inaktiv.

F: Was passiert, wenn der Inhalt an der Quelle aktualisiert wird?

Wir bedienen die optimierte Version der Seite aus dem Cache, solange sich die zugrunde liegende Quellseite nicht geändert hat. Wenn sich die Quelle jedoch ändert, wird unser System automatisch aktualisiert, sodass KI-Agenten immer die aktuellsten Inhalte erhalten. Dies liegt daran, dass wir niedrige TTL-Einstellungen (Cache Time To Live) verwenden (in der Reihenfolge von Minuten), sodass jedes Inhaltsupdate auf Ihrer Site eine neue Optimierung innerhalb dieses Triggers ermöglicht. <!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

F. Ist „Optimieren“ bei Edge nur für Sites, die Adobe Edge Delivery Service (EDS) verwenden?

Nein. Optimize at Edge ist CDN-unabhängig und funktioniert mit jeder Frontend-Architektur, nicht nur mit der, die im EDS-Stack von Adobe bereitgestellt wird.

F. Wie unterscheidet sich das Optimieren beim Edge-Pre-Rendering vom herkömmlichen Server-seitigen Rendering (SSR)?

Beide lösen unterschiedliche Probleme und können zusammenarbeiten. Herkömmliche SSR rendert Server-seitige Inhalte, schließt jedoch keine Inhalte ein, die später im Browser geladen werden. Optimieren am Edge-Pre-Rendering : Erfasst die Seite nach dem Laden von JavaScript- und Client-seitigen Daten und erzeugt die vollständig assemblierte Version am CDN-Edge. SSR konzentriert sich auf die Verbesserung des menschlichen Erlebnisses und „Optimize“ bei Edge verbessert das Web-Erlebnis für LLMs.
