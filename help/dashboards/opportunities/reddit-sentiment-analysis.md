---
title: Reddit-Sentiment-Analyse
description: Erfahren Sie, wie LLM Optimizer Reddit-Threads analysiert, um Empfehlungen zu generieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in KI-Suchergebnissen verbessern.
feature: Opportunities
autotag-review: '2026-07-15T18:05:47.495Z'
TQID: 'https://experienceleague.adobe.com/trt7J6hxXtRdGat8Ohhd32JkwwIAJ26G8M98pBrN1CY'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1163
ht-degree: 100%

---


# Reddit-Sentiment-Analyse

Reddit ist eine wichtige Datenquelle für Large Language Models. Wenn Benutzende KI-Assistenten über Ihre Marke befragen, werden die Antworten durch das Reddit-Inhalts-Sentiment beeinflusst. Wie über Ihre Marke in Subreddits diskutiert wird, beeinflusst direkt, wie KI-Systeme sie wahrnehmen und in den generierten Antworten präsentieren.

Die Möglichkeit „Reddit-Sentiment-Analyse“ ist verfügbar, wenn Reddit-Threads als Zitierquelle für die Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt wurden. Diese zitierten Threads und ihre Kommentare werden hinsichtlich Sentiment, Share of Voice und wiederkehrenden Themen analysiert. Anschließend zeigt die Möglichkeit priorisierte Empfehlungen an, um die Wahrnehmung und Zitierung Ihrer Marke von KI-Systemen zu verbessern.

Ihre Marke wird hinsichtlich vier Dimensionen analysiert:

- **Analysierte Beiträge**: Anzahl der Reddit-Beiträge, die auf Markenerwähnungen und Sentiment untersucht wurden.
- **Analysierte Kommentare**: Anzahl der untersuchten Kommentare der analysierten Beiträge.
- **Markenerwähnungen (Threads)**: Wie häufig Ihre Marke in den analysierten Threads erwähnt wird.
- **Gesamt-Sentiment (Threads)**: Das allgemeine Sentiment zu Ihrer Marke in den analysierten Threads.

>[!NOTE]
>Die Reddit-Sentiment-Analyse befindet sich derzeit in der Beta-Phase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionalität ändern.

