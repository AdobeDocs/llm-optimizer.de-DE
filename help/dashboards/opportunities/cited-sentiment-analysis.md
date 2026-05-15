---
title: Cited Sentiment Analysis
description: Erfahren Sie, wie LLM Optimizer die am häufigsten zitierten URLs analysiert, um Empfehlungen zu präsentieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in den KI-Suchen verbessern.
feature: Opportunities
autotag-review: '2026-05-15T17:39:50.086Z'
TQID: 'https://experienceleague.adobe.com/ZqgWup29QoQ-j0fDM6DqhGpzRqscg1f-fdXHTMN9fIk'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1030
ht-degree: 1%

---


# Cited Sentiment Analysis

Wenn KI-Systeme Fragen zu Ihrer Marke beantworten, nutzen sie eine Reihe häufig zitierter URLs - Web-Seiten von Drittanbietern, auf die in KI-generierten Antworten häufig verwiesen wird. Wie Ihre Marke auf diesen Seiten dargestellt wird, bestimmt direkt, wie KI-Systeme sie den Benutzern darstellen.

Die Sentiment-Analyse-Opportunity analysiert die am häufigsten zitierten URLs, die für Eingabeaufforderungen in Ihrem Markenpräsenz-Dashboard-Eingabeaufforderungssatz erkannt wurden. Es bewertet Markenerwähnung, Sentiment, Share of Voice und wiederkehrende Themen auf diesen Seiten. Anschließend werden priorisierte Empfehlungen angezeigt, um die Wahrnehmung Ihrer Marke in Bezug auf die Content-KI-Systeme zu verbessern, auf die sich die meisten verlassen.

Es zeigt vier Schlüsselmetriken:

- **Analysierte Seiten** — Anzahl der zitierten Webseiten, die auf Markenerwähnung und Sentiment untersucht wurden.
- **Übersprungene Seiten** - Anzahl der Seiten, die nicht analysiert werden konnten (z. B. aufgrund von Zugriffsbeschränkungen).
- **Markenerwähnung (Seiten)** - Wie oft Ihre Marke auf analysierten Seiten erwähnt wird.
- **Gesamt-Sentiment (Seiten)** - Zusammengefasstes Sentiment für Ihre Marke über analysierte Seiten hinweg.

>[!NOTE]
>Die zitierte Sentiment-Analyse befindet sich derzeit in der Betaphase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionen ändern.

![Cited Sentiment Analysis Dashboard](/help/dashboards/opportunities/assets/cited-sentiment-overview.png)

## Funktionsweise

LLM Optimizer identifiziert die am häufigsten zitierten URLs, die in KI-generierten Antworten für Eingabeaufforderungen in Ihrem Markenpräsenz-Dashboard-Eingabeaufforderungssatz angezeigt werden. Es analysiert diese Seiten für Markenerwähnung, Sentiment, Share of Voice und KI-Zitate. Es vergleicht die Leistung Ihrer Marke mit der der Konkurrenz auf dem Markt, identifiziert wiederkehrende Themen und generiert Empfehlungen, um Wahrnehmungslücken auf den Seiten zu schließen, die für KI-Systeme am wichtigsten sind.

Wenn für die Eingabeaufforderungen in Ihrem Eingabeaufforderungssatz keine angegebenen URLs erkannt werden, wird diese Opportunity nicht in Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Auf dieser Registerkarte finden Sie Empfehlungen, wie Sie die Wahrnehmung Ihrer Marke in Bezug auf die am häufigsten zitierten URLs verbessern können. Die Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/cited-sentiment-suggestions.png)

Die Tabelle Vorschläge enthält die folgenden Spalten:

- **Vorschlag** - Die empfohlene Verbesserung, um eine Wahrnehmungslücke zu schließen.
- **Priorität** — Dringlichkeitsstufe (kritisch, hoch, Medium, niedrig).
- **Aktionselemente** - Öffnet ein Bedienfeld mit spezifischen Schritten zur Implementierung der Empfehlung, einschließlich der verantwortlichen Teams.

Wenn Sie einen Vorschlag erweitern, wird ein Abschnitt **KI-Analyse** mit folgenden Inhalten angezeigt:

- **Warum dies verbessert werden muss** - Eine Erklärung der festgestellten Wahrnehmungslücke, einschließlich der zitierten URLs, die Ihre Marke und den Wettbewerbskontext unterrepräsentieren.
- **Verbessern** - Spezifische Leitlinien für Öffentlichkeitsarbeit, Inhaltserstellung oder Partnerschaftsaktionen, um die Lücke zu schließen.
- **Erwartetes Ergebnis** — Das erwartete Ergebnis der Umsetzung der Empfehlung.

## Leistung

Die **Performance** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke auf den am häufigsten zitierten Seiten. Es ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und Mitbewerbern auf der Grundlage von Erwähnungen auf allen zitierten Seiten.

![Marktlandschaft](/help/dashboards/opportunities/assets/cited-sentiment-landscape.png)

