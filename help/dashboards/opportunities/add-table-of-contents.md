---
title: Inhaltsverzeichnis hinzufügen
description: Erfahren Sie, wie LLM Optimizer Seiten mit hohem Traffic identifiziert, denen eine klare Navigationsstruktur für KI-Agenten fehlt, und wie Sie mit Optimize ein Inhaltsverzeichnis unter Edge überprüfen und bereitstellen können.
feature: Opportunities
source-git-commit: 36a6836f86b6d31cc4bf4682e881bd127edf66e4
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Inhaltsverzeichnis hinzufügen

>[!NOTE]
>
> **EARLY ACCESS** - Diese Funktion ist im EARLY ACCESS-Modus verfügbar. Verfügbarkeit, Eignung und Teile des Workflows können sich mit zunehmender Reife der Funktion ändern. Wenden Sie sich an Ihr Adobe-Accountteam, wenn Sie Fragen zum Zugriff haben.

Die Gelegenheit zum Hinzufügen des Inhaltsverzeichnisses kennzeichnet Seiten mit hohem Traffic, denen ein klarer **Inhaltsverzeichnis** und ein Strukturleitfaden fehlen, was es KI-Agenten erschwert, die Seite zu analysieren und Benutzerabfragen den richtigen Abschnitten zuzuordnen. Es führt ein strukturiertes Inhaltsverzeichnis mit (**verknüpften Überschriften** ein, die die Hauptabschnitte der Seite widerspiegeln. Diese Struktur hilft Agenten dabei, relevante Passagen zuverlässiger zu extrahieren, zu kartieren und zu zitieren.

Für jede betroffene URL können Sie vorgeschlagene Inhaltsverzeichniseinträge überprüfen und dann mit [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) bereitstellen, sodass der Agentendatenverkehr einen klareren Navigationskontext erhält, ohne dass Änderungen am Content Management System (CMS) erforderlich sind.

## So wird das Problem behoben

Fehlerbehebungen werden mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) angewendet, die:

- Bereitstellung eines vorab gerenderten HTML-Snapshots für KI-Agenten.
- Fügt der Seite ein Inhaltsverzeichnis hinzu.
- Funktioniert auf CDN-Ebene (keine CMS-Änderungen).
- Ist nur KI - keine Auswirkungen auf menschliche Besucher oder SEO-Bots.
- Wird innerhalb von Minuten bereitgestellt und kann **der Benutzeroberfläche** LLM Optimizer vollständig rückgängig gemacht werden.

## Funktionsweise

LLM Optimizer identifiziert Seiten mit hohem Traffic, auf denen ein **Inhaltsverzeichnis** die Navigation von KI-Agenten durch Überschriften und Abschnitte verbessern würde. Für jede Seite basieren Vorschläge auf Überschriften, die sich bereits auf der Seite befinden, sodass das Inhaltsverzeichnis die Seitenstruktur widerspiegelt.

Betroffene URLs werden in der Tabelle **URLs mit Vorschlägen** auf der Registerkarte **Aktuelle**&quot; angezeigt.

Bei **Aktuelle**) haben Sie für jede URL folgende Möglichkeiten:

- **Erweitern Sie die**, um das vorgeschlagene Inhaltsverzeichnis zu überprüfen (analysiert aus auf der Seite angezeigten Überschriften und als verankerte Einträge präsentiert).
- **Vorschau** ein Vor- und Nachvergleich.
- **Als behoben markieren** wenn Sie die Opportunity außerhalb von LLM Optimizer angesprochen haben.
- **Ignorieren** nicht relevante Vorschläge.

Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt, was im Einklang mit anderen Opportunities von Edge optimieren steht.

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, wählen Sie die Inhaltsverzeichnisvorschläge aus, die Sie bereitstellen möchten. Die Fußzeile fasst zusammen, wie viele Elemente ausgewählt sind, und bietet normalerweise **Als Behoben kennzeichnen**, **Vorschläge ignorieren** und **Optimierungen bereitstellen**.

Klicken Sie **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die ausgewählten URLs und Optimierungsdetails aufgelistet. Überprüfen Sie die Liste und wählen Sie **Bereitstellen** oder **Abbrechen**.

Nach erfolgreicher Bereitstellung wird mit **Bereitstellung abgeschlossen** bestätigt, wie viele Optimierungen live gingen. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

>[!NOTE]
>
>Für die Bereitstellung der Optimierungen muss der Onboarding-Prozess „Optimieren bei Edge&quot; abgeschlossen werden. Wenn Sie noch nicht eingestiegen sind, werden Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess weitergeleitet. Ausführliche Informationen zur Funktionsweise von „Optimieren bei Edge&quot;, zu unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um das bereitgestellte Inhaltsverzeichnis zu überprüfen, verwenden Sie **Details** für Analysen, sofern verfügbar, oder klicken Sie **Live anzeigen**, um eine schreibgeschützte Ansicht des **aktuellen Seiteninhalts** zu öffnen, der zur Überprüfung bereitgestellt wird (einschließlich des eingefügten **Inhaltsverzeichnisses**).

Wenn Sie Edge-Änderungen stapelweise rückgängig machen müssen, wählen Sie die optimierten Zeilen mithilfe der Kontrollkästchen aus und verwenden Sie dann **Rollback** in der Kopfzeile.

## Rollback

Wenn Sie es sich anders überlegen, können Sie eine bereitgestellte Optimierung zurücksetzen. Wählen Sie in **Ansicht** Feste Vorschläge“ die optimierten Zeilen aus, die Sie zurücksetzen möchten, und klicken Sie dann auf **Rollback** in der Kopfzeile.

Im Dialogfeld **Rollback** werden die Vorschläge aufgelistet, für die ein Rollback durchgeführt wird, mit einer kurzen Warnung, dass bereitgestellte Optimierungen zurückgesetzt werden. Bestätigen Sie die Liste und klicken Sie dann auf **Rollback** oder **Abbrechen**.

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.
