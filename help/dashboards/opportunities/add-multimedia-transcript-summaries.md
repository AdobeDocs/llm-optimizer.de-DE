---
title: Hinzufügen von Multimedia-Transkriptzusammenfassungen
description: Erfahren Sie, wie LLM Optimizer Seiten identifiziert, auf denen wichtige Informationen ohne maschinenlesbaren Text in Videos eingebettet sind, und wie Sie mit Optimize bei Edge KI-generierte Transkriptzusammenfassungen überprüfen und bereitstellen können.
feature: Opportunities
autotag-review: '2026-07-15T16:47:13.112Z'
TQID: 'https://experienceleague.adobe.com/lsMTVS4cFaGnhZonULQE4MB31bMdkzxoKA62o4IBcz0'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 775
ht-degree: 9%

---


# Hinzufügen von Multimedia-Transkriptzusammenfassungen

>[!NOTE]
>
> **EARLY ACCESS** - Zusammenfassungen von Multimedia-Transkripten hinzufügen sind im EARLY ACCESS-Bereich verfügbar. Verfügbarkeit, Eignung und Teile des Workflows können sich mit zunehmender Reife der Funktion ändern. Wenden Sie sich an Ihr Adobe-Accountteam, wenn Sie Fragen zum Zugriff haben.

Die Gelegenheit „Zusammenfassungen von Multimedia-Transkripten hinzufügen“ identifiziert Seiten, auf denen wichtige Informationen in Videos oder anderen Medien ohne Transkripte oder kurze Textzusammenfassungen vorhanden sind, die KI-Agenten lesen können. Sie führt **KI-generierte Transkriptzusammenfassungen** ein, die auf dem Medien- und Seitenkontext basieren. Es hilft dabei, wichtige Markeninformationen wiederherzustellen, die andernfalls verpasst würden, indem es Multimedia-Inhalte für KI-Agenten verständlich macht.

Für jede betroffene URL können Sie die vorgeschlagenen Details **Content Patch**, **Implementierung** (z. B. den Ziel-CSS-Selektor und -Vorgang) und **Rationale** überprüfen und dann mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) bereitstellen, sodass der Agent-Traffic die angereicherte HTML erhält, ohne dass Änderungen am Content Management System (CMS) erforderlich sind.

## So wird das Problem behoben

Fehlerbehebungen werden mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) angewendet, die:

- Bereitstellung eines vorab gerenderten HTML-Snapshots für KI-Agenten.
- In wird die Seite mit dem Transkript-Zusammenfassungstext in der abgerufenen HTML angereichert (z. B. in der Nähe des entsprechenden Inline-Videos).
- Funktioniert auf CDN-Ebene (keine CMS-Änderungen).
- Ist nur KI - keine Auswirkungen auf menschliche Besucher oder SEO-Bots.
- Wird innerhalb von Minuten bereitgestellt und kann **der Benutzeroberfläche** LLM Optimizer vollständig rückgängig gemacht werden.

## Funktionsweise

LLM Optimizer kennzeichnet Seiten mit hohem Traffic, auf denen maschinenlesbarer Text für eingebettete Medien fehlt, basierend auf Ihrer Konfiguration und der Seitenstruktur. Betroffene URLs werden in der Tabelle **URLs mit Vorschlägen** auf der Registerkarte **Aktuelle**&quot; angezeigt, wo Sie eine Zeile erweitern können, um jeden **Inhaltspatch** zu untersuchen, wie er angewendet wird und warum er empfohlen wird.

Für jede Seite gibt es Folgendes:

**Multimedia-Zusammenfassung** - Strukturierte Zusammenfassungen, die aus Videoinhalten abgeleitet sind.
**Vorschau** - Vor und nach dem Seitenvergleich.

![URLs mit Vorschlägen zu aktuellen Vorschlägen, erweiterte Zeile mit Inhalts-Patch, Implementierungsdetails und Begründung](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-expand.png)

