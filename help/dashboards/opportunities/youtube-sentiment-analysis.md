---
title: YouTube Sentiment Analysis
description: Erfahren Sie, wie LLM Optimizer YouTube-Videos und -Kommentare analysiert, um Empfehlungen zu präsentieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in den KI-Suchen verbessern.
feature: Opportunities
source-git-commit: 91fcd44f97e996fa7eb712928aba5dda250ea55b
workflow-type: tm+mt
source-wordcount: '1255'
ht-degree: 1%

---


# YouTube Sentiment Analysis

YouTube ist eine der einflussreichsten Plattformen, die die Verbraucherwahrnehmung und Markenreputation prägen. Wenn KI-Systeme auf Eingabeaufforderungen zu Ihrer Marke reagieren, zitieren sie zunehmend YouTube-Videos als Quellen, was die Art und Weise, wie Ihre Marke in diesen Inhalten diskutiert wird, zu einer direkten Eingabe in KI-generierte Antworten macht.

Die YouTube Sentiment-Analyse-Opportunity wird angezeigt, wenn YouTube-Videos als Zitate für Eingabeaufforderungen in der Eingabeaufforderung im Markenpräsenz-Dashboard erkannt werden. Es analysiert die zitierten Videos und ihre Kommentare für Sentiment, Share of Voice und wiederkehrende Themen. Anschließend werden priorisierte Empfehlungen angezeigt, um zu verbessern, wie Ihre Marke in KI-generierten Antworten wahrgenommen und dargestellt wird.

Es analysiert Ihre Marke in sechs Dimensionen:

- **Analysierte Videos** - Anzahl der auf Markenerwähnung und Sentiment hin untersuchten YouTube-Videos.
- **Analysierte Kommentare** - Anzahl der Kommentare, die in analysierten Videos untersucht werden.
- **Markenerwähnung (Videos)** - Wie oft Ihre Marke in Videoinhalten erwähnt wird.
- **Markenerwähnung (Kommentare)** - Wie oft Ihre Marke in Kommentaren erwähnt wird.
- **Gesamt-Sentiment (Videos)** - Zusammengefasstes Sentiment für Ihre Marke über Videoinhalte hinweg.
- **Gesamt-Sentiment (Kommentare)** - Zusammengefasstes Sentiment für Ihre Marke über Kommentare hinweg.

>[!NOTE]
>YouTube Sentiment Analysis befindet sich derzeit in der Betaphase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionen ändern.

![YouTube Sentiment Analysis Dashboard](/help/dashboards/opportunities/assets/youtube-sentiment-overview.png)

## Funktionsweise

LLM Optimizer überwacht von KI-Systemen zitierte YouTube-Videos auf Eingabeaufforderungen in der Eingabeaufforderung für das Markenpräsenz-Dashboard. Wenn zitierte Videos erkannt werden, werden diese Videos und ihre Kommentare auf Markenerwähnung-, Sentiment-, Share of Voice- und KI-Zitate analysiert. Es vergleicht die Performance Ihrer Marke mit der der Konkurrenz am Markt und den entsprechenden Marken, identifiziert wiederkehrende Themen, die das Sentiment fördern, und generiert Empfehlungen, um Wahrnehmungslücken zu schließen.

Wenn für die Eingabeaufforderungen in Ihrem Eingabeaufforderungssatz keine YouTube-Videos angegeben werden, wird diese Opportunity nicht in Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Auf dieser Registerkarte finden Sie Empfehlungen zur Verbesserung der Wahrnehmung Ihrer Marke in YouTube. Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/youtube-sentiment-suggestions.png)

Die Tabelle Vorschläge enthält die folgenden Spalten:

- **Vorschlag** - Die empfohlene Verbesserung, um eine Wahrnehmungslücke zu schließen.
- **Priorität** — Dringlichkeitsstufe (kritisch, hoch, Medium, niedrig).
- **Aktionselemente** - Öffnet ein Bedienfeld mit spezifischen Schritten zur Implementierung der Empfehlung, einschließlich der verantwortlichen Teams (z. B. Inhaltsstrategie, Influencer-Marketing, Produkt-Marketing).
- **Beweis** - Öffnet eine Quellentabelle mit den Videos, die dem Vorschlag zugrunde liegen.

