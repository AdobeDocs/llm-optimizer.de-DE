---
title: Sentiment-Analyse von Zitierungen
description: Erfahren Sie, wie LLM Optimizer die am häufigsten zitierten URLs analysiert, um Empfehlungen zu generieren, die die Wahrnehmung und Sichtbarkeit Ihrer Marke in KI-Suchergebnissen verbessern.
feature: Opportunities
autotag-review: '2026-07-15T17:45:11.828Z'
TQID: 'https://experienceleague.adobe.com/B-gDBklZ7XjMCQx-HaYx8H8yr9eZbXBvuRTAUfqJ-QU'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ab7fdb62-bd53-4cfd-8c2c-169f7e47f20e
subfeature_v2: id: cd42f7fa-7c4e-41cf-ba86-6e0de16ed456
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1030
ht-degree: 100%

---


# Sentiment-Analyse von Zitierungen

Wenn KI-Systeme Fragen zu Ihrer Marke beantworten, greifen sie auf eine Reihe von häufig zitierten URLs zurück – Web-Seiten von Drittanbietern, auf die in KI-generierten Antworten häufig verwiesen wird. Wie Ihre Marke auf diesen Seiten dargestellt wird, beeinflusst direkt, wie KI-Systeme sie den Benutzenden präsentieren.

Die Möglichkeit „Sentiment-Analyse von Zitierungen“ analysiert die am häufigsten zitierten URLs, die für die Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt wurden. Es wertet Markenerwähnungen, Sentiment, Share of Voice und wiederkehrende Themen auf diesen Seiten aus. Anschließend werden priorisierte Empfehlungen angezeigt, um die Wahrnehmung Ihrer Marke in den Inhalten zu verbessern, auf die KI-Systeme am meisten zurückgreifen.

Es werden vier Schlüsselmetriken angezeigt:

- **Analysierte Seiten**: Anzahl der zitierten Web-Seiten, die auf Markenerwähnungen und Sentiment untersucht wurden.
- **Übersprungene Seiten**: Anzahl der Seiten, die nicht analysiert werden konnten (z. B. aufgrund von Zugriffsbeschränkungen).
- **Markenerwähnungen (Seiten)**: Wie häufig Ihre Marke auf den analysierten Seiten erwähnt wird.
- **Gesamt-Sentiment (Seiten)**: Das allgemeine Sentiment zu Ihrer Marke auf den analysierten Seiten.

>[!NOTE]
>Die Sentiment-Analyse von Zitierungen befindet sich derzeit in der Beta-Phase. Funktionen und Verfügbarkeit können sich im Zuge der Weiterentwicklung der Funktionalität ändern.

![Dashboard der Sentiment-Analyse von Zitierungen](/help/dashboards/opportunities/assets/cited-sentiment-overview.png)

## Funktionsweise

LLM Optimizer identifiziert die am häufigsten zitierten URLs, die in KI-generierten Antworten auf Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ erwähnt werden. Diese Seiten werden hinsichtlich Markenerwähnungen, Sentiment, Share of Voice und KI-Zitierungen analysiert. Die Leistung Ihrer Marke wird mit der der Konkurrenz am Markt verglichen, wiederkehrende Themen werden ermittelt und Empfehlungen zum Schließen von Wahrnehmungslücken auf den für KI-Systeme wichtigsten Seiten werden generiert.

Wenn für die Prompts in Ihrem Prompt-Set keine zitierten URLs gefunden werden, wird diese Möglichkeit nicht auf Ihrem Dashboard angezeigt.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **Vorschläge** und **Leistung**.

## Vorschläge

Diese Registerkarte enthält Empfehlungen zur Verbesserung der Markenwahrnehmung der am häufigsten zitierten URLs. Die Vorschläge sind in drei Unterregisterkarten unterteilt: **Aktuelle Vorschläge**, **Korrigierte Vorschläge** und **Ignorierte Vorschläge**.

![Registerkarte „Vorschläge“](/help/dashboards/opportunities/assets/cited-sentiment-suggestions.png)

Die Tabelle mit Vorschlägen enthält die folgenden Spalten:

- **Vorschlag**: Die empfohlene Verbesserung zur Schließung einer Wahrnehmungslücke.
- **Priorität**: Dringlichkeitsgrad (Kritisch, Hoch, Mittel, Niedrig).
- **Aktionselemente**: Öffnet ein Panel mit konkreten Schritten zur Umsetzung der Empfehlung, einschließlich der verantwortlichen Teams.

Wenn Sie einen Vorschlag erweitern, wird der Abschnitt **KI-Analyse** mit folgenden Informationen angezeigt:

- **Warum dies verbessert werden muss**: Eine Erklärung der festgestellten Wahrnehmungslücke, einschließlich der zitierten URLs, die Ihre Marke und den Wettbewerbskontext unterrepräsentieren.
- **Verbesserungsmöglichkeiten**: Konkrete Anleitungen für Kontaktaufnahme, Inhaltserstellung oder Partnerschaftsaktionen zum Schließen der Lücke.
- **Erwartetes Ergebnis**: Das erwartete Ergebnis der Umsetzung der Empfehlung.

## Leistung

Die Registerkarte **Leistung** bietet eine detaillierte Aufschlüsselung der Leistung Ihrer Marke auf den am häufigsten zitierten Seiten. Sie ist in vier Abschnitte unterteilt.

### Marktsituation

Vergleicht die Leistung Ihrer Marke mit zugehörigen Marken und der Konkurrenz am Markt auf der Grundlage von Erwähnungen auf allen zitierten Seiten.

