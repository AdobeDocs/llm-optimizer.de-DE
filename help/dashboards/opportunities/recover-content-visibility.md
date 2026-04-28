---
title: Inhaltssichtbarkeit wiederherstellen
description: Erfahren Sie, wie LLM Optimizer Seiten identifiziert, auf denen kritische Inhalte von KI-Agenten ausgeblendet werden, und wie Sie diese Sichtbarkeit mithilfe der Edge-basierten Optimierung wiederherstellen können.
feature: Opportunities
source-git-commit: fd3c1b5ab75b54a93be06460ba15b382e74d8e3a
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 1%

---


# Inhaltssichtbarkeit wiederherstellen

KI-Agenten können nur Inhalte zitieren, auf die sie zugreifen können. Wenn wichtige Inhalte auf Ihren Seiten hinter Client-seitigem Rendering und dynamischen Lasten (wie Produktbeschreibungen, Benutzerbewertungen, Rezepte und Kommentare) verborgen sind, verpassen KI-Agenten diese vollständig, sodass wertvolle Inhalte für die Systeme, die sie zitieren könnten, unsichtbar bleiben.

Die Content-Sichtbarkeit zum Wiederherstellen identifiziert Seiten auf Ihrer Site, auf denen diese Sichtbarkeitslücke besteht. Für jede betroffene Seite wird genau angezeigt, welche Inhalte in der KI-Agentenansicht fehlen, die Lücke wird hervorgehoben und Sie können Korrekturen ohne CMS-Änderungen oder ohne Beteiligung von Entwicklern vornehmen.

Es zeigt drei Schlüsselmetriken auf einen Blick:

- **URLs** - Anzahl der Content-Sichtbarkeiten, die mit einer Seitenlücke identifiziert wurden.
- **Geschätzter Inhaltsgewinn** - Der geschätzte Multiplikator des Inhalts, der durch Anwendung der Optimierung wiederhergestellt werden könnte.
- **Durchschn. Content-Sichtbarkeit** - Der durchschnittliche Prozentsatz der Inhalte, die derzeit für KI-Agenten auf den betroffenen Seiten sichtbar sind.

![Content-Sichtbarkeit-Dashboard wiederherstellen](/help/dashboards/opportunities/assets/recover-content-visibility-overview.png)

Eine Videoübersicht zu dieser Opportunity finden Sie unter [Content-Sichtbarkeit wiederherstellen](https://www.youtube.com/watch?v=BigPyJssFCw).

Diese Opportunity kann mithilfe von „Optimieren [ Edge&quot; optimiert ](/help/dashboards/optimize-at-edge/overview.md). Optimierungen werden ausschließlich an KI-Agenten bereitgestellt, ohne dass dies Auswirkungen auf menschliche Besucher hat (Bot-only-Bereitstellung). Optimierungen werden dann auf der CDN-Ebene angewendet, ohne dass CMS-Änderungen erforderlich sind, und können innerhalb von Minuten ohne Entwicklerinteraktion wirksam werden, was eine schnelle Bereitstellung mit geringem Risiko ermöglicht.

## Funktionsweise

LLM Optimizer analysiert Ihre Seiten, indem es vergleicht, auf was KI-Agenten zugreifen können, und was tatsächlich auf der Seite vorhanden ist. Seiten, die einen hohen Agent-Traffic erhalten, aber eine niedrige Content-Sichtbarkeit haben, werden in der **URLs mit** angezeigt, die nach dem Agent-Traffic-Volumen priorisiert sind.

Für jede betroffene URL bietet LLM Optimizer Folgendes:

- **KI-Analyse** - Eine Beschreibung dessen, welche Inhalte fehlen und warum sie für die LLM-Kompatibilität wichtig sind, zusammen mit einer Liste der Inhaltsreferenzen, die wiederhergestellt werden können
- **Content-Sichtbarkeit** - Der Prozentsatz des Inhalts, der derzeit für KI-Agenten auf dieser Seite sichtbar ist
- **Content Gain Ratio** - Der geschätzte Multiplikator des wiederherstellbaren Inhalts, wenn die Optimierung angewendet wird
- **Vorschau** - Ein direkter Vergleich von HTML, der zeigt, wie die Seite jetzt im Vergleich zur Nachoptimierung aussieht, sodass Sie die Änderung vor der Bereitstellung überprüfen können

Die Fehlerbehebung erfolgt mit [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) - der Edge-basierten Bereitstellungsfunktion von Adobe, die einen vollständig vorgerenderten, KI-freundlichen HTML-Schnappschuss für LLM-Benutzeragenten auf CDN-Ebene bereitstellt und zuvor ausgeblendete Inhalte wiederherstellt, ohne Ihre CMS zu berühren.

<!-- [URLs with suggestions](/help/dashboards/opportunities/assets/recover-content-visibility-urls.png)-->

## URLs mit Vorschlägen

Die Tabelle **URLs mit**&quot; listet alle betroffenen Seiten auf und kann nach Klassifizierung gefiltert werden. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile**, um die KI-Analyse anzuzeigen, einschließlich der fehlenden Inhalte und der Gründe, warum sie wichtig sind.
- **Vorschau** der parallele HTML-Vergleich der aktuellen Seite mit der Post-Optimierungsversion.
- **Als behoben markieren** sobald das Problem behoben wurde.
- **Ignorieren** nicht relevante Vorschläge.

Die Vorschläge sind in drei Ansichten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**. Sobald ein Vorschlag bereitgestellt wurde, wechselt er zu Feste Vorschläge mit dem Status **Optimiert** und zu einer **Live anzeigen**-Aktion, um zu überprüfen, ob die Optimierung für agenten Traffic live ist. Feste Vorschläge können auch jederzeit zurückgesetzt werden.

![Behobene Vorschläge mit dem Status Optimiert](/help/dashboards/opportunities/assets/recover-content-visibility-fixed.png)

## Bereitstellen der Optimierung

Nachdem Sie die Vorschläge geprüft und die zu optimierenden URLs ausgewählt haben, klicken Sie auf **Optimierungen bereitstellen**, um die Fehlerbehebung am CDN-Edge zu veröffentlichen. In **Bestätigungsdialogfeld „Für Edge bereitstellen** werden die ausgewählten URLs, ihr Typ (PreRender) und der angewendete Vorschlag angezeigt. Nach der Bereitstellung wird in einem Bestätigungsbildschirm bestätigt, welche URLs erfolgreich optimiert wurden.

>[!NOTE]
>
>Für die Bereitstellung der Optimierungen muss der Onboarding-Prozess „Optimieren bei Edge&quot; abgeschlossen werden. Wenn Sie noch nicht eingestiegen sind, werden Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess weitergeleitet. Ausführliche Informationen zur Funktionsweise von „Optimieren bei Edge&quot;, zu unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md).