Wenn Sie einen Vorschlag erweitern, wird ein Abschnitt **KI-Analyse** mit folgenden Inhalten angezeigt:

- **Warum dies verbessert werden muss** - Eine Erläuterung der festgestellten Wahrnehmungslücke, einschließlich des Wettbewerbskontexts und der Art und Weise, wie sich das Problem in allen YouTube-Inhalten bildet.
- **Verbessern** - Spezifische Anleitungen dazu, welche Inhalte oder Aktionen die Lücke schließen würden.
- **Erwartetes Ergebnis** — Das erwartete Ergebnis der Umsetzung der Empfehlung.

Die **Quellen**-Tabelle zeigt die YouTube-Videos, die den Vorschlag unterstützen, mit den folgenden Spalten:

- **Video** - Titel und Link zum YouTube-Video.
- **channel** - Der YouTube-Kanal, der das Video veröffentlicht hat.
- **Interaktion** - Interaktionsstufe (niedrig, Medium, hoch).
- **Markenerwähnung** - Anzahl der Markenerwähnung im Vergleich zur Gesamtzahl der Erwähnungen im Video.
- **Share of Voice** - Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle genannten Marken.
- **Top 5 Marken** - Die am häufigsten erwähnten Marken im Video.
- **Sentiment** - Im Video sehen Sie eine allgemeine Sentiment zu Ihrer Marke.
- **AI Citations** - Anzahl der AI-Antworten, die auf dieses Video verwiesen wurden.

## Leistung

Die **Performance** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke in allen YouTube-Inhalten. Es ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und Wettbewerbern auf der Grundlage von Erwähnungen.

![Marktlandschaft](/help/dashboards/opportunities/assets/youtube-sentiment-market-landscape.png)

Es zeigt:

- **Markenerwähnung in Videos** - Ihr Share of Voice im Vergleich zu zugehörigen Marken und Marktkonkurrenten.
- **Markenerwähnung in Kommentaren** - Gleicher Vergleich über Kommentarinhalte hinweg.
- **Market Tracking** - Ein filterbares Diagramm, in dem Sie bis zu fünf Marken von Mitbewerbern auswählen können, um Share of Voice über Videos und Kommentare hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung über alle analysierten Inhalte hinweg mit einem **Sentiment-Verteilungsdiagramm** das die prozentuale Aufschlüsselung der günstigen, neutralen und ungünstigen Sentiment für Videos und Kommentare anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/youtube-sentiment-distribution.png)

### Videos

Eine detaillierte Tabelle der analysierten YouTube-Videos mit den folgenden Spalten:

- **Video** - Titel und Link zum YouTube-Video.
- **channel** - Der YouTube-Kanal, der das Video veröffentlicht hat.
- **Interaktion** - Interaktionsstufe (niedrig, Medium, hoch).
- **Markenerwähnung** - Anzahl der Markenerwähnung im Vergleich zur Gesamtzahl der Erwähnungen im Video.
- **Share of Voice** - Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle genannten Marken.
- **Top 5 Marken** - Die am häufigsten erwähnten Marken im Video.
- **Sentiment** - Im Video sehen Sie eine allgemeine Sentiment zu Ihrer Marke.
- **AI-Zitate** - Anzahl der mit dem Video verknüpften KI-Zitationssignale.

Auf der Registerkarte Leistung werden die **Videos** und **Themen** in einer Ansicht angezeigt (mit **Videos** ausgewählt). Die folgende Abbildung enthält die Tabelle auf Videoebene und darunter die Zusammenfassung **Themen**.

![Videos und Themen auf der Registerkarte „Leistung“](/help/dashboards/opportunities/assets/youtube-sentiment-videos.png)

### Kommentare

