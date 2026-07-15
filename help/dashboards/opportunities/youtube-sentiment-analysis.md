---
title: YouTube-Sentiment-Analyse
description: Erfahren Sie, wie LLM Optimizer YouTube-Videos analysiert, um Empfehlungen zu generieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in KI-Suchergebnissen verbessern.
feature: Opportunities
autotag-review: '2026-07-15T18:00:20.630Z'
TQID: 'https://experienceleague.adobe.com/qWlMzK13noSQULxakuUKHlDGZ-307yJjGJ4vsru2W6M'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1255
ht-degree: 100%

---


# YouTube-Sentiment-Analyse

YouTube ist eine der einflussreichsten Plattformen zur Prägung der Wahrnehmung von Privatkundschaften und des Rufs von Marken. Wenn KI-Systeme auf Prompts zu Ihrer Marke reagieren, greifen sie immer häufiger auf YouTube-Videos als Quellen zurück, sodass die Art und Weise, wie Ihre Marke in diesen Inhalten thematisiert wird, direkte Auswirkungen auf die KI-generierten Antworten hat.

Die Möglichkeit „YouTube-Sentiment-Analyse“ ist verfügbar, wenn YouTube-Videos als Zitierquelle für die Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt wurden. Diese zitierten Videos und ihre Kommentare werden hinsichtlich Sentiment, Share of Voice und wiederkehrenden Themen analysiert. Anschließend werden priorisierte Empfehlungen angezeigt, um die Wahrnehmung und Darstellung Ihrer Marke in KI-generierten Antworten zu verbessern.

Ihre Marke wird hinsichtlich sechs Dimensionen analysiert:

- **Analysierte Videos**: Anzahl der auf Markenerwähnungen und Sentiment untersuchten YouTube-Videos.
- **Analysierte Kommentare**: Anzahl der untersuchten Kommentare der analysierten Videos.
- **Markenerwähnungen (Videos)**: Wie häufig Ihre Marke in Videoinhalten erwähnt wird.
- **Markenerwähnungen (Kommentare)**: Wie häufig Ihre Marke in Kommentaren erwähnt wird.
- **Allgemeines Sentiment (Videos)**: Das allgemeine Sentiment zu Ihrer Marke im gesamten Videoinhalt.
- **Gesamt-Sentiment (Kommentare)**: Das allgemeine Sentiment zu Ihrer Marke in allen Kommentaren.

>[!NOTE]
>Die YouTube-Sentiment-Analyse befindet sich derzeit in der Beta-Phase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionalität ändern.

![Dashboard der YouTube-Sentiment-Analyse](/help/dashboards/opportunities/assets/youtube-sentiment-overview.png)

## Funktionsweise

LLM Optimizer überwacht YouTube-Videos, die von KI-Systemen für Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ zitiert werden. Wenn zitierte Videos erkannt werden, werden diese Videos und ihre Kommentare hinsichtlich Markenerwähnungen, Sentiment, Share of Voice und KI-Zitierungen analysiert. Die Leistung Ihrer Marke wird mit der der Konkurrenz am Markt und der zugehörigen Marken verglichen, wiederkehrende Themen mit Auswirkungen auf das Sentiment werden ermittelt und Empfehlungen zum Schließen von Wahrnehmungslücken werden generiert.

Wenn für die Prompts in Ihrem Prompt-Set keine YouTube-Videos zitiert werden, wird diese Möglichkeit nicht auf Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Diese Registerkarte enthält Empfehlungen zur Verbesserung der Wahrnehmung Ihrer Marke auf YouTube. Die Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Korrigierte Vorschläge** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/youtube-sentiment-suggestions.png)

Die Tabelle mit Vorschlägen enthält die folgenden Spalten:

- **Vorschlag**: Die empfohlene Verbesserung zur Schließung einer Wahrnehmungslücke.
- **Priorität**: Dringlichkeitsgrad (Kritisch, Hoch, Mittel, Niedrig).
- **Aktionselemente**: Öffnet ein Panel mit konkreten Schritten zur Umsetzung der Empfehlung, einschließlich der verantwortlichen Teams (z. B. Inhaltsstrategie, Influencer-Marketing, Produkt-Marketing).
- **Nachweis**: Öffnet die Tabelle „Quellen“ mit den Videos, auf denen der Vorschlag basiert.

