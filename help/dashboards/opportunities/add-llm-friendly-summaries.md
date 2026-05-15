---
title: LLM-freundliche Zusammenfassungen hinzufügen
description: Erfahren Sie, wie LLM Optimizer Seiten mit hohem Traffic identifiziert, denen kurze Zusammenfassungen und Schlüsselpunkte für KI-Agenten fehlen, und wie Sie diese mit Optimize bei Edge überprüfen und bereitstellen können.
feature: Opportunities
autotag-review: '2026-05-15T17:27:51.631Z'
TQID: 'https://experienceleague.adobe.com/QpBdx3B-qg41ZWtPU2R4CNq-POrSs31UIb0kms1H3GU'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 793
ht-degree: 0%

---


# LLM-freundliche Zusammenfassungen hinzufügen

Die Opportunity „LLM-freundliche Zusammenfassungen hinzufügen“ identifiziert Seiten mit hohem Traffic, denen es an prägnanten strukturierten Zusammenfassungen mangelt, was es KI-Agenten erschwert, wichtige Informationen auf der Seite schnell zu verstehen. Sie bietet klare Zusammenfassungen und wichtige Punkte, die auf Ihrem vorhandenen Seiteninhalt basieren. Auf diese Weise können Agenten wichtige Markenansprüche effizienter interpretieren und erfassen und die Wahrscheinlichkeit erhöhen, dass Ihre Inhalte genau in KI-Antworten enthalten sind.

Für jede betroffene URL können Sie KI-generierte Vorschläge überprüfen und dann mit [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) bereitstellen, sodass der Agentendatenverkehr klarer und überschaubarer wird, ohne dass Änderungen am Content Management System (CMS) erforderlich sind.

## So wird das Problem behoben

Fehlerbehebungen werden mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) angewendet, die:

- Bereitstellung eines vorab gerenderten HTML-Snapshots für KI-Agenten.
- Reiht die Seite mit Zusammenfassungen und/oder wichtigen Punkten in der abgerufenen HTML an.
- Funktioniert auf CDN-Ebene (keine CMS-Änderungen).
- Ist nur KI - keine Auswirkungen auf menschliche Besucher oder SEO-Bots.
- Wird innerhalb von Minuten bereitgestellt und kann **der Benutzeroberfläche** LLM Optimizer vollständig rückgängig gemacht werden.

## Funktionsweise