Eine detaillierte Tabelle analysierter YouTube-Kommentare mit denselben Spalten wie die Videotabelle, gefiltert nach Daten auf Kommentarebene.

### Themen

Eine Tabelle mit wiederkehrenden Themen, die in analysierten Inhalten identifiziert werden und Folgendes zeigen:

- **Thema** - Das wiederkehrende Design oder Thema identifiziert.
- **Markenerwähnung** — Anzahl der mit dem Thema verknüpften Markenerwähnung.
- **Sentiment** - Das gesamte mit dem Thema verknüpfte Sentiment.

Die **Themen**-Tabelle wird in derselben Leistungsansicht wie die Videotabelle angezeigt. Weitere Informationen finden Sie in der Abbildung [&#x200B; Abschnitt &#x200B;](#videos)Videos“ weiter oben.

## In der Demo ausprobieren

Sehen Sie sich die YouTube Sentiment Analysis Opportunity in Aktion an, indem Sie die Demo-Umgebung von Frescopa verwenden.

[YouTube Sentiment Analysis in der Frescopa-Demo anzeigen](https://play.llmo.now/org/demo-org/opportunities/youtube-analysis/971280f5-6a07-4506-85bf-d7419dca9803?siteId=frescopa-demo)

## Häufig gestellte Fragen

**Warum ist YouTube wichtig für die KI-Suche?**

KI-Systeme zitieren zunehmend YouTube-Videos, wenn sie Antworten zu Marken, Produkten und Themen generieren. Wenn diese zitierten Videos Ihre Marke ungünstig oder ungenau diskutieren, fließt diese Sentiment direkt in die Darstellung Ihrer Marke durch KI-Systeme ein. Die Verbesserung der Art und Weise, wie Ihre Marke in YouTube-Inhalten diskutiert wird, die KI-Systeme bereits zitieren, ist eine der direktesten Möglichkeiten, die KI-generierte Markenwahrnehmung zu beeinflussen.

**Warum wird diese Opportunity nicht in meinem Dashboard angezeigt?**

Diese Opportunity wird nur angezeigt, wenn YouTube-Videos als Zitate für Eingabeaufforderungen in der Eingabeaufforderung im Markenpräsenz-Dashboard erkannt werden. Wenn für diese Eingabeaufforderungen keine YouTube-Videos zitiert werden, wird die Opportunity nicht angezeigt. Je mehr YouTube von Ihrer Marke abgedeckt wird und diese Videos von KI-Systemen für Ihr Eingabeaufforderungsset zitiert werden, desto mehr Möglichkeiten stehen zur Verfügung.

**Was bedeutet Sentiment insgesamt?**

Insgesamt spiegelt Sentiment den aggregierten Ton des Inhalts wider, in dem Ihre Marke erwähnt wird: günstig, neutral oder ungünstig. Er wird für Videos und Kommentare separat berechnet, da diese erheblich voneinander abweichen können.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an den gesamten Markenerwähnung innerhalb eines bestimmten Inhalts oder über alle analysierten Inhalte hinweg im Verhältnis zu allen anderen erwähnten Marken.

**Was sind KI-Zitate?**

KI-Zitate zeigen, wie viele KI-Antworten ein bestimmtes Video zitiert haben. Höhere KI-Zitationszahlen zeigen an, dass das Video aktiv von KI-Systemen verwendet wird, wenn Antworten zu verwandten Themen generiert werden - was den Sentiment in diesen Videos für die KI-Darstellung Ihrer Marke besonders wichtig macht.

**Wie werden die Wettbewerber auf dem Markt identifiziert?**

Mitbewerber werden automatisch anhand der Branche Ihrer Marke und der Marken identifiziert, die im analysierten Inhalt am häufigsten erwähnt werden. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Marktverfolgungsdiagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die YouTube-Analyse spiegelt die Inhalte wider, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum analysiert wurden. Sehen Sie sich die Opportunity erneut an, nachdem Sie Empfehlungen zur Nachverfolgung von Änderungen beim Sentiment und Share of Voice implementiert haben.
