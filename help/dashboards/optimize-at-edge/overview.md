---
title: Optimize at Edge
description: Erfahren Sie, wie Sie in LLM Optimizer Optimierungen am CDN-Edge bereitstellen können, ohne dass Authoring-Änderungen erforderlich sind.
feature: Opportunities
autotag-review: '2026-05-15T17:55:41.072Z'
TQID: 'https://experienceleague.adobe.com/kMxoKtrfyzxIpLJP9nt-rq6GP37ICCNe4XienUKqDZE'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: d1956731-2adb-4bb7-8301-2b239254ac72id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e9001ce2-5245-4a8e-8601-dd958009072f
source-git-commit: 559e77adedb1a93215090441c93c2aa6dc664e5f
workflow-type: tm+mt
source-wordcount: 2931
ht-degree: 63%

---


# Optimize at Edge

Diese Seite bietet einen detaillierten Überblick darüber, wie Optimierungen am CDN-Edge ohne Authoring-Änderungen bereitgestellt werden können. Sie behandelt den Onboarding-Prozess, die verfügbaren Optimierungsmöglichkeiten und die automatische Optimierung am Edge.

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

„Optimize at Edge“ unterstützt Möglichkeiten zur Verbesserung des Agent-basierten Web-Erlebnisses. Weitere Informationen zu den einzelnen Möglichkeiten finden Sie sowohl auf der Seite [Dashboard „Möglichkeiten“](/help/dashboards/opportunities-overview.md) als auch im Abschnitt „Möglichkeiten“ auf dieser Seite.

## Onboarding

<!--You should reach out to either your Adobe account team or the FDE team to start the onboarding process. Your IT or CDN team is also required to complete the pre-requisites and setup process. Additionally, you can also contact `llmo-at-edge@adobe.com` for further onboarding assistance.-->

Starten Sie den Onboarding-Prozess in Ihrem LLM Optimizer-Konto:

1. Wählen Sie im Dashboard **Kundenkonfiguration** die Registerkarte **CDN-Konfiguration** aus.
1. Klicken Sie auf **CDN integrieren**.
   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/cc-cdn.png)
1. Kundschaften von AEM Cloud Service Managed Fastly können die Routing-Einrichtung selbstständig durchführen und direkt in der LLM Optimizer-Benutzeroberfläche abschließen. Für Kundschaften, die andere CDN-Anbieter verwenden, muss Ihr IT-/CDN-Team die erforderlichen Einrichtungs- und Voraussetzungsschritte durchführen. Weitere Anleitungen finden Sie in den Handbüchern mit Beispiel-CDNs unten.

>[!NOTE]
>Bitte beachten Sie die folgenden detaillierten Anleitungen, die den gesamten Onboarding-Fluss abdecken. Bei Problemen, die nicht in diesen Handbücher behandelt werden, können Sie sich an `llmo-at-edge@adobe.com` wenden.

Voraussetzungen für Ihr IT-/CDN-Team:

* Fügen Sie den Benutzer-Agent `*AdobeEdgeOptimize/1.0*` zur Zulassungsliste in der Datei robots.txt Ihrer Site oder zu den Regeln für die Verwaltung des Bot-Traffics hinzu.
* Stellen Sie sicher, dass Seiten nicht auf Domain- oder CDN-Ebene blockiert werden.
* Fügen Sie Routing-Regeln für „Optimize at Edge“ im CDN hinzu.
* Wenn Ihr CDN über WAF- oder Bot-Manager-Regeln verfügt, setzen Sie den `*AdobeEdgeOptimize/1.0*`-Benutzer-Agent auf die Zulassungsliste. Wenn eine zusätzliche Überprüfung erforderlich ist, konfigurieren Sie den Header `x-edgeoptimize-fetcher-key`. Jedes BYOCDN-Handbuch enthält die folgenden Schritte.
* Prüfen Sie das Routing für „Optimize at Edge“ in der Benutzeroberfläche von LLM Optimizer.

Das folgende Diagramm zeigt, wie Anfragen eine BYOCDN-Einrichtung mit „Optimize at Edge“ durchlaufen:

![BYOCDN-Anfragefluss](/help/assets/optimize-at-edge/byocdn-request-flow.png)

>[!IMPORTANT]
>Routing muss im äußeren CDN (dem CDN, das dem Client am nächsten ist) konfiguriert werden. Wenn Sie über mehrere CDNs verfügen, kann das Routing nur im äußeren CDN erfolgen.