Es zeigt:

- **Markenerwähnung in Pages** - Ihr Share of Voice im Vergleich zu zugehörigen Marken und Wettbewerbern.
- **Market Tracking** - Ein filterbares Diagramm, in dem Sie bis zu fünf Marken von Mitbewerbern auswählen können, um Share of Voice über analysierte Seiten hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung auf allen analysierten Seiten mit einem **Sentiment-Verteilungsdiagramm** das die prozentuale Aufschlüsselung des günstigen, neutralen und ungünstigen Sentiment auf allen Seiten anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/cited-sentiment-distribution.png)

### Seiten

Eine detaillierte Tabelle der analysierten zitierten Web-Seiten mit den folgenden Spalten:

- **Seite** - URL der analysierten Seite.
- **Markenerwähnung** — Anzahl der Markenerwähnung im Vergleich zur Gesamtzahl der Erwähnungen auf der Seite.
- **Share of Voice** - Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle genannten Marken.
- **Top 5 Marken** - Die am häufigsten genannten Marken auf der Seite.
- **Sentiment** - Sentiment in Richtung Ihrer Marke auf der Seite.
- **AI-Zitate** - Anzahl der AI-Antworten, die auf diese Seite verwiesen wurden.

### Themen

Eine Tabelle mit wiederkehrenden Themen, die auf analysierten Seiten identifiziert wurden und Folgendes zeigen:

- **Thema** - Das wiederkehrende Design oder Thema identifiziert.
- **Markenerwähnung** — Anzahl der mit dem Thema verknüpften Markenerwähnung.
- **Sentiment** - Das gesamte mit dem Thema verknüpfte Sentiment.

Wenn Sie **Details** auf ein beliebiges Thema klicken, wird eine Drilldown-Liste mit einer Zusammenfassung der Analyse und den beitragenden Quellseiten geöffnet.

## In der Demo ausprobieren

Sehen Sie die zitierte Sentiment-Analyse-Opportunity in Aktion, indem Sie die Frescopa-Demoumgebung verwenden - [Anzeigen der zitierten Sentiment-Analyse in der Frescopa-](https://play.llmo.now/org/demo-org/opportunities/cited-analysis/d3a8b217-9f4c-4e88-a612-6b7f91e5c044?siteId=frescopa-demo).

## Häufig gestellte Fragen

**Warum sind die am häufigsten zitierten URLs für die KI-Suche wichtig?**

Die am häufigsten zitierten URLs sind die KI-Systeme von Drittanbieterseiten, die am häufigsten beim Generieren von Antworten über Ihre Marke referenziert werden. Die Sentiment und das Framing auf diesen Seiten haben einen direkten und übergroßen Einfluss darauf, wie KI Ihre Marke repräsentiert, mehr als Seiten, die selten zitiert werden. Die Verbesserung der Darstellung Ihrer Marke auf diesen spezifischen Seiten ist eine der Aktionen mit der höchsten Hebelwirkung, die Sie für die KI-Sichtbarkeit ausführen können.

**Warum wird diese Opportunity nicht in meinem Dashboard angezeigt?**

Diese Opportunity wird nur angezeigt, wenn zitierte URLs für Eingabeaufforderungen in der Eingabeaufforderung im Markenpräsenz-Dashboard erkannt werden. Wenn für diese Eingabeaufforderungen keine angegebenen URLs identifiziert wurden, wird die Opportunity nicht angezeigt.

**Was bedeutet das Überspringen von Seiten?**

Übersprungene Seiten sind zitierte URLs, die nicht analysiert werden konnten. In der Regel ist dies der Fall, weil sich die Seite hinter einer Paywall befindet, eine Authentifizierung erfordert oder den automatischen Zugriff blockiert. Diese Seiten werden gezählt, aber von der Sentiment- und Markenerwähnung-Analyse ausgeschlossen.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an den Markenerwähnung-Gesamtwerten einer bestimmten Seite oder aller analysierten Seiten im Verhältnis zu allen anderen erwähnten Marken.

**Was sind KI-Zitate?**

KI-Zitate zeigen, wie viele KI-Antworten auf einer bestimmten Seite zitiert wurden. Höhere KI-Zitationszahlen zeigen an, dass die Seite von KI-Systemen aktiv verwendet wird, wenn Antworten zu verwandten Themen generiert werden, wodurch der Sentiment auf diesen Seiten für die KI-Darstellung Ihrer Marke besonders wichtig ist.

**Wie werden die Wettbewerber auf dem Markt identifiziert?**

Wettbewerber werden automatisch anhand der Branche Ihrer Marke und der auf den analysierten Seiten am häufigsten genannten Marken identifiziert. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Marktverfolgungsdiagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die Analyse spiegelt die zitierten URLs wider, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum erkannt wurden. Sehen Sie sich die Opportunity erneut an, nachdem Sie Empfehlungen zur Nachverfolgung von Änderungen beim Sentiment und Share of Voice implementiert haben.