![Dashboard der Reddit-Sentiment-Analyse](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Funktionsweise

LLM Optimizer überwacht Reddit-Threads, die von KI-Systemen für Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ zitiert werden. Wenn zitierte Threads erkannt werden, werden diese Threads und ihre Kommentare hinsichtlich Markenerwähnungen, Sentiment, Share of Voice und KI-Zitierungen analysiert. Die Leistung Ihrer Marke wird mit der der Konkurrenz am Markt verglichen, wiederkehrende Themen mit Auswirkungen auf das Sentiment werden ermittelt und Empfehlungen zum Schließen von Wahrnehmungslücken werden generiert.

Wenn für die Prompts in Ihrem Prompt-Set keine Reddit-Threads zitiert werden, wird diese Möglichkeit nicht auf Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Diese Registerkarte enthält Empfehlungen zur Verbesserung der Wahrnehmung Ihrer Marke auf Reddit. Die Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Korrigierte Vorschläge** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

Die Tabelle mit Vorschlägen enthält die folgenden Spalten:

- **Vorschlag**: Die empfohlene Verbesserung zur Schließung einer Wahrnehmungslücke.
- **Priorität**: Dringlichkeitsgrad (Kritisch, Hoch, Mittel, Niedrig).
- **Aktionselemente**: Öffnet ein Panel mit konkreten Schritten zur Umsetzung der Empfehlung, einschließlich der verantwortlichen Teams (z. B. PR, Community-Management, Produkt-Marketing).
- **Nachweis**: Öffnet die Tabelle „Quellen“ mit den Reddit-Threads, auf denen der Vorschlag basiert.

Wenn Sie einen Vorschlag erweitern, wird der Abschnitt **KI-Analyse** mit folgenden Informationen angezeigt:

- **Warum dies verbessert werden muss**: Eine Erklärung der festgestellten Wahrnehmungslücke, einschließlich des Wettbewerbskontextes und der Art und Weise, wie das Problem in den Reddit-Threads entsteht.
- **Verbesserungsmöglichkeiten**: Konkrete Anleitungen für Inhalte oder Aktionen zum Schließen der Lücke.
- **Erwartetes Ergebnis**: Das erwartete Ergebnis der Umsetzung der Empfehlung.

Die Tabelle **Quellen** zeigt die Reddit-Threads an, auf denen der Vorschlag basiert, und enthält die folgenden Spalten:

- **Thread**: Titel des Reddit-Threads und Link dorthin.
- **Subreddit**: Der Subreddit, in dem der Thread veröffentlicht wurde.
- **Interaktion**: Interaktionsstufe (niedrig, mittel, hoch).
- **Markenerwähnungen**: Anzahl der Erwähnungen Ihrer Marke im Vergleich zur Gesamtanzahl der Erwähnungen im Thread.
- **Share of Voice**: Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle erwähnten Marken.
- **Die fünf besten Marken**: Die am häufigsten erwähnten Marken im Thread.
- **Sentiment**: Gesamt-Sentiment zu Ihrer Marke im Thread.
- **KI-Zitierungen**: Anzahl der KI-Antworten, die diesen Thread zitierten.

## Leistung

Die Registerkarte **Leistung** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke in Reddit-Inhalten. Sie ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und der Konkurrenz am Markt auf der Grundlage von Erwähnungen in Threads.

![Marktsituation](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Folgendes wird angezeigt:

- **Markenerwähnungen in Threads**: Ihr Share of Voice im Vergleich zu zugehörigen Marken und der Konkurrenz am Markt.
- **Markt-Tracking**: Ein filterbares Diagramm, in dem Sie bis zu fünf Marken der Konkurrenz auswählen können, um Share of Voice über Threads hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung in allen analysierten Threads mit einem Diagramm der **Sentiment-Verteilung**, das die prozentuale Aufschlüsselung des günstigen, neutralen und ungünstigen Sentiments in allen Threads anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Threads

Eine detaillierte Tabelle der analysierten Reddit-Threads mit den folgenden Spalten:

- **Thread**: Titel des Reddit-Threads und Link dorthin.
- **Subreddit**: Der Subreddit, in dem der Thread veröffentlicht wurde.
- **Interaktion**: Interaktionsstufe (niedrig, mittel, hoch).
- **Markenerwähnungen**: Anzahl der Erwähnungen Ihrer Marke im Vergleich zur Gesamtanzahl der Erwähnungen im Thread.
- **Share of Voice**: Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle erwähnten Marken.
- **Die fünf besten Marken**: Die am häufigsten erwähnten Marken im Thread.
- **Sentiment**: Gesamt-Sentiment zu Ihrer Marke im Thread.
- **KI-Zitierungen**: Anzahl der KI-Antworten, die diesen Thread zitierten.

### Themen

Eine Tabelle mit wiederkehrenden, in analysierten Threads identifizierten Themen, die Folgendes zeigt:

- **Thema**: Das wiederkehrende oder identifizierte Thema.
- **Markenerwähnungen**: Anzahl der mit dem Thema verknüpften Markenerwähnungen.
- **Sentiment**: Gesamt-Sentiment zu dem Thema.

Durch Klicken auf **Details** bei einem beliebigen Thema wird ein Panel mit einem detaillierten Überblick auf zwei Registerkarten geöffnet:

- **Analyse**: Eine Zusammenfassung der Art und Weise, wie Ihre Marke in mit diesem Thema zusammenhängenden Threads dargestellt wird.
- **Quellen**: Die konkreten Reddit-Threads, die zum Sentiment-Signal des Themas beitragen.

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „Reddit-Sentiment-Analyse“ in der Frescopa-Demoumgebung aus.

[„Reddit-Sentiment-Analyse“ in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Häufig gestellte Fragen

**Warum ist Reddit für die KI-Suche wichtig?**

Reddit ist eine der am stärksten gewichteten Quellen für LLM-Trainings-Daten und Echtzeitabruf. Wenn KI-Systeme Antworten zu Marken, Produkten und Themen generieren, liefern Reddit-Diskussionen häufig Informationen zu Ton, Kontext und Tatsachenbehauptungen für diese Antworten. Eine Marke, die auf Reddit ungünstig oder falsch dargestellt wird, wird wahrscheinlich auch in KI-generierten Antworten so präsentiert.

**Warum wird diese Möglichkeit nicht in meinem Dashboard angezeigt?**

Diese Möglichkeit ist nur verfügbar, wenn Reddit-Threads als Zitierung für die Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt wurden. Wenn für diese Prompts keine Reddit-Threads zitiert wurden, wird die Möglichkeit nicht angezeigt. Wenn mehr Reddit-Inhalte zu Ihrer Marke erstellt und diese Threads von KI-Systemen für Ihr Prompt-Set zitiert werden, wird die Möglichkeit zur Verfügung gestellt.

**Was bedeutet „Gesamt-Sentiment“?**

Das Gesamt-Sentiment spiegelt den allgemeinen Ton der Threads wider, in denen Ihre Marke erwähnt wird: günstig, neutral oder ungünstig. Dabei werden alle analysierten Threads berücksichtigt.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an der Gesamtanzahl der Markenerwähnungen in einem bestimmten Thread oder in allen analysierten Threads im Verhältnis zu allen anderen erwähnten Marken.

**Was sind KI-Zitierungen?**

KI-Zitierungen zeigen, wie viele KI-Antworten einen bestimmten Thread zitierten. Höhere KI-Zitierungszahlen zeigen an, dass der Thread von KI-Systemen aktiv verwendet wird, wenn Antworten zu verwandten Themen generiert werden. Das bedeutet, dass das Sentiment in diesen Threads für die KI-Darstellung Ihrer Marke besonders wichtig ist.

**Wie wird die Konkurrenz am Markt identifiziert?**

Die Konkurrenz wird automatisch anhand der Branche Ihrer Marke und der in den analysierten Threads am häufigsten erwähnten Marken identifiziert. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Markt-Tracking-Diagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die Reddit-Analyse berücksichtigt die Inhalte, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum analysiert wurden. Kehren Sie nach Umsetzung der Empfehlungen zur Möglichkeit zurück, um Änderungen beim Sentiment und Share of Voice nachzuverfolgen.