Die Tabelle **URLs mit Vorschlägen** listet Seiten auf, auf denen das Transkript oder der Zusammenfassungstext die Erkennung durch Agenten erleichtern würde. Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile** um den **Inhaltspatch**-Text, **Implementierungsdetails** (einschließlich des geplanten DOM-Vorgangs und der CSS-Auswahl) und **Begründung** für die Änderung anzuzeigen.
- **Vorschau** des Vorher-Nachher-Vergleichs für agenten Traffic.
- **Als behoben markieren** wenn Sie die Opportunity außerhalb von LLM Optimizer angesprochen haben.
- **Ignorieren** Sie nicht relevante Vorschläge.

Sie können den Patch-Text aus der Zeile bearbeiten, wenn er unterstützt wird (Bleistiftsymbol), und dann die Zeilen-Kontrollkästchen verwenden, um auszuwählen, was bereitgestellt werden soll. Die Fußzeile zeigt an, wie viele ausgewählt sind, und bietet **Als behoben markieren**, **Vorschläge ignorieren** und **Optimierungen bereitstellen**.

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, klicken Sie auf **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die URLs, Selektoren und Vorgänge aufgelistet, die Sie ausführen möchten. Überprüfen Sie die Liste und wählen Sie **Bereitstellen** oder **Abbrechen**.

![Dialogfeld „In Edge bereitstellen“ für Patches für zusammenfassenden Multimediainhalt von Transkripten](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-dialog.png)

Nach erfolgreicher Bereitstellung wird mit **Bereitstellung abgeschlossen** bestätigt, wie viele Optimierungen live gingen. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

![Bestätigung des Bereitstellungsabschlusses](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-confirm.png)

>[!NOTE]
>
> Das Bereitstellen von Optimierungen erfordert den Abschluss des Onboarding-Prozesses „Optimize at Edge“. Falls Sie das Onboarding noch nicht abgeschlossen haben, gelangen Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess. Ausführliche Informationen zur Funktionsweise von „Optimize at Edge“, zu den unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um die Live **Inhaltspatch**, **Implementierung** Details und **Begründung** zu überprüfen. Darüber hinaus können Sie **Details** für Analysen oder &quot;**anzeigen** verwenden, sofern verfügbar, um zu bestätigen, welchen Agent-Traffic erhält.

![Behobene Vorschläge mit optimiertem Status, erweitertem Inhaltspatch und Rollback](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-fixed.png)

Um ein Rollback in großen Mengen durchzuführen, wählen Sie die optimierten Zeilen mithilfe der Kontrollkästchen aus und verwenden Sie dann **Rollback** in der Kopfzeile.

![Es wurden Vorschläge korrigiert, bei denen Zeilen vor dem Rollback ausgewählt wurden](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-select-in-fixed.png)

## Rollback

Wenn Sie es sich anders überlegen, können Sie eine bereitgestellte Optimierung zurücksetzen. Wählen **unter &quot;** Vorschläge“ die Zeilen aus, die zurückgesetzt werden sollen, und klicken Sie dann auf **Rollback**.

Das **Rollback**-Dialogfeld listet die Vorschläge auf, die zurückgesetzt werden sollen, und warnt davor, dass bereitgestellte Optimierungen aus dem Live-Pfad für Agentendatenverkehr entfernt werden. Bestätigen Sie und klicken Sie dann auf **Rollback** oder **Abbrechen**.

![Dialogfeld „Rollback“ mit Vorschlägen zum Zurücksetzen](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-dialog.png)

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.

![Rollback abgeschlossen - Rollback erfolgreich durchgeführt](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-confirm.png)

## Ausprobieren in der Demo

Erkunden Sie den Workflow „Zusammenfassungen von Multimedia-Transkripten hinzufügen“ in der [Frescopa-Demo](https://play.llmo.now/org/demo-org).
