---
title: Reddit Sentiment Analysis
description: Erfahren Sie, wie LLM Optimizer Reddit-Threads analysiert, um Empfehlungen zu präsentieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in den KI-Suchen verbessern.
feature: Opportunities
autotag-review: '2026-05-15T17:56:59.489Z'
TQID: 'https://experienceleague.adobe.com/LRC3nhHrAZoODy4gfsZiR7gc0i8n-IYqvZFj1TAUxsQ'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1163
ht-degree: 1%

---


# Reddit Sentiment Analysis

Reddit ist eine wichtige Datenquelle für große Sprachmodelle. Wenn Anwender KI-Assistenten nach Ihrer Marke fragen, werden die Antworten durch das Reddit Content Sentiment beeinflusst. Die Art und Weise, wie Ihre Marke über Subreddits hinweg diskutiert wird, beeinflusst direkt, wie KI-Systeme sie verstehen und in generierten Antworten darstellen.

Die Reddit-Sentiment-Analyse-Opportunity wird angezeigt, wenn Reddit-Threads als Zitate für Eingabeaufforderungen in der Eingabeaufforderung im Markenpräsenz-Dashboard erkannt werden. Es analysiert diese Threads und ihre Kommentare für Sentiment, Share of Voice und wiederkehrende Themen. Anschließend werden priorisierte Empfehlungen präsentiert, um zu verbessern, wie Ihre Marke von KI-Systemen wahrgenommen und zitiert wird.

Es analysiert Ihre Marke in vier Dimensionen:

- **Analysierte Beiträge** — Anzahl der für Markenerwähnung und Sentiment geprüften Reddit-Beiträge.
- **Analysierte Kommentare** — Anzahl der Kommentare, die in analysierten Beiträgen geprüft wurden.
- **Markenerwähnung (Threads)** - Wie oft Ihre Marke in analysierten Threads erwähnt wird.
- **Gesamt-Sentiment (Threads)** - Aggregierte Sentiment zu Ihrer Marke über analysierte Threads hinweg.

>[!NOTE]
>Reddit Sentiment Analysis befindet sich derzeit in der Betaphase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionen ändern.