![Marktsituation](/help/dashboards/opportunities/assets/cited-sentiment-landscape.png)

Folgendes wird angezeigt:

- **Markenerwähnungen auf Seiten**: Ihr Share of Voice im Vergleich zu zugehörigen Marken und der Konkurrenz am Markt.
- **Markt-Tracking**: Ein filterbares Diagramm, in dem Sie bis zu fünf Marken der Konkurrenz auswählen können, um Share of Voice über analysierte Seiten hinweg zu vergleichen.

### Sentiment-Analyse

Verfolgt die Markenwahrnehmung auf allen analysierten Seiten mit einem Diagramm der **Sentiment-Verteilung**, das die prozentuale Aufschlüsselung des günstigen, neutralen und ungünstigen Sentiments auf allen Seiten anzeigt.

![Sentiment-Analyse](/help/dashboards/opportunities/assets/cited-sentiment-distribution.png)

### Seiten

Eine detaillierte Tabelle der analysierten zitierten Web-Seiten mit den folgenden Spalten:

- **Seite**: URL der analysierten Seite.
- **Markenerwähnungen**: Anzahl der Erwähnungen Ihrer Marke im Vergleich zur Gesamtanzahl der Erwähnungen auf der Seite.
- **Share of Voice**: Der Anteil der Erwähnungen Ihrer Marke in Bezug auf alle erwähnten Marken.
- **Die fünf besten Marken**: Die am häufigsten erwähnten Marken auf der Seite.
- **Sentiment**: Gesamt-Sentiment zu Ihrer Marke auf der Seite.
- **KI-Zitierungen**: Anzahl der KI-Antworten, die diese Seite zitierten.

### Themen

Eine Tabelle mit wiederkehrenden, auf analysierten Seiten identifizierten Themen, die Folgendes zeigt:

- **Thema**: Das wiederkehrende oder identifizierte Thema.
- **Markenerwähnungen**: Anzahl der mit dem Thema verknüpften Markenerwähnungen.
- **Sentiment**: Gesamt-Sentiment zu dem Thema.

Durch Klicken auf **Details** auf einem beliebigen Thema wird ein detaillierter Überblick mit einer Zusammenfassung der Analyse und den beitragenden Quellseiten geöffnet.

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „Sentiment-Analyse von Zitierungen“ in der Frescopa-Demoumgebung aus. [„Sentiment-Analyse von Zitierungen“ in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/cited-analysis/d3a8b217-9f4c-4e88-a612-6b7f91e5c044?siteId=frescopa-demo).

## Häufig gestellte Fragen

**Warum sind die am häufigsten zitierten URLs für die KI-Suche wichtig?**

Die am häufigsten zitierten URLS sind die Drittanbieterseiten, auf die KI-Systeme beim Generieren von Antworten zur Ihrer Marke am häufigsten verweisen. Das Sentiment und Framing auf diesen Seiten haben einen direkten und übermäßig großen Einfluss darauf, wie KI Ihre Marke darstellt, und zwar mehr als Seiten, die selten zitiert werden. Das Verbessern der Darstellung Ihrer Marke auf diesen konkreten Seiten ist eine der Aktionen mit den größten Auswirkungen, die Sie für die KI-Sichtbarkeit ausführen können.

**Warum wird diese Möglichkeit nicht in meinem Dashboard angezeigt?**

Diese Möglichkeit wird nur angezeigt, wenn zitierte URLs für Prompts in Ihrem Prompt-Set im Dashboard „Markenpräsenz“ ermittelt werden. Wenn für diese Prompts keine zitierten URLs identifiziert wurden, wird die Möglichkeit nicht angezeigt.

**Was bedeutet „Übersprungene Seiten“?**

Übersprungene Seiten sind zitierte URLs, die nicht analysiert werden konnten. In der Regel ist dies der Fall, weil sich die Seite hinter einer Paywall befindet, eine Authentifizierung erfordert oder den automatischen Zugriff blockiert. Diese Seiten werden gezählt, aber von der Sentiment- und Markenerwähnungs-Analyse ausgeschlossen.

**Was ist Share of Voice?**

Share of Voice ist der prozentuale Anteil der Marke an der Gesamtanzahl der Markenerwähnungen auf einer bestimmten Seite oder auf allen analysierten Seiten im Verhältnis zu allen anderen erwähnten Marken.

**Was sind KI-Zitierungen?**

KI-Zitierungen zeigen, wie viele KI-Antworten eine bestimmte Seite zitierten. Höhere KI-Zitierungszahlen zeigen an, dass die Seite von KI-Systemen aktiv verwendet wird, wenn Antworten zu verwandten Themen generiert werden. Das bedeutet, dass das Sentiment auf diesen Seiten für die KI-Darstellung Ihrer Marke besonders wichtig ist.

**Wie wird die Konkurrenz am Markt identifiziert?**

Die Konkurrenz wird automatisch anhand der Branche Ihrer Marke und der auf den analysierten Seiten am häufigsten erwähnten Marken identifiziert. Sie können auch manuell bis zu fünf Marken auswählen, um sie im Markt-Tracking-Diagramm zu vergleichen.

**Wie oft wird die Analyse aktualisiert?**

Die Analyse berücksichtigt die zitierten URLs, die bis zu dem in der Dashboard-Kopfzeile angezeigten Datum ermittelt wurden. Kehren Sie nach Umsetzung der Empfehlungen zur Möglichkeit zurück, um Änderungen beim Sentiment und Share of Voice nachzuverfolgen.