LLM Optimizer kennzeichnet Seiten mit hohem Traffic, auf denen Seiten- oder **(Zusammenfassungen** und **Schlüsselpunkte** das Verständnis von KI erleichtern. Betroffene URLs werden in der Tabelle **URLs mit Vorschlägen** auf der Registerkarte **Aktuelle**&quot; angezeigt, wo Sie eine Zeile erweitern können, um jede Empfehlung zu überprüfen.

![URLs mit Vorschlägen zu aktuellen Vorschlägen, erweiterte Zeile mit Seiten- und Abschnittsübersichtsvorschlägen](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-expand.png)

Die Tabelle **URLs mit Vorschlägen** listet Seiten auf, auf denen Zusammenfassungen die Erkennung durch Agenten erleichtern würden. Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile** um die Analyse und den vorgeschlagenen Zusammenfassungstext (und ggf. die wichtigsten Punkte) anzuzeigen.
- **Vorschau** des Vorher-Nachher-Vergleichs für agenten Traffic.
- **Als behoben markieren** wenn Sie die Opportunity außerhalb von LLM Optimizer angesprochen haben.
- **Ignorieren** nicht relevante Vorschläge.

Jeder erweiterte Eintrag zeigt zusammenfassende Anweisungen auf Seiten- und Abschnittsebene, **KI-generierte** Kopien, Bearbeitungssteuerelemente und mit der Live-Seite verknüpften Kontext an.

Klicken Sie **Vorschau** in der Spalte **Aktionen**, um die Optimierungsvorschau zu öffnen. Dabei wird verglichen, wie Ihre Seite jetzt nach agentem Traffic aussieht, und zwar mit der Ansicht nach der Optimierung (z. B. eingefügte **Zusammenfassung** und **Schlüsselpunkt**-Inhalte, die an den vorgeschlagenen Platzierungen ausgerichtet sind). Sie können diese Vorschau jederzeit vor der Bereitstellung öffnen oder schließen.

Wenn Sie zur Veröffentlichung bereit sind, aktivieren Sie die Kontrollkästchen für die Zusammenfassung und die wichtigsten Punktzeilenelemente. Die Fußzeile zeigt an, wie viele ausgewählt sind, und bietet **Als behoben markieren**, **Vorschläge ignorieren** und **Optimierungen bereitstellen**.

![Aktuelle Vorschläge mit ausgewählten Übersichtszeilenelementen und Bereitstellungsoptimierungen in der Fußzeile](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-url.png)

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, klicken Sie auf **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die ausgewählten URLs und Optimierungsdetails aufgelistet. Überprüfen Sie die Liste und wählen Sie **Bereitstellen** oder **Abbrechen**.

![Dialogfeld „Für Edge bereitstellen“](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-dialog.png)

Nach erfolgreicher Bereitstellung bestätigt **Bereitstellung abgeschlossen** wie viele Optimierungen aktiviert wurden, und stellt fest, dass es möglicherweise einige Zeit dauern kann, bis KI-Agenten die Aktualisierung indizieren. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

![Bestätigung des Bereitstellungsabschlusses](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-confirm.png)

>[!NOTE]
>
>Für die Bereitstellung der Optimierungen muss der Onboarding-Prozess „Optimieren bei Edge&quot; abgeschlossen werden. Wenn Sie noch nicht eingestiegen sind, werden Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess weitergeleitet. Ausführliche Informationen zur Funktionsweise von „Optimieren bei Edge&quot;, zu unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um bereitgestellte Übersichtskopien und Anweisungen zu überprüfen.

![Registerkarte „Behobene Vorschläge“ mit dem Status „Optimiert“, erweiterten bereitgestellten Zusammenfassungen, „Live anzeigen“ und „Details“](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-fixed.png)

Klicken Sie in **Zeile auf** Live anzeigen“, um eine schreibgeschützte Ansicht des **aktuellen Seiteninhalts** zu öffnen, der zur Überprüfung bereitgestellt wird (einschließlich eingefügter **Zusammenfassung** und **Schlüsselpunkt**-Blöcke, falls angewendet). Verwenden Sie **Details** für die Analyse. Wenn Sie Edge-Änderungen stapelweise rückgängig machen müssen, wählen Sie die optimierten Zeilen mithilfe der Kontrollkästchen aus und verwenden Sie dann **Rollback** in der Kopfzeile.

![Es wurden Vorschläge mit Kontrollkästchen für die Massenauswahl vor dem Rollback korrigiert](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-in-fixed.png)

## Rollback

Wenn Sie es sich anders überlegen, können Sie jede bereitgestellte Optimierung zurücksetzen. Wählen Sie in **Ansicht** Feste Vorschläge“ die optimierten Zeilen aus, die Sie zurücksetzen möchten, und klicken Sie dann auf **Rollback** in der Kopfzeile.

Im Dialogfeld **Rollback** werden die Vorschläge aufgelistet, für die ein Rollback durchgeführt wird, mit einer kurzen Warnung, dass bereitgestellte Optimierungen zurückgesetzt werden. Bestätigen Sie die Liste und klicken Sie dann auf **Rollback** oder **Abbrechen**.

![Dialogfeld „Rollback“ mit Vorschlägen zum Zurücksetzen](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-dialog.png)

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.

![Rollback abgeschlossen - Rollback erfolgreich durchgeführt](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-confirm.png)

## In der Demo ausprobieren

Erkunden Sie den Workflow „LLM-freundliche Zusammenfassungen hinzufügen“ in der [Frescopa-Demo](https://play.llmo.now/org/demo-org).
