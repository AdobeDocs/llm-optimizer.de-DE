---
title: Markenpräsenz
description: Erfahren Sie, wie Sie mit dem Markenpräsenz-Dashboard verstehen können, wie Ihre Marke auf der Ebene der KI-generierten Reaktionen wahrgenommen wird.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 1%

---


# Markenpräsenz {#brand-presence}

Das Markenpräsenz-Dashboard bietet einen detaillierten Überblick darüber, wie Ihre Marke auf der Ebene der KI-generierten Reaktionen wahrgenommen wird. Es zeigt an, wo, wie oft und in welchem Kontext Ihre Marke erwähnt wird. Sie können das Dashboard verwenden, um die Sichtbarkeit zu messen, Zitate zu verfolgen und Sentiment-Trends zu erkunden. Das Dashboard ist in mehrere Abschnitte unterteilt, die jeweils unterschiedliche Einblicke bieten. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Markenpräsenz](/help/dashboards/assets/brand-main.png)

Auf dieser Seite wird Folgendes beschrieben:

* [Filter](#filters)
* [Übersichtsmetriken](##key-metrics)
* [Vergleich von anderen](##others-comparison)
* [Sentiment-Trend](#sentiment-trend)
* [Datenerkenntnisse](#data-insights)

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
* **Kategorie** - Filtert die angezeigten Ergebnisse nach vordefinierten Kategorien oder benutzerdefinierten Kategorien.
* **Thema** - Filtern Sie nach Thema, um Inhaltsthemen und Themenbereiche zu analysieren, in denen Ihre Marke in KI-Antworten erscheint.
* **Platform** - Wählen Sie die zu analysierende KI-Engine aus. LLM Optimizer unterstützt derzeit ChatGPT, Google-KI-Übersichten, den Google-KI-Modus, den Microsoft-Co-Piloten, Google Gemini und Perplexity.
* **Prompts-Herkunft** - Wählen Sie den Ursprung der Prompts aus. Der Ursprung kann entweder vom Benutzer eingegeben oder per KI generiert werden.
* **Prompt-Branding** - Filtern Sie die Ergebnisse nach gebrandeten Eingabeaufforderungen oder nach nicht gebrandeten Eingabeaufforderungen.
* **Region** - Filtern der Ergebnisse nach Geografie. Nicht alle Regionen werden zum Start verfügbar sein.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Übersichtsmetriken {#overview-metrics}

Im Dashboard werden drei sehr wichtige Metriken oben auf der Seite hervorgehoben: Sichtbarkeitsbewertung, Erwähnungen und Zitate. Je niedriger die Anzahl für diese Metriken ist, desto schlechter wird Ihre Marke wahrgenommen, und Sie sollten handeln, um Ihren Markenpräsenz zu verbessern. Nachfolgend finden Sie eine kurze Beschreibung jeder Metrik und dessen, was sie darstellt.

![Übersichtsmetriken](/help/dashboards/assets/overview-metrics.png)

### Sichtbarkeitsbewertung {#visibility-score}

Die Sichtbarkeitsbewertung besteht aus Faktoren wie: Erwähnungen, Zitate, Sentiment und Rang. Jedem Faktor ist ein bestimmtes „Gewicht“ zugeordnet, das zum Endwert hinzuaddiert.

### Markenerwähnung {#mentions}

Diese Metrik stellt die Gesamtzahl der Male dar, in denen Ihre Marke oder Ihre Kategorien in den KI-Eingabeaufforderungen der Stichprobe erwähnt wurden. Wenn Sie beispielsweise die Marke „Coffe B“ mit den Kategorien „Maschinen“ und „Zubehör“ verwenden, zählt diese Metrik die Gesamtzahl der Fälle, in denen diese in den KI-Stichprobenantworten erscheinen.

### Zitierungen {#citations}

Diese Metrik gibt an, wie oft die Site als Quelle referenziert wurde.

Trendindikatoren für jede Schlüsselmetrik zeigen, wie sich diese Werte im Laufe der Zeit im Vergleich zum vorherigen Zeitraum ändern.

## Vergleich von anderen {#others-comparison}

Im Abschnitt Vergleich anderer Marken können Sie bis zu fünf andere Marken auswählen und ihre Erwähnungen und Zitate mit Ihrer Marke vergleichen. Auf diese Weise können Sie Ihre Leistung im Verhältnis zu anderen Marken anzeigen und bewerten.

![Sonstige - Vergleich](/help/dashboards/assets/other-comparison.png)

Die anderen Marken werden aus der Dropdown-Liste ausgewählt und die Diagramme werden aktualisiert, wenn Sie auf **Filter anwenden** klicken. Die Diagramme zeigen wöchentliche Markenerwähnung und wöchentliche Markennamen nebeneinander. Sie können auch den Mauszeiger über das Diagramm bewegen, um die Datenentwicklung über den wöchentlichen Zeitrahmen hinweg zu sehen.

## Sentiment-Trend-Analyse {#sentiment-trend}

Im Abschnitt Sentiment-Trend-Analyse können Sie verfolgen, wie Ihre Marke in den beprobten KI-Antworten wahrgenommen wird. Die Sentiment-Trend-Metrik kann entweder positiv, neutral oder negativ sein. Beispielsweise kann es positiv sein, wenn Antworten die Produktqualität hervorheben, oder negativ, wenn sie schlechten Service erwähnen. Das Trenddiagramm zeigt die Veränderungen der Markenwahrnehmung von Woche zu Woche. Dieser Abschnitt wird erst ausgefüllt, nachdem Ihre Marke erwähnt wurde.

![Sentiment-Trend ](/help/dashboards/assets/sentiment-trend.png)

## Data Insights und Share of Voice {#data-insights}

Abgerundet wird das Dashboard durch zwei wichtige Tabellen: Dateneinblicke und Share of Voice. Die Informationen in diesen Tabellen helfen Ihnen dabei zu erkennen, wo Ihre Marke stark ist und wo eine Optimierung erforderlich ist.

Mithilfe der Tabelle **Dateneinblicke** können Sie Themen und Benutzerfragen erkunden, um die Auswirkungen von Inhalten zu bewerten und zu optimieren. Die Ergebnisse werden nach Themen und Eingabeaufforderungen aufgeführt. In der **Share of Voice**-Tabelle wird Ihre Markensprache mit anderen Marken themenübergreifend verglichen. So können Sie Lücken identifizieren und zukünftige Themen priorisieren.

![Dateneinblicke](/help/dashboards/assets/data-insights.png)

Beide Tabellen verfügen über ein Suchfeld für den schnellen Zugriff auf Themen. Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabellen in das Reporting für Führungskräfte aufzunehmen.

Klicken Sie auf die Registerkarten unten, um Details zu jeder Tabelle und den zugehörigen Metriken anzuzeigen.

>[!BEGINTABS]

>[!TAB Dateneinblicke]

Die Tabelle „Dateneinblicke“ hilft Ihnen, Themen und Benutzeraufforderungen zu erkunden, um die Auswirkungen von Inhalten zu bewerten und zu optimieren. Angezeigt werden die folgenden Metriken:

* **Thema** - Die Themenkategorie stellt SEO-Schlüsselwörter und Benutzerfragen dar, die sich auf Ihre Marke beziehen. Sie können auf klicken, um die einzelnen Themen zu erweitern und die einzelnen Eingabeaufforderungen für das Markenpräsenz zu analysieren. Jedes Thema verfügt über eine Schaltfläche **Details**, wenn Sie mit der Maus darauf zeigen. Durch Klicken auf die Schaltfläche wird ein separates Fenster mit weiteren Details angezeigt.
* **Region** - zeigt die Region der Eingabeaufforderungen an.
* **Beliebtheit** - Die Beliebtheitskategorie gibt das Suchvolumen für dieses Thema in Bezug auf alle anderen Themen in der Analyse an. Der Wert kann entweder Hoch, Medium oder Niedrig sein.
* **Sichtbarkeitsbewertung** - Die Sichtbarkeitsbewertung für dieses Thema. Sie spiegelt gewichtete Faktoren wie Erwähnungen, Zitate, Sentiment und Rang wider.
* **Erwähnungen** - Die Häufigkeit, mit der Ihre Marke in KI-Antworten für dieses Thema oder diese Themen-/Eingabeaufforderungskombination erwähnt wurde.
* **Sentiment** - Die Markenwahrnehmung in KI-Antworten, da sie sich auf jedes Thema bezieht, berechnet als Durchschnitt über alle Wochen hinweg. Wird nur aufgefüllt, wenn Ihre Marke tatsächlich erwähnt wird.
* **Position** - Die relative Bekanntheit Ihrer Marke in KI-Antworten, berechnet als Durchschnitt über alle Wochen hinweg.
* **Alle Zitate** - Die Anzahl der eindeutigen Quellen, die in KI-Antworten für dieses Thema oder diese Themen-/Eingabeaufforderungskombination zitiert werden (einschließlich Eigene Zitierungen).
* **Eigene Zitierungen** - Die Häufigkeit, mit der Ihre Marke in KI-Antworten für dieses Keyword oder diese Keyword-/Fragekombination zitiert wurde.
  <!--* **Executions**-->

Sie können auch zusätzliche Details zu jedem Thema anzeigen, indem Sie auf das **Details**-Symbol am Ende jeder Zeile klicken.

>[!TAB Share of Voice]

Die Share of Voice-Tabelle bietet einen vergleichenden Überblick über die Leistung Ihrer Marke in wichtigen Themen der generativen KI-Reaktionen. Es hilft Ihnen, Sichtbarkeitslücken zu identifizieren, die Leistung der Konkurrenz zu verfolgen und Bereiche für die Optimierung zu priorisieren. Angezeigt werden die folgenden Metriken:

* **Thema** - Das analysierte Thema.
* **Beliebtheit** - Das Suchvolumen für das Thema in Bezug auf alle anderen Themen in Ihrer Analyse.
* **Erwähnungen** - Gibt an, wie oft Ihre Marke in KI-Antworten für das Thema oder die Themen-/Eingabeaufforderungskombination erwähnt wurde.
* **Rangfolge** - Die Rangfolge der Share of Voice Ihrer Marke in Bezug auf alle anderen identifizierten Marken.
* **Share of Voice** - Der Prozentsatz aller Erwähnungen, die Ihre Marke in KI-generierten Antworten enthält.
* **Top 5 Andere** - Die fünf Top-Marken, die am häufigsten für dieselben Themen erwähnt werden. Die Marken sind nach ihrem Share of Voice (vom höchsten zum niedrigsten) organisiert.

>[!ENDTABS]

### Verwenden der Data Insights-Tabelle {#using-data-insights}

Die Tabelle „Dateneinblicke“ hilft Ihnen, von Metriken zu Aktionen zu wechseln, indem die Leistung auf Themen- und Eingabeaufforderungsebene aufgeschlüsselt wird.

Wichtige Verwendungsmöglichkeiten der Tabelle:

* Priorisieren Sie Themen mit hoher Popularität bei geringer Sichtbarkeit - Fokusoptimierung, bei denen die Zielgruppennachfrage stark ist, Ihr Markenpräsenz jedoch schwach ist.
* Verfolgen Sie Sentiment-Verschiebungen - erkennen Sie Themen, bei denen Erwähnungen im negativen oder neutralen Bereich liegen, und koordinieren Sie Ihre Reaktion.
* Zitate mit Eigene Zitierungen vergleichen - Eingabeaufforderungen identifizieren, bei denen Ihre Marke erwähnt wird, der Inhalt anderer Marken jedoch zitiert wird, was eine Inhaltslücke signalisiert.
* Positionsbereich auswerten - Überwachen Sie, ob Ihre Marke frühzeitig in KI-Reaktionen (Positionen 1-3) oder weiter unten (6-10) erscheint.