![Reddit Sentiment Analysis Dashboard](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Funktionsweise

LLM Optimizer überwacht die von KI-Systemen zitierten Reddit-Threads auf Eingabeaufforderungen in Ihrem Markenpräsenz-Dashboard-Eingabeaufforderungssatz. Wenn zitierte Threads erkannt werden, werden diese Threads und ihre Kommentare auf Markenerwähnung-, Sentiment-, Share of Voice- und AI-Zitate analysiert. Es vergleicht die Performance Ihrer Marke mit der der Konkurrenz auf dem Markt, identifiziert wiederkehrende Themen, die Sentiment fördern, und generiert Empfehlungen, um Wahrnehmungslücken zu schließen.

Wenn für die Eingabeaufforderungen in Ihrem Eingabeaufforderungssatz keine Reddit-Threads angegeben werden, wird diese Opportunity nicht in Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Auf dieser Registerkarte finden Sie Empfehlungen, wie Sie die Wahrnehmung Ihrer Marke auf Reddit verbessern können. Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

Die Tabelle Vorschläge enthält die folgenden Spalten:

- **Vorschlag** - Die empfohlene Verbesserung, um eine Wahrnehmungslücke zu schließen.
- **Priorität** — Dringlichkeitsstufe (kritisch, hoch, Medium, niedrig).
- **Aktionselemente** - Öffnet ein Bedienfeld mit spezifischen Schritten zur Implementierung der Empfehlung, einschließlich der verantwortlichen Teams (z. B. PR, Community-Management, Produkt-Marketing).
- **Beweis** — Öffnet eine Quellen-Tabelle, die die Reddit-Threads hinter dem Vorschlag anzeigt.

Wenn Sie einen Vorschlag erweitern, wird ein Abschnitt **KI-Analyse** mit folgenden Inhalten angezeigt:

- **Warum dies verbessert werden muss** - Eine Erklärung der festgestellten Wahrnehmungslücke, einschließlich des Wettbewerbskontexts und der Art und Weise, wie sich das Problem über Reddit-Threads hinweg ausbildet.
- **Verbessern** - Spezifische Anleitungen dazu, welche Inhalte oder Aktionen die Lücke schließen würden.
- **Erwartetes Ergebnis** — Das erwartete Ergebnis der Umsetzung der Empfehlung.

Die **Quellen**-Tabelle zeigt die Reddit-Threads, die den Vorschlag antreiben, mit den folgenden Spalten:

- **Thread** - Titel und Link zum Reddit-Thread.
- **Subreddit** - Der Subreddit, in dem der Thread veröffentlicht wurde.
- **Interaktion** - Interaktionsstufe (niedrig, Medium, hoch).
- **Markenerwähnung** - Anzahl der Markenerwähnung im Vergleich zur Gesamtzahl der Erwähnungen im Thread.
- **Share of Voice** - Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle genannten Marken.
- **Top 5 Marken** - Die am häufigsten erwähnten Marken im Thread.
- **Sentiment** - Sentiment in Richtung Ihrer Marke im Thread.
- **KI-Zitate** - Anzahl der KI-Antworten, die diesen Thread zitiert haben.

## Leistung

Die **Performance** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke in allen Reddit-Inhalten. Es ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und Mitbewerbern, die auf Erwähnungen in Threads basieren.

![Marktlandschaft](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Es zeigt:

- **Markenerwähnung in Threads** - Ihr Share of Voice im Vergleich zu zugehörigen Marken und Marktkonkurrenten.
- **Market Tracking** - Ein filterbares Diagramm, in dem Sie bis zu fünf Marken von Mitbewerbern auswählen können, um Share of Voice über Threads hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung über analysierte Threads hinweg mit einem **Sentiment-Verteilungsdiagramm** das die prozentuale Aufschlüsselung des günstigen, neutralen und ungünstigen Sentiment auf die Threads anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Threads

Eine detaillierte Tabelle der analysierten Reddit-Threads mit den folgenden Spalten:

- **Thread** - Titel und Link zum Reddit-Thread.
- **Subreddit** - Der Subreddit, in dem der Thread veröffentlicht wurde.
- **Interaktion** - Interaktionsstufe (niedrig, Medium, hoch).
- **Markenerwähnung** - Anzahl der Markenerwähnung im Vergleich zur Gesamtzahl der Erwähnungen im Thread.
- **Share of Voice** - Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle genannten Marken.
- **Top 5 Marken** - Die am häufigsten erwähnten Marken im Thread.
- **Sentiment** - Sentiment in Richtung Ihrer Marke im Thread.
- **KI-Zitate** - Anzahl der KI-Antworten, die diesen Thread zitiert haben.

### Themen

Eine Tabelle mit wiederkehrenden Themen, die in analysierten Threads identifiziert wurden und Folgendes zeigen:

- **Thema** - Das wiederkehrende Design oder Thema identifiziert.
- **Markenerwähnung** — Anzahl der mit dem Thema verknüpften Markenerwähnung.
- **Sentiment** - Das gesamte mit dem Thema verknüpfte Sentiment.

Wenn Sie **einem beliebigen** auf „Details“ klicken, wird ein Dropdown-Bedienfeld mit zwei Registerkarten geöffnet:

- **Analyse** - Eine Zusammenfassung, wie Ihre Marke über die mit diesem Thema verbundenen Threads hinweg diskutiert wird.
- **Sources** - Die spezifischen Reddit-Threads, die zum Sentiment-Signal des Themas beitragen.

## In der Demo ausprobieren

Sehen Sie sich die Reddit Sentiment Analysis Opportunity in Aktion an, indem Sie die Demo-Umgebung von Frescopa verwenden.

[Reddit Sentiment Analysis im Frescopa Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Häufig gestellte Fragen

**Warum ist Reddit für die KI-Suche wichtig?**

Reddit ist eine der am stärksten gewichteten Quellen für LLM-Schulungsdaten und Echtzeitabruf. Wenn KI-Systeme Antworten zu Marken, Produkten und Themen generieren, geben Reddit-Diskussionen häufig Aufschluss über den Ton, den Rahmen und die tatsächlichen Behauptungen in diesen Antworten. Eine Marke, die auf Reddit ungünstig oder ungenau diskutiert wird, wird wahrscheinlich eher in KI-generierten Antworten so dargestellt.

**Warum wird diese Opportunity nicht in meinem Dashboard angezeigt?**

Diese Opportunity wird nur angezeigt, wenn Reddit-Threads als Zitate für Eingabeaufforderungen im Markenpräsenz-Dashboard-Eingabeaufforderungssatz erkannt werden. Wenn für diese Eingabeaufforderungen keine Reddit-Threads zitiert werden, wird die Opportunity nicht angezeigt. Da Ihre Marke eine größere Abdeckung von Reddit erhält und diese Threads von KI-Systemen für Ihr Eingabeaufforderungsset zitiert werden, wird die Gelegenheit verfügbar.

**Was bedeutet Sentiment insgesamt?**

Insgesamt spiegelt Sentiment den aggregierten Ton der Threads wider, in denen Ihre Marke erwähnt wird: günstig, neutral oder ungünstig berechnet über alle analysierten Threads hinweg.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an den gesamten Markenerwähnung innerhalb eines bestimmten Threads oder über alle analysierten Threads hinweg im Vergleich zu allen anderen erwähnten Marken.

**Was sind KI-Zitate?**

KI-Zitate zeigen, wie viele KI-Antworten einen bestimmten Thread zitiert haben. Höhere KI-Zitationszahlen zeigen an, dass der Thread von KI-Systemen aktiv verwendet wird, wenn Antworten zu verwandten Themen generiert werden - was den Sentiment in diesen Threads besonders wichtig für die KI-Darstellung Ihrer Marke macht.

**Wie werden die Wettbewerber auf dem Markt identifiziert?**

Konkurrenten werden automatisch anhand der Branche Ihrer Marke und der Marken identifiziert, die in den analysierten Threads am häufigsten erwähnt werden. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Marktverfolgungsdiagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die Reddit-Analyse spiegelt die Inhalte wider, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum analysiert wurden. Sehen Sie sich die Opportunity erneut an, nachdem Sie Empfehlungen zur Nachverfolgung von Änderungen beim Sentiment und Share of Voice implementiert haben.
