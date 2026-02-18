---
title: Optimize at Edge
description: Erfahren Sie, wie Sie in LLM Optimizer Optimierungen am CDN-Edge bereitstellen können, ohne dass Authoring-Änderungen erforderlich sind.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 85%

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

Um den Einrichtungsprozess zu leiten, wählen Sie unten Ihren CDN-Provider aus und folgen Sie dem entsprechenden Konfigurationshandbuch. Beachten Sie, dass diese Beispiele an Ihre tatsächliche Live-Konfiguration angepasst werden müssen. Wir empfehlen, Änderungen zuerst in den niedrigeren Umgebungen anzuwenden.

### CDN-Konfigurationshandbücher

| CDN-Anbieter | Typ | Handbuch |
|---|---|---|
| AEM Cloud Service Managed CDN (Fastly) | Von Adobe verwaltet | [Einrichtungshandbuch anzeigen](/help/dashboards/optimize-at-edge-aem-managed-cdn.md) |
| Fastly (BYOCDN) | Eigenes CDN einbringen | [Einrichtungshandbuch anzeigen](/help/dashboards/optimize-at-edge-fastly-byocdn.md) |
| Akamai (BYOCDN) | Eigenes CDN einbringen | [Einrichtungshandbuch anzeigen](/help/dashboards/optimize-at-edge-akamai-byocdn.md) |
| Cloudflare (BYOCDN) | Eigenes CDN einbringen | [Einrichtungshandbuch anzeigen](/help/dashboards/optimize-at-edge-cloudflare-byocdn.md) |

>[!NOTE]
>Wenn Ihr CDN-Anbieter oben nicht aufgeführt ist oder Sie Ihre Domain oder E-Mail in der LLM Optimizer-Benutzeroberfläche nicht finden, wenden Sie sich bitte an `llmo-at-edge@adobe.com`, um Unterstützung beim Onboarding zu erhalten. Sobald die Einrichtungskonfigurationen abgeschlossen sind, können Sie Empfehlungen für Möglichkeiten von „Optimize at Edge“ in LLM Optimizer bereitstellen.

Jedes der oben genannten CDN-Setup-Handbücher enthält detaillierte Überprüfungsschritte am Ende, um zu bestätigen, dass der Agent-Traffic korrekt weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

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

Mit einem einzigen Klick können Sie die Maschinenlesbarkeit jeder Site bewerten. Sie können direkt vergleichen, was AI Agents bzw. menschliche Benutzende sehen, und abschätzen, wie viel Inhalt mithilfe von LLM Optimizer sichtbar gemacht werden könnte. Auf der Seite [Kann KI Ihre Website lesen?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) finden Sie für weitere Informationen.

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