Um den Einrichtungsprozess zu durchlaufen, wählen Sie unten Ihren CDN-Anbieter aus und befolgen Sie die entsprechenden Konfigurationsanleitungen. Beachten Sie, dass diese Beispiele an Ihre tatsächliche Live-Konfiguration angepasst werden müssen. Wir empfehlen, Änderungen zuerst in den niedrigeren Umgebungen anzuwenden.

### CDN-Konfigurationsanleitungen

| CDN-Anbieter | Typ | Handbuch |
|---|---|---|
| Von AEM Cloud Service verwaltetes CDN (Fastly) | Von Adobe verwaltet | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/aemcs-managed-cdn.md) |
| Fastly (BYOCDN) | Einbinden Ihres eigenen CDN | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/fastly-byocdn.md) |
| Akamai (BYOCDN) | Einbinden Ihres eigenen CDN | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/akamai-byocdn.md) |
| Cloudflare (BYOCDN) | Einbinden Ihres eigenen CDN | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/cloudflare-byocdn.md) |
| CloudFront (BYOCDN) | Einbinden Ihres eigenen CDN | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/cloudfront-byocdn.md) |
| Azure-Haustür (BYOCDN) | Einbinden Ihres eigenen CDN | [Setup-Anleitungen anzeigen](/help/dashboards/optimize-at-edge/azure-front-door-byocdn.md) |

>[!NOTE]
>
>Wenn Ihr CDN-Anbieter oben nicht aufgeführt ist oder wenn Sie Ihre Domain oder Ihre E-Mail-Adresse auf der Benutzeroberfläche von LLM Optimizer nicht finden, wenden Sie sich bitte an `llmo-at-edge@adobe.com`, um Unterstützung beim Onboarding zu erhalten. Sobald die Einrichtungskonfigurationen abgeschlossen sind, können Sie Empfehlungen für Möglichkeiten von „Optimize at Edge“ in LLM Optimizer bereitstellen.

Jede der oben genannten CDN-Setup-Anleitungen enthält am Ende detaillierte Überprüfungsschritte, mit denen Sie sicherstellen können, dass der Agent-basierter Traffic korrekt weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

## Möglichkeiten

In der folgenden Tabelle sind Möglichkeiten aufgeführt, die das Agent-basierte Web-Erlebnis verbessern können und durch „Optimize at Edge“ unterstützt werden.