Wenn Sie einen Vorschlag erweitern, wird der Abschnitt **KI-Analyse** mit folgenden Informationen angezeigt:

- **Warum dies verbessert werden muss**: Eine Erklärung der festgestellten Wahrnehmungslücke, einschließlich des Wettbewerbskontextes und der Art und Weise, wie das Problem in den YouTube-Inhalten entsteht.
- **Verbesserungsmöglichkeiten**: Konkrete Anleitungen für Inhalte oder Aktionen zum Schließen der Lücke.
- **Erwartetes Ergebnis**: Das erwartete Ergebnis der Umsetzung der Empfehlung.

Die Tabelle **Quellen** zeigt die YouTube-Videos an, auf denen der Vorschlag basiert, und enthält die folgenden Spalten:

- **Video**: Titel des YouTube-Videos und Link dorthin.
- **Kanal**: Der YouTube-Kanal, auf dem das Video veröffentlicht wurde.
- **Interaktion**: Interaktionsstufe (niedrig, mittel, hoch).
- **Markenerwähnungen**: Anzahl der Erwähnungen Ihrer Marke im Vergleich zur Gesamtanzahl der Erwähnungen im Video.
- **Share of Voice**: Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle erwähnten Marken.
- **Die fünf besten Marken**: Die am häufigsten erwähnten Marken im Video.
- **Sentiment**: Gesamt-Sentiment zu Ihrer Marke im Video.
- **KI-Zitierungen**: Anzahl der KI-Antworten, die dieses Video zitierten.

## Leistung

Die Registerkarte **Leistung** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke in YouTube-Inhalten. Sie ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und der Konkurrenz am Markt auf der Grundlage von Erwähnungen.

![Marktsituation](/help/dashboards/opportunities/assets/youtube-sentiment-market-landscape.png)

Folgendes wird angezeigt:

- **Markenerwähnungen in Videos**: Ihr Share of Voice im Vergleich zu zugehörigen Marken und der Konkurrenz am Markt.
- **Markenerwähnungen in Kommentaren**: Gleicher Vergleich in Kommentarinhalten.
- **Markt-Tracking**: Ein filterbares Diagramm, in dem Sie bis zu fünf Marken der Konkurrenz auswählen können, um Share of Voice über Videos und Kommentare hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung in allen analysierten Inhalten mit einem Diagramm der **Sentiment-Verteilung**, das die prozentuale Aufschlüsselung des günstigen, neutralen und ungünstigen Sentiments sowohl für Videos als auch Kommentare anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/youtube-sentiment-distribution.png)

### Videos

Eine detaillierte Tabelle der analysierten YouTube-Videos mit den folgenden Spalten:

- **Video**: Titel des YouTube-Videos und Link dorthin.
- **Kanal**: Der YouTube-Kanal, auf dem das Video veröffentlicht wurde.
- **Interaktion**: Interaktionsstufe (niedrig, mittel, hoch).
- **Markenerwähnungen**: Anzahl der Erwähnungen Ihrer Marke im Vergleich zur Gesamtanzahl der Erwähnungen im Video.
- **Share of Voice**: Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle erwähnten Marken.
- **Die fünf besten Marken**: Die am häufigsten erwähnten Marken im Video.
- **Sentiment**: Gesamt-Sentiment zu Ihrer Marke im Video.
- **KI-Zitierungen**: Anzahl der KI-Zitiersignale, die mit dem Video zusammenhängen.

Auf der Registerkarte „Leistung“ werden die Panels **Videos** und **Themen** in einer gemeinsamen Ansicht angezeigt (**Videos** ist ausgewählt). Die folgende Abbildung enthält die Tabelle auf Videoebene und darunter die Zusammenfassung **Themen**.