![Dialogfeld „Für Edge bereitstellen“](/help/dashboards/opportunities/assets/recover-content-visibility-deploy.png)

## In der Demo ausprobieren

Erleben Sie die Möglichkeit, die Content-Sichtbarkeit mithilfe der Frescopa-Demoumgebung in Aktion wiederherzustellen.

[View Recover Content-Sichtbarkeit in der Frescopa Demo](https://play.llmo.now/org/demo-org/opportunities/prerender/75729489-756a-4c2b-9905-155b1715da5c)

## Häufig gestellte Fragen

**Warum ist mein Seiteninhalt vor KI-Agenten verborgen?**

Die meisten modernen Websites verlassen sich darauf, dass JavaScript Inhalte nach der ersten Seitenanforderung dynamisch lädt. KI-Agenten führen JavaScript normalerweise nicht aus, sodass Client-seitig gerenderte Inhalte - Produktlisten, Benutzerbewertungen, Blog-Artikel-Links und ähnliche Elemente - vom KI-Agenten nie gesehen werden, selbst wenn sie für menschliche Besucher vollständig sichtbar sind.

**Wirkt sich diese Optimierung auf meine menschlichen Besucher oder SEO-Bots aus?**

Nein. Bei Edge optimieren werden nur KI-Benutzeragenten berücksichtigt. Besuchende und SEO-Bots erhalten die Originalseite genau wie zuvor, ohne Änderungen an ihrem Erlebnis oder ihrer Leistung.

**Muss ich meine CMS ändern oder Entwickler einbeziehen?**

Nein. Die Optimierung wird am CDN-Edge angewendet und erfordert keine Änderungen am Authoring, Code-Bereitstellungen oder Entwicklerinteraktionen. Nach dem Onboarding von Optimizer bei Edge können Sie Änderungen in Minutenschnelle direkt über die LLM Optimizer-Benutzeroberfläche bereitstellen und zurücksetzen.

**Was passiert, wenn sich mein Seiteninhalt nach der Bereitstellung ändert?**

Für die Wiederherstellungs-Content-Sichtbarkeit verwendet LLM Optimizer TTL-Einstellungen mit geringem Cache, damit alle Inhaltsaktualisierungen auf Ihrer Site innerhalb von Minuten aktualisiert werden können. KI-Agenten erhalten immer die aktuellste Version Ihres Inhalts.

**Wie komme ich bei Edge zu Optimize?**

Auf der [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) Seite finden Sie den vollständigen Onboarding-Prozess, die CDN-Konfigurationshandbücher und die Voraussetzungen.
