---
title: Inhaltsverzeichnis hinzufügen
description: Erfahren Sie, wie LLM Optimizer Seiten mit hohem Traffic identifiziert, denen eine klare Navigationsstruktur für KI-Agenten fehlt, und wie Sie mit Optimize ein Inhaltsverzeichnis unter Edge überprüfen und bereitstellen können.
feature: Opportunities
autotag-review: '2026-07-15T16:47:42.882Z'
TQID: 'https://experienceleague.adobe.com/x-7FiZKCLMmEfm1x2lQNtfOd4su1MyGLrcAtLnjpaqw'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 655
ht-degree: 9%

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
- **Ignorieren** Sie nicht relevante Vorschläge.

Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt, was im Einklang mit anderen Opportunities von Edge optimieren steht.

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, wählen Sie die Inhaltsverzeichnisvorschläge aus, die Sie bereitstellen möchten. Die Fußzeile fasst zusammen, wie viele Elemente ausgewählt sind, und bietet normalerweise **Als Behoben kennzeichnen**, **Vorschläge ignorieren** und **Optimierungen bereitstellen**.

Klicken Sie **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die ausgewählten URLs und Optimierungsdetails aufgelistet. Überprüfen Sie die Liste und wählen Sie **Bereitstellen** oder **Abbrechen**.

Nach erfolgreicher Bereitstellung wird mit **Bereitstellung abgeschlossen** bestätigt, wie viele Optimierungen live gingen. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

>[!NOTE]
>
>Das Bereitstellen von Optimierungen erfordert den Abschluss des Onboarding-Prozesses „Optimize at Edge“. Falls Sie das Onboarding noch nicht abgeschlossen haben, gelangen Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess. Ausführliche Informationen zur Funktionsweise von „Optimize at Edge“, zu den unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um das bereitgestellte Inhaltsverzeichnis zu überprüfen, verwenden Sie **Details** für Analysen, sofern verfügbar, oder klicken Sie **Live anzeigen**, um eine schreibgeschützte Ansicht des **aktuellen Seiteninhalts** zu öffnen, der zur Überprüfung bereitgestellt wird (einschließlich des eingefügten **Inhaltsverzeichnisses**).

Wenn Sie Edge-Änderungen stapelweise rückgängig machen müssen, wählen Sie die optimierten Zeilen mithilfe der Kontrollkästchen aus und verwenden Sie dann **Rollback** in der Kopfzeile.

## Rollback

Wenn Sie es sich anders überlegen, können Sie eine bereitgestellte Optimierung zurücksetzen. Wählen Sie in **Ansicht** Feste Vorschläge“ die optimierten Zeilen aus, die Sie zurücksetzen möchten, und klicken Sie dann auf **Rollback** in der Kopfzeile.

Im Dialogfeld **Rollback** werden die Vorschläge aufgelistet, für die ein Rollback durchgeführt wird, mit einer kurzen Warnung, dass bereitgestellte Optimierungen zurückgesetzt werden. Bestätigen Sie die Liste und klicken Sie dann auf **Rollback** oder **Abbrechen**.

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.