![Tabellen „Videos“ und „Themen“ auf der Registerkarte „Leistung“](/help/dashboards/opportunities/assets/youtube-sentiment-videos.png)

### Kommentare

Eine detaillierte Tabelle mit analysierten YouTube-Kommentaren, die die gleichen Spalten wie die Tabelle „Videos“ enthält, gefiltert nach Daten auf Kommentarebene.

### Themen

Eine Tabelle mit wiederkehrenden, in analysierten Inhalten identifizierten Themen, die Folgendes zeigt:

- **Thema**: Das wiederkehrende oder identifizierte Thema.
- **Markenerwähnungen**: Anzahl der mit dem Thema verknüpften Markenerwähnungen.
- **Sentiment**: Gesamt-Sentiment zu dem Thema.

Die Tabelle **Themen** wird in der gleichen Leistungsansicht wie die Tabelle „Videos“ angezeigt; siehe Abbildung im Abschnitt [Videos](#videos) oben.

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „YouTube-Sentiment-Analyse“ in der Frescopa-Demoumgebung aus.

[„YouTube-Sentiment-Analyse“ in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/youtube-analysis/971280f5-6a07-4506-85bf-d7419dca9803?siteId=frescopa-demo)

## Häufig gestellte Fragen

**Warum ist YouTube für die KI-Suche wichtig?**

KI-Systeme greifen bei der Generierung von Antworten zu Marken, Produkten und Themen zunehmend auf YouTube-Videos zurück. Wenn Ihre Marke in den zitierten Videos ungünstig oder falsch dargestellt wird, hat dieses Sentiment direkte Auswirkungen auf die Art und Weise, wie KI-Systeme Ihre Marke präsentieren. Eine der direktesten Möglichkeiten, die von KI-Systemen generierte Markenwahrnehmung zu beeinflussen, besteht darin, die Art und Weise zu verbessern, wie Ihre Marke in bereits von KI-Systemen zitierten YouTube-Inhalten erwähnt wird.

**Warum wird diese Möglichkeit nicht in meinem Dashboard angezeigt?**

Diese Möglichkeit ist nur verfügbar, wenn YouTube-Videos als Zitierquelle für die Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt wurden. Wenn für diese Prompts keine YouTube-Videos zitiert wurden, wird die Möglichkeit nicht angezeigt. Wenn mehr YouTube-Inhalte zu Ihrer Marke erstellt und diese Videos von KI-Systemen für Ihr Prompt-Set zitiert werden, wird die Möglichkeit zur Verfügung gestellt.

**Was bedeutet „Gesamt-Sentiment“?**

Das Gesamt-Sentiment spiegelt den allgemeinen Ton des Inhalts wieder, in dem Ihre Marke erwähnt wird: günstig, neutral oder ungünstig. Dies wird für Videos und Kommentare separat ermittelt, da diese erheblich voneinander abweichen können.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an der Gesamtanzahl der Markenerwähnungen in einem bestimmten Inhalt oder im gesamten analysierten Inhalt im Verhältnis zu allen anderen erwähnten Marken.

**Was sind KI-Zitierungen?**

KI-Zitierungen zeigen, wie viele KI-Antworten ein bestimmtes Video zitierten. Höhere KI-Zitierungszahlen zeigen an, dass das Video von KI-Systemen aktiv verwendet wird, wenn Antworten zu verwandten Themen generiert werden. Das bedeutet, dass das Sentiment in diesen Videos für die KI-Darstellung Ihrer Marke besonders wichtig ist.

**Wie wird die Konkurrenz am Markt identifiziert?**

Die Konkurrenz wird automatisch anhand der Branche Ihrer Marke und der in den analysierten Inhalten am häufigsten erwähnten Marken identifiziert. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Markt-Tracking-Diagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die YouTube-Analyse berücksichtigt die Inhalte, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum analysiert wurden. Kehren Sie nach Umsetzung der Empfehlungen zur Möglichkeit zurück, um Änderungen beim Sentiment und Share of Voice nachzuverfolgen.
