---
title: Relevante häufig gestellte Fragen hinzufügen
description: Erfahren Sie, wie LLM Optimizer Seiten mit hohem Traffic identifiziert, denen strukturierte Q&A-Inhalte für KI-Agenten fehlen, und wie Sie mit KI-generierte FAQs zu Optimize bei Edge überprüfen und bereitstellen können.
feature: Opportunities
autotag-review: '2026-05-15T17:28:53.611Z'
TQID: 'https://experienceleague.adobe.com/491jK6SRnc2yJ4Uw9UzK71W3nsTWDhxt3lW0Sy8-3NQ'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 742
ht-degree: 1%

---


# Relevante häufig gestellte Fragen hinzufügen

Die Gelegenheit „Relevante FAQ hinzufügen“ identifiziert Seiten mit hohem Traffic, denen strukturierte Q&amp;A-Inhalte fehlen, auf die KI-Agenten bei der Generierung von Antworten häufig angewiesen sind. Es werden relevante, **häufig gestellte Fragen (Intent-Alignment** vorgestellt, die auf vorhandenem Seitenmaterial basieren. Auf diese Weise können Agenten Benutzerfragen direkter mit Ihren Inhalten abgleichen.

Für jede betroffene URL können Sie KI-generierte FAQ-Vorschläge überprüfen und dann mit [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) bereitstellen, sodass der Agent-Traffic einen klareren Q&amp;A-Kontext erhält, ohne dass Änderungen am Content Management System (CMS) erforderlich sind.

## So wird das Problem behoben

Fehlerbehebungen werden mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) angewendet, die:

- Bereitstellung eines vorab gerenderten HTML-Snapshots für KI-Agenten.
- Reiht die Seite mit FAQ-Inhalten in der abgerufenen HTML an.
- Funktioniert auf CDN-Ebene (keine CMS-Änderungen).
- Ist nur KI - keine Auswirkungen auf menschliche Besucher oder SEO-Bots.
- Wird innerhalb von Minuten bereitgestellt und kann **der Benutzeroberfläche** LLM Optimizer vollständig rückgängig gemacht werden.

## Funktionsweise

LLM Optimizer identifiziert Seiten mit hohem Traffic, auf denen Fragen und Antworten fehlen oder mager sind. Dies erfolgt anhand der Eingabeaufforderung Ihrer Marke. Betroffene URLs werden in der Tabelle **URLs mit Vorschlägen** auf der Registerkarte **Aktuelle**&quot; angezeigt, wo Sie eine Zeile erweitern können, um jede Empfehlung zu überprüfen.

![URLs mit Vorschlägen zu aktuellen Vorschlägen, erweiterte Zeile mit FAQ-Eingabeaufforderungen und KI-generierten Antworten](/help/dashboards/opportunities/assets/add-relevant-faqs-expand.png)

Die Tabelle **URLs mit**&quot; listet Seiten auf, auf denen häufig gestellte Fragen zur KI-gesteuerten Erkennung beitragen würden. Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile**, um den vorgeschlagenen FAQ-Inhalt für diese Seite anzuzeigen.
- **Vorschau** des Vorher-Nachher-Vergleichs für agenten Traffic.
- **Als behoben markieren** wenn Sie die Opportunity außerhalb von LLM Optimizer angesprochen haben.
- **Ignorieren** nicht relevante Vorschläge.

In jedem erweiterten Eintrag sind die mit **Seite verknüpften FAQ**, **KI-generierte** empfohlenen Antworten, kurzen **Begründungen** **Quellen** aufgeführt. Die Tabelle zeigt auch, wie viele FAQs pro URL und **Agent-Traffic (4 Wochen) vorgeschlagen werden** damit Sie Prioritäten setzen können.

Klicken Sie **Vorschau** auf eine Zeile, um die Optimierungsvorschau zu öffnen. Es wird verglichen, wie Ihre Seite jetzt nach agentem Traffic aussieht, mit der Ansicht nach der Optimierung (z. B. der neue **FAQs**-Block).

![Optimierungsvorschau beim Vergleich der aktuellen Agentenansicht mit der Agentenansicht nach der Optimierung mit häufig gestellten Fragen](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-01.png)

Wählen Sie die FAQ-Vorschläge, die Sie versenden möchten, mithilfe der Zeilenkontrollkästchen aus. Die Fußzeile zeigt an, wie viele ausgewählt sind, und bietet **Als behoben markieren**, **Vorschläge ignorieren** und **Optimierungen bereitstellen**.

![Ausgewählte FAQ-Vorschläge zu aktuellen Vorschlägen mit Bereitstellungsoptimierungen](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-02.png)

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, klicken Sie auf **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die URLs, Fragen und Antworten aufgelistet, die Sie per Push übertragen möchten. Überprüfen Sie die Liste und wählen Sie dann entweder **Bereitstellen** oder **Abbrechen**.

![Dialogfeld „Für Edge bereitstellen“](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-03.png)

Nach erfolgreicher Bereitstellung wird mit **Bereitstellung abgeschlossen** bestätigt, wie viele Optimierungen live gingen. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

![Bestätigung des Bereitstellungsabschlusses](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-04.png)

>[!NOTE]
>
>Für die Bereitstellung der Optimierungen muss der Onboarding-Prozess „Optimieren bei Edge&quot; abgeschlossen werden. Wenn Sie noch nicht eingestiegen sind, werden Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess weitergeleitet. Ausführliche Informationen zur Funktionsweise von „Optimieren bei Edge&quot;, zu unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um den Inhalt der häufig gestellten Fragen zu überprüfen, verwenden Sie **Details** für Analysen oder klicken Sie **Live anzeigen**, um eine schreibgeschützte Ansicht des **aktuellen Seiteninhalts** zu öffnen, der zur Überprüfung bereitgestellt wird (einschließlich des eingefügten Abschnitts **FAQs**).

![Es wurden Vorschläge mit dem Status „Optimiert“, „Live anzeigen“ und „Rollback“ korrigiert](/help/dashboards/opportunities/assets/add-relevant-faqs-fixed.png)

Das Fenster **Live anzeigen** zeigt die Seitenstruktur und die Kopie der häufig gestellten Fragen an, wie in dieser Prüfung dargestellt.

![Live anzeigen - aktueller Seiteninhalt einschließlich häufig gestellter Fragen](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-05.png)

## Rollback

Wenn Sie es sich anders überlegen, können Sie jede bereitgestellte Optimierung zurücksetzen. In der **Feste**&quot; können Sie die optimierten Zeilen auswählen, die Sie zurücksetzen möchten, und dann in der Kopfzeile auf **Rollback** klicken.

Im Dialogfeld **Rollback** werden die Vorschläge aufgelistet, für die ein Rollback durchgeführt wird, mit einer kurzen Warnung, dass bereitgestellte Optimierungen zurückgesetzt werden. Bestätigen Sie die Liste und klicken Sie dann auf **Rollback** oder **Abbrechen**.

![Dialogfeld „Rollback“ mit Vorschlägen zum Zurücksetzen](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-07.png)

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.

![Rollback abgeschlossen - Rollback erfolgreich durchgeführt](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-08.png)

## In der Demo ausprobieren

Erkunden Sie den Workflow zum Hinzufügen relevanter FAQs in der [Frescopa-Demo](https://play.llmo.now/org/demo-org).