| Möglichkeit | Typ | Automatische Identifikation | Automatische Vorschläge | Automatische Optimierung |
|---------|----------|----------|----------|----------|
| [Content-Sichtbarkeit wiederherstellen](/help/dashboards/opportunities/recover-content-visibility.md) | Technische GEO | Erkennt Seiten, auf denen kritische Inhalte vor AI Agents verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die sichtbar gemacht werden können. | Hebt Inhalte hervor, die für AI Agents verfügbar gemacht werden können, und empfiehlt die Aktivierung von Vorab-Rendering für diese Seiten. | Stellt eine vollständig gerenderte, KI-freundliche HTML-Momentaufnahme für den Agent-basierten Traffic bereit, der den zuvor ausgeblendeten Inhalt sichtbar macht. |
| [Anreichern von Produktdetailseiten](/help/dashboards/opportunities/enrich-product-detail-pages.md) | Technische GEO | Vergleicht für Adobe Commerce-Storefronts vollständige Katalogdaten mit dem, auf was KI-Agenten auf jeder Produktdetailseite zugreifen können; zeigt PDPs an, auf denen Varianten, Spezifikationen, Attribute und zugehörige Katalogfelder im für Agenten sichtbaren HTML fehlen, priorisiert nach Agententraffic. | Zeigt, dass in der Agentenansicht wiederherstellbare Kataloginformationen fehlen und warum dies für die LLM-gesteuerte Produkterkennung wichtig ist. | Stellt einen vollständig vorgerenderten, KI-freundlichen HTML-Schnappschuss für den Agent-Traffic am CDN-Edge bereit, sodass Agenten umfangreichen Produktkontext aus Ihrem Katalog erhalten, ohne dass CMS- oder Katalogänderungen erforderlich sind. |
| [LLM-freundliche Zusammenfassungen hinzufügen](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Inhaltsoptimierung | kennzeichnet Seiten mit hohem Traffic, denen es an prägnanten Zusammenfassungen und strukturierten Schlüsselpunkten auf Seiten- oder Abschnittsebene mangelt, wodurch das Scannen und Interpretieren für KI-Agenten erschwert wird. | empfiehlt kurze, KI-generierte Zusammenfassungen und wichtige Punkte, die auf vorhandenen Inhalten basieren. | Fügt Zusammenfassungen und wichtige Punkte in die entsprechenden HTML-Abschnitte ein, um zu verbessern, wie Modelle den Seiteninhalt interpretieren und beschreiben. |
| [Relevante FAQs hinzufügen](/help/dashboards/opportunities/add-relevant-faqs.md) | Inhaltsoptimierung | kennzeichnet Seiten mit hohem Traffic, denen strukturierte Fragen und Antworten fehlen, die auf Ihr Eingabeaufforderungsset abgestimmt sind, wodurch es für KI-Agenten schwieriger wird, Benutzerfragen mit Ihrer Seite abzugleichen. | Empfiehlt KI-generierte FAQ-Inhalte, die auf die Benutzerabsicht und vorhandene Seitenthemen abgestimmt sind. | Fügt Inhalte häufig gestellter Fragen in das HTML ein, sodass Seiten in KI-gestützten Antworten leichter auffindbar und relevanter werden. |
| [Vereinfachung komplexer Inhalte](/help/dashboards/opportunities/simplify-complex-content.md) | Inhaltsoptimierung | Kennzeichnet Seiten mit komplexem Text, der das Verständnis durch KI behindern kann. | Stellt KI-generierte vereinfachte Versionen von komplexem Text bereit, wobei die ursprüngliche Bedeutung erhalten bleibt. | Schreibt komplexe Abschnitte auf der Seite um, wodurch die Lesbarkeit für KI verbessert wird. |
| [Inhaltsverzeichnis hinzufügen](/help/dashboards/opportunities/add-table-of-contents.md) | Technische GEO | Erkennt Seiten ohne klare strukturelle Organisation oder Navigationsüberschriften, was es für KI-Agenten schwierig macht, Inhalte zu analysieren und Benutzerabfragen zuzuordnen. | Schlägt ein strukturiertes Inhaltsverzeichnis mit verankerten Überschriften vor, die die Hauptabschnitte der Seite widerspiegeln. | Fügt ein Inhaltsverzeichnis in HTML ein, wodurch die Seitenstruktur verbessert wird, sodass KI-Modelle relevante Abschnitte leichter extrahieren, zuordnen und zitieren können. |
| [Hinzufügen von Zusammenfassungen von Multimedia-Transkripten](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Inhaltsoptimierung | kennzeichnet Seiten, auf denen wichtige Informationen ohne maschinenlesbare Transkripte oder Zusammenfassungen in Videos oder andere Medien eingebettet sind, sodass diese Inhalte für KI-Agenten schwer zu verwenden sind. Zeigt betroffene URLs und empfohlenen Text an. | empfiehlt KI-generierte Transkriptzusammenfassungen, die auf den Medien und der Seite basieren. | Fügt Transkriptzusammenfassungen in die HTML ein, damit der Agent-Traffic maschinenlesbaren Text erhält (z. B. in der Nähe des entsprechenden Videos). |

### Weitere Tools

Die Browser-Erweiterung [Content Visibility Checker](https://chromewebstore.google.com/detail/ai-content-visibility-che/jbjngahjjdgonbeinjlepfamjdmdcbcc) zeigt, auf wie viele Inhalte Ihrer Web-Seiten LLMs zugreifen können und was verborgen bleibt. Dieses Tool wurde als kostenloses und eigenständiges Diagnose-Tool entwickelt und erfordert keine Produktlizenz oder Einrichtung.

Mit einem einzigen Klick können Sie die Maschinenlesbarkeit jeder Site bewerten. Sie können direkt vergleichen, was AI Agents bzw. menschliche Benutzende sehen, und abschätzen, wie viel Inhalt mithilfe von LLM Optimizer sichtbar gemacht werden könnte. Auf der Seite [Kann KI Ihre Website lesen?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) finden Sie für weitere Informationen.

## Details zu einzelnen Möglichkeiten

In den folgenden Abschnitten finden Sie zusätzliche Details zu jeder von „Optimize at Edge“ unterstützten Möglichkeit.

### Inhaltssichtbarkeit wiederherstellen

Diese Gelegenheit kennzeichnet Seiten, auf denen wichtige Inhalte für KI-Agenten aufgrund des Client-seitigen Renderings ausgeblendet sind. Für jede identifizierte Seite wird genau angezeigt, welche Inhalte in der KI-Agent-Ansicht fehlen, Sichtbarkeitslücken werden hervorgehoben und Sie können Änderungen direkt anwenden, um die ausgeblendeten Inhalte wiederherzustellen. Wenn Sie diese Opportunity mit Optimieren in Edge bereitstellen, wird eine vorgerenderte, KI-optimierte Version der Seite LLM-Benutzeragenten bereitgestellt, damit sie auf den vollständigen Kontext zugreifen können, ohne JavaScript auszuführen.
Dadurch wird sichergestellt, dass die Seite zunächst für KI-Agenten vollständig sichtbar ist. Zusätzliche Verbesserungen werden auf diese vorab gerenderte HTML angewendet.

>[!IMPORTANT]
>Diese Vorab-Rendering-Funktion wird auf alle unten dargestellten Möglichkeiten bei der Bereitstellung mit „Optimize at Edge“ angewendet, um sicherzustellen, dass die Seite für AI Agents vollständig sichtbar ist.

Unter [Wiederherstellen der Content-Sichtbarkeit](/help/dashboards/opportunities/recover-content-visibility.md) finden Sie einen Überblick über Dashboards, Bereitstellungsschritte und häufig gestellte Fragen.

### Anreichern von Produktdetailseiten

Diese Opportunity zielt auf Adobe Commerce-Produktdetailseiten ab, auf denen Käufer den vollständigen Produktkontext durch interaktive Storefront-Erlebnisse sehen, KI-Agenten jedoch nur einen oberflächlichen HTML-Schnappschuss erhalten. Der Katalogagent vergleicht Ihren maßgeblichen Commerce-Katalog mit dem für den Agenten sichtbaren PDP, listet alle bedeutsamen Lücken auf (z. B. Varianten oder Spezifikationen, die in statischen HTML nie vorkommen) und ermöglicht Ihnen die Bereitstellung einer Bot-only-Edge-Antwort, die die Parität für LLM-Crawlers wiederherstellt, ohne Katalogdatensätze oder die menschliche Benutzeroberfläche zu ändern.

Unter [Produktdetailseiten anreichern](/help/dashboards/opportunities/enrich-product-detail-pages.md) finden Sie eine Anleitung zum Dashboard, Bereitstellungsschritte und häufig gestellte Fragen.

### LLM-freundliche Zusammenfassungen hinzufügen

Diese Opportunity identifiziert Seiten mit hohem Traffic, die von knappen Zusammenfassungen und strukturierten Schlüsselpunkten profitieren können, sodass LLMs Ansprüche auf der Seite schnell verstehen können. Für jede Seite wird erkannt, wo eine Zusammenfassung am meisten benötigt wird, und es werden KI-generierte Zusammenfassungen (und ggf. Schlüsselpunkte) auf Seiten- oder Abschnittsebene vorgeschlagen, die auf vorhandenen Inhalten basieren. Bei der Bereitstellung von mit Optimieren auf Edge wird dieser Inhalt in die HTML eingefügt, die KI-Agenten abrufen, wodurch sich die Genauigkeit der Darstellung Ihrer Marke in KI-Antworten verbessert.

Weitere [ zu dieser Opportunity finden Sie ](/help/dashboards/opportunities/add-llm-friendly-summaries.md) „LLM-freundliche Zusammenfassungen hinzufügen .

### Relevante häufig gestellte Fragen hinzufügen

Bei dieser Gelegenheit werden Seiten mit hohem Traffic gekennzeichnet, auf denen zusätzliche Q&amp;A-Inhalte besser mit der Benutzerabsicht und den Eingabeaufforderungen bei der KI-gestützten Erkennung übereinstimmen könnten. Für jede Seite werden von KI generierte FAQ-Blöcke vorgeschlagen, die mit der Eingabeaufforderung und dem Inhalt auf der Seite verknüpft sind. Mit Optimize bei Edge werden diese FAQs in die HTML eingefügt, was Ihre Seite KI-freundlicher macht und die Wahrscheinlichkeit erhöht, dass KI-Antworten direkt Ihre Anleitung widerspiegeln.

Unter [Relevante FAQs hinzufügen](/help/dashboards/opportunities/add-relevant-faqs.md) finden Sie eine Anleitung zum Dashboard, Bereitstellungsschritte und häufig gestellte Fragen.

### Komplexe Inhalte vereinfachen

Bei dieser Möglichkeit werden Seiten mit langen, komplexen Absätzen ermittelt, die das Verständnis von KI reduzieren können. Für jede Seite, die die Lesbarkeitsschwellen überschreitet, wird KI-generierter Inhalt erstellt, der verständlicher und einfacher zu erfassen ist, während die ursprüngliche Bedeutung erhalten bleibt. Bei der Bereitstellung am Edge führen diese dem Agent-basierten Traffic bereitgestellten vereinfachten Inhalte dazu, dass LLMs Ihre Inhalte besser interpretieren und zusammenfassen können.

Unter [Vereinfachen komplexer Inhalte](/help/dashboards/opportunities/simplify-complex-content.md) finden Sie eine Anleitung zum Dashboard, Bereitstellungsschritte und häufig gestellte Fragen.

### Inhaltsverzeichnis hinzufügen

Diese Opportunity erkennt Seiten, die für KI-Agenten schwer zu navigieren sind, da Überschriften und Abschnittsstruktur unklar sind oder fehlen. Für jede betroffene Seite wird ein strukturiertes Inhaltsverzeichnis mit verankerten Einträgen vorgeschlagen, die auf die Hauptabschnitte ausgerichtet sind. Wenn Sie bei Edge mit Optimieren bereitstellen, wird dieses Inhaltsverzeichnis in die HTML eingefügt, damit -Modelle Benutzerabfragen zuverlässiger den rechten Teilen der Seite zuordnen und sie zitieren können.

Unter [Inhaltsverzeichnis hinzufügen](/help/dashboards/opportunities/add-table-of-contents.md) finden Sie eine exemplarische Vorgehensweise für Dashboards, Bereitstellungsschritte und Anleitungen für den frühzeitigen Zugriff.

### Hinzufügen von Multimedia-Transkriptzusammenfassungen

Diese Opportunity zielt auf Seiten ab, auf denen wichtige Informationen nur in der Videowiedergabe enthalten sind, ohne Transkripte oder Textzusammenfassungen, die KI-Agenten lesen können. Für jede Seite werden KI-generierte Transkripte und kurze Zusammenfassungen der wichtigsten Punkte aus den Medien empfohlen. Bei „Optimieren“ in Edge werden diese Zusammenfassungen als maschinenlesbarer Text zur HTML hinzugefügt, sodass Agenten dieselbe Substanz verwenden können, die Besuchende durch das Ansehen des Videos erhalten.

Unter [Zusammenfassungen von Multimedia-](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) hinzufügen“ finden Sie eine exemplarische Vorgehensweise im Dashboard, Bereitstellungsschritte und häufig gestellte Fragen.

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

## Zusätzliche Ressourcen

Weitere Informationen zur Funktion „Optimieren in Edge&quot; finden Sie in der folgenden Wiedergabeliste [LLM Optimizer - Optimieren in Edge](https://www.youtube.com/playlist?list=PLzbVcr6JHocVSMWBCaCw4xxjQ_VFVvFh0).

## Häufig gestellte Fragen

F: Können Kundschaften der Testversion „Optimize at Edge“ ausprobieren?

Ja, Kundschaften der Testversion können auf eine Optimierungsmöglichkeit zugreifen und diese für bis zu 10 Seiten bereitstellen. Standardmäßig handelt es sich um die Möglichkeit „Content-Sichtbarkeit wiederherstellen“, die AI Agents den Zugriff auf die Komplettversion Ihrer Seiteninhalte ermöglicht.

F. Welche Arten von LLMs werden mit „Optimize at Edge“ angesprochen?

Die Liste der anzusprechenden Benutzer-Agents definieren Sie im Rahmen des Onboardings.

<!--
Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.
-->

F. Was passiert, wenn mein Onboarding für „Optimize at Edge“ noch nicht erfolgt ist?

Wenn Sie auf **Optimierungen bereitstellen** klicken, bevor Sie die erforderliche Einrichtung abgeschlossen haben, werden keinerlei Änderungen auf Ihre Site angewendet. Stattdessen werden Sie in einem Popup-Dialogfeld aufgefordert, sich unter `llmo-at-edge@adobe.com` an unser Team zu wenden, um Unterstützung beim Onboarding zu erhalten. Bis zum Abschluss des Onboardings können Sie weiter die erkannten Möglichkeiten und Vorschläge erkunden, der Bereitstellungs-Workflow mit einem Klick bleibt jedoch inaktiv.

F: Was passiert, wenn der Inhalt an der Quelle aktualisiert wird?

Wir bedienen die optimierte Version Ihrer Seite aus dem Cache, solange sich die zugrunde liegende Quellseite nicht geändert hat. Wenn sich die Quelle jedoch für **Content-Sichtbarkeit wiederherstellen** ändert, wird unser System automatisch aktualisiert, sodass KI-Agenten immer die aktuellsten Inhalte erhalten. Dies liegt daran, dass wir niedrige TTL-Einstellungen (Cache Time To Live) verwenden (in der Reihenfolge von Minuten), sodass jedes Inhaltsupdate auf Ihrer Site eine neue Optimierung innerhalb dieses Triggers ermöglicht. Bei Inhaltsmöglichkeiten wie **LLM-freundliche Zusammenfassungen hinzufügen** überwacht LLM Optimizer die Quellseite auf Änderungen. Wenn eine Änderung erkannt wird, pausieren wir die Optimierung und markieren sie für eine menschliche Überprüfung, um zu verhindern, dass der Inhalt zwischen der für den Agenten sichtbaren Seite und der für den Menschen sichtbaren Seite verschoben wird.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

F. Ist „Optimize at Edge“ nur für Sites gedacht, die Adobe Edge Delivery Service (EDS) verwenden?

Nein. „Optimize at Edge“ ist CDN-unabhängig und funktioniert mit jeder Frontend-Architektur, nicht nur mit der, die im EDS-Stack von Adobe bereitgestellt wird.

F. Wie unterscheidet sich das Vorab-Rendering bei „Optimize at Edge“ vom herkömmlichen Server-seitigen Rendering (SSR)?

Beide lösen unterschiedliche Probleme und können zusammenarbeiten. Herkömmliches SSR rendert Server-seitige Inhalte, schließt jedoch keine Inhalte ein, die später im Browser geladen werden. Das Vorab-Rendering von „Optimize at Edge“ erfasst die Seite nach dem Laden von JavaScript- und Client-seitigen Daten und erzeugt die vollständig aufgebaute Version am CDN-Edge. SSR konzentriert sich auf die Verbesserung des menschlichen Erlebnisses, „Optimize at Edge“ verbessert das Web-Erlebnis für LLMs.

F. Ist Recover Content-Sichtbarkeit (d. h. Pre-Rendering) Cloaking? Es klingt so, als würde eine andere Version der Seite KI-Agenten bereitgestellt.

Nein. Pre-Rendering stellt sicher, dass KI-Agenten denselben Inhalt sehen können, den menschliche Besucher und SEO-Bots bereits sehen. Viele Websites laden aussagekräftige Inhalte mit JavaScript, die von typischen KI-Agenten nicht ausgeführt werden, sodass Agenten große Teile der Seite übersehen können. Beim Pre-Rendering wird ein statischer Snapshot erstellt, der den Volltext erfasst, sodass Agenten dieselben Informationen wie Menschen und Suchmaschinen erhalten. Es **die** von Inhalten für LLMs wieder her. Faktische Inhalte werden nicht hinzugefügt oder geändert.

F. Was ist mit anderen Inhaltsmöglichkeiten, wie z. B. „LLM-freundliche Zusammenfassungen hinzufügen“, bei denen eine neue Kopie auf der den Agenten bereitgestellten Seite erscheint? Ist das Tarnung?

Nein. Optimize at Edge führt keine Informationen ein, auf die menschliche Benutzende und SEO-Crawler nicht zugreifen können. Der Service organisiert oder fasst Inhalte, die bereits auf der Seite vorhanden sind, neu zusammen, damit KI-Agenten sie leichter interpretieren können. Wenn jemand einem Link von einer KI-Antwort auf Ihre Website folgt, kann er immer noch die gleichen zugrunde liegenden Informationen auf der Live-Seite finden.

F. Was passiert, wenn ich Optimierungen für einige, aber nicht für alle URLs in meiner Domain bereitstelle?

Nur die URLs, die Sie explizit optimieren, werden geändert. Für URLs mit bereitgestellten Möglichkeiten erhalten AI Agents die optimierte Version. Für URLs ohne bereitgestellte Möglichkeiten leitet unser Service die Originalseite einfach unverändert weiter, ohne Änderungen anzuwenden oder sie auf unserer Optimierungs-Cache-Ebene zu speichern. Dadurch wird sichergestellt, dass Sie Optimierungen selektiv bereitstellen können, ohne dass sich dies auf den Rest Ihrer Site auswirkt.
