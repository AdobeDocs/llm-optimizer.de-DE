---
title: Markenpräsenz
description: Erfahren Sie, wie Sie mit dem Dashboard „Markenpräsenz“ analysieren können, wie Ihre Marke in KI-generierten Antworten wahrgenommen wird.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: ht
source-wordcount: '1299'
ht-degree: 100%

---


# Markenpräsenz {#brand-presence}

Das Dashboard „Markenpräsenz“ bietet einen detaillierten Überblick darüber, wie Ihre Marke in KI-generierten Antworten wahrgenommen wird. Es zeigt an, wo, wie oft und in welchem Kontext Ihre Marke erwähnt wird. Sie können das Dashboard verwenden, um die Sichtbarkeit zu messen, Zitierungen zu verfolgen und Sentiment-Trends zu erkunden. Das Dashboard ist in mehrere Abschnitte unterteilt, die jeweils unterschiedliche Erkenntnisse bereitstellen. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Markenpräsenz](/help/dashboards/assets/brand-main.png)

Diese Seite beschreibt Folgendes:

* [Filter](#filters)
* [Überblickmetriken](##key-metrics)
* [Vergleich mit anderen](##others-comparison)
* [Sentiment-Trend](#sentiment-trend)
* [Datenerkenntnisse](#data-insights)

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** – Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel die letzten 4 Wochen. Sie können den Zeitraum auch mit der Option **Benutzerdefinierte Wochen** anpassen.
* **Kategorie** – Filtert die angezeigten Ergebnisse nach vordefinierten Kategorien oder benutzerdefinierten Kategorien.
* **Thema** – Filtern Sie nach Thema, um Inhaltsthemen und Themenbereiche zu analysieren, in denen Ihre Marke in KI-Antworten erscheint.
* **Plattform** – Wählen Sie die zu analysierende KI-Engine aus.LLM Optimizer unterstützt derzeit ChatGPT, Google AI Overviews, den Google AI Mode, Microsoft Copilot, Google Gemini und Perplexity.
* **Herkunft der Prompts** – Wählen Sie die Herkunft der Prompts. Die Herkunft kann entweder von den Benutzenden eingegeben oder per KI generiert werden.
* **Prompt-Branding** – Filtern Sie die Ergebnisse nach Prompts mit oder ohne Branding.
* **Region** – Filtern Sie die Ergebnisse nach Geografie. Bei Veröffentlichung werden noch nicht alle Regionen verfügbar sein.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden**, um Ihre Auswahl auf das Dashboard anzuwenden.

## Überblickmetriken {#overview-metrics}

Im Dashboard werden oben auf der Seite drei sehr wichtige Metriken hervorgehoben: Sichtbarkeitsbewertung, Erwähnungen und Zitierungen. Je niedriger die Anzahl bei diesen Metriken ist, desto schlechter wird Ihre Marke wahrgenommen. Sie sollten Maßnahmen ergreifen, um Ihre Markenpräsenz zu verbessern. Nachfolgend finden Sie eine kurze Beschreibung jeder Metrik und dessen, was sie darstellt.

![Überblickmetriken](/help/dashboards/assets/overview-metrics.png)

### Sichtbarkeitsbewertung {#visibility-score}

Die Sichtbarkeitsbewertung besteht aus Faktoren wie Erwähnungen, Zitierungen, Sentiment und Rang. Jedem Faktor ist ein bestimmtes „Gewicht“ zugeordnet, das auf den Endwert angerechnet wird.

### Erwähnungen der Marke {#mentions}

Diese Metrik gibt an, wie oft Ihre Marke oder Ihre Kategorien in den KI-Prompts der Stichprobe insgesamt erwähnt wurden. Wenn Sie beispielsweise die Marke „Kaffee B“ mit den Kategorien „Maschinen“ und „Zubehör“ verwenden, zählt diese Metrik die Gesamtzahl der Fälle, in denen diese in den KI-Antworten der Stichprobe erscheinen.

### Zitierungen {#citations}

Diese Metrik gibt an, wie oft Ihre Site als Quelle referenziert wurde.

Für jede Schlüsselmetrik zeigen Trend-Indikatoren an, wie sich die Werte im Zeitverlauf verglichen mit dem vorherigen Zeitraum ändern.

## Vergleich mit anderen {#others-comparison}

Im Abschnitt „Vergleich mit anderen“ können Sie bis zu fünf andere Marken auswählen und deren Erwähnungen und Zitierungen mit denen Ihrer Marke vergleichen. So können Sie Ihre Leistung im Verhältnis zu anderen Marken anzeigen und benchmarken.

![Vergleich mit anderen](/help/dashboards/assets/other-comparison.png)

Die anderen Marken werden aus der Dropdown-Liste ausgewählt und die Diagramme werden aktualisiert, wenn Sie auf **Filter anwenden** klicken. Die Diagramme zeigen wöchentliche Erwähnungen und Zitierungen der Marken nebeneinander. Sie können auch den Mauszeiger über das Diagramm bewegen, um die Datenentwicklung im wöchentlichen Zeitrahmen zu sehen.

## Sentiment-Trend-Analyse {#sentiment-trend}

Im Abschnitt „Sentiment-Trend-Analyse“ können Sie verfolgen, wie Ihre Marke in den KI-Antworten der Stichprobe wahrgenommen wird. Die Sentiment-Trend-Metrik kann entweder positiv, neutral oder negativ sein. Beispielsweise kann sie positiv sein, wenn Antworten die Produktqualität hervorheben, oder negativ, wenn sie schlechten Service erwähnen. Das Trend-Diagramm zeigt die Veränderungen der Markenwahrnehmung von Woche zu Woche. Dieser Abschnitt wird erst mit Daten gefüllt, wenn Ihre Marke erwähnt wurde.

![Sentiment-Trend](/help/dashboards/assets/sentiment-trend.png)

## Datenerkenntnisse und Share of Voice {#data-insights}

Abgerundet wird das Dashboard durch zwei wichtige Tabellen: „Datenerkenntnisse“ und „Share of Voice“. Anhand der Informationen in diesen Tabellen können Sie erkennen, wo Ihre Marke stark ist und wo eine Optimierung erforderlich ist.

Mit der Tabelle **Datenerkenntnisse** erfahren Sie mehr über die Themen und Fragen von Benutzenden und können die Wirkung Ihrer Inhalte bewerten und optimieren. Die Ergebnisse werden nach Themen und Prompts aufgeführt. In der Tabelle **Share of Voice** wird Ihre Markensprache themenübergreifend mit der anderer Marken verglichen. So können Sie Lücken identifizieren und Themen zukünftig priorisieren.

![Datenerkenntnisse](/help/dashboards/assets/data-insights.png)

Beide Tabellen verfügen über ein Suchfeld für den schnellen Zugriff auf Themen. Mit der Schaltfläche **Spalten konfigurieren** können Sie anpassen, welche Metriken angezeigt werden. Außerdem können Sie mit der Option **Exportieren** die CSV-Datei der Tabelle herunterladen und die Erkenntnisse mit Ihrem Team teilen oder die Tabellen in das Reporting für Führungskräfte aufnehmen.

Klicken Sie auf die Registerkarten unten, um Details zu jeder Tabelle und den zugehörigen Metriken anzuzeigen.

>[!BEGINTABS]

>[!TAB Datenerkenntnisse]

Mit der Tabelle „Datenerkenntnisse“ können Sie Themen und Benutzer-Prompts erkunden und die Wirkung Ihrer Inhalte bewerten und optimieren. Folgende Metriken werden angezeigt:

* **Thema** – Die Themenkategorie stellt SEO-Schlüsselwörter und Benutzerfragen in Verbindung mit Ihrer Marke dar. Sie können auf ein Thema klicken, um es zu erweitern und die einzelnen für die Markenpräsenz analysierten Prompts anzuzeigen. Jedes Thema verfügt über eine Schaltfläche **Details**, wenn Sie mit der Maus darauf zeigen. Durch Klicken auf die Schaltfläche wird ein separates Fenster mit weiteren Details angezeigt.
* **Region** – Zeigt die Region der Prompts an.
* **Beliebtheit** – Die Kategorie „Beliebtheit“ gibt das Suchvolumen für dieses Thema relativ zu allen anderen Themen in der Analyse an. Mögliche Werte sind „Hoch“, „Mittel“ und „Niedrig“.
* **Sichtbarkeitsbewertung** – Die Sichtbarkeitsbewertung für dieses Thema. Sie spiegelt gewichtete Faktoren wie Erwähnungen, Zitierungen, Sentiment und Rang wider.
* **Erwähnungen** – Gibt an, wie oft Ihre Marke in KI-Antworten für dieses Thema oder für diese Themen-Prompt-Kombination erwähnt wurde.
* **Sentiment** – Die Markenwahrnehmung in KI-Antworten bezogen auf das jeweilige Thema, berechnet als Durchschnitt über alle Wochen hinweg. Wird nur mit Daten gefüllt, wenn Ihre Marke tatsächlich erwähnt wird.
* **Position** – Die relative Bekanntheit Ihrer Marke in KI-Antworten, berechnet als Durchschnitt über alle Wochen hinweg.
* **Alle Zitierungen** – Anzahl der eindeutigen Quellen, die in KI-Antworten für dieses Thema oder diese Themen-Prompt-Kombination zitiert wurden (einschließlich eigener Zitierungen).
* **Eigene Zitierungen** – Gibt an, wie oft Ihre Marke in KI-Antworten für dieses Keyword oder diese Keyword-Frage-Kombination zitiert wurde.
  <!--* **Executions**-->

Sie können auch zusätzliche Details zu jedem Thema anzeigen, indem Sie am Ende der gewünschten Zeile auf das Symbol **Details** klicken.

>[!TAB Share of Voice]

Die Tabelle „Share of Voice“ bietet einen vergleichenden Überblick über die Leistung Ihrer Marke in wichtigen Themen der Antworten generativer KI. So können Sie Sichtbarkeitslücken identifizieren, die Leistung der Wettbewerber nachverfolgen und Bereiche mit Optimierungspotenzial priorisieren. Folgende Metriken werden angezeigt:

* **Thema** – Das analysierte Thema.
* **Beliebtheit** – Das Suchvolumen für dieses Thema im Verhältnis zu allen anderen Themen in Ihrer Analyse.
* **Erwähnungen** – Gibt an, wie oft Ihre Marke in KI-Antworten für dieses Thema oder für diese Themen-Prompt-Kombination erwähnt wurde.
* **Rangliste** – Der Rang des Share of Voice Ihrer Marke im Vergleich zu allen identifizierten anderen Marken.
* **Share of Voice** – Der Prozentsatz aller Erwähnungen, die Ihre Marke in KI-generierten Antworten enthält.
* **Top 5 andere** – Die fünf Top-Marken, die am häufigsten für dieselben Themen erwähnt werden. Die Marken sind sortiert nach ihrem Share of Voice (vom höchsten zum niedrigsten).

>[!ENDTABS]

### Verwenden der Tabelle „Datenerkenntnisse“ {#using-data-insights}

Durch Aufschlüsselung der Leistung auf Themen- und Prompt-Ebene hilft Ihnen die Tabelle „Datenerkenntnisse“ dabei, aus Metriken Aktionen abzuleiten.

Wichtige Verwendungsmöglichkeiten der Tabelle:

* Priorisieren Sie Themen mit hoher Beliebtheit und geringer Sichtbarkeit. Fokussieren Sie die Optimierung auf Bereiche, in denen eine hohe Zielgruppennachfrage besteht, Ihre Markenpräsenz jedoch schwach ist.
* Verfolgen Sie Sentiment-Verschiebungen nach. Erkennen Sie Themen, bei denen Erwähnungen im negativen oder neutralen Bereich liegen, und koordinieren Sie Ihre Reaktion.
* Vergleichen Sie „Zitierungen“ und „Eigene Zitierungen“. Identifizieren Sie Prompts, in denen Ihre Marke erwähnt wird, der Inhalt anderer Marken jedoch zitiert wird, was eine Inhaltslücke signalisiert.
* Werten Sie den Positionsbereich aus. Überwachen Sie, ob Ihre Marke in KI-Antworten frühzeitig (Positionen 1–3) oder weiter unten (6–10) erscheint.
