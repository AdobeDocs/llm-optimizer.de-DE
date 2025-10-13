---
title: URL-Inspektor
description: Erfahren Sie, wie Sie mit dem URL-Inspektor analysieren können, wie bestimmte Seiten in Ihrer Domain bei der KI-Suche funktionieren.
source-git-commit: a699f8f3c50f77d07f29cd354fd1ef8e6eed8ff9
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# URL-Inspektor

Mit dem URL-Inspektor können Sie analysieren, wie bestimmte Seiten in Ihrer Domain bei der KI-Suche funktionieren. Es kombiniert Sichtbarkeit, Agentendatenverkehr und Verweisdaten auf URL-Ebene, um Ihnen einen granularen Überblick darüber zu geben, welche URLs zitiert werden und wie oft sie in Antworten angezeigt werden.

![URL-Inspektor](/help/dashboards/assets/url-insp.png)

## Filter

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
* **Kategorie** - Filtert die angezeigten Ergebnisse nach Kategorien.
* **Platform** - Wählen Sie die zu analysierende KI-Engine aus.
* **Seiteninhaltstyp** - Filtern nach Inhaltstyp.
* **Region** - Filtern der Ergebnisse nach Geografie. Nicht alle Regionen werden zum Start verfügbar sein.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Übersichtsmetriken

Der URL-Inspektor bietet mehrere Übersichtsmetriken, mit denen Sie schnell beurteilen können, wie Ihre Seiten in KI-Suchen abschneiden. Die folgenden Metriken werden bereitgestellt:

* **Eindeutige Eingabeaufforderungen mit eigenen Zitaten** - Die Gesamtzahl der eindeutigen AI-Eingabeaufforderungen mit eigenen Zitaten.
* **Eindeutige Eingabeaufforderungen insgesamt** - Die Gesamtzahl der eindeutigen AI-Eingabeaufforderungen.
* **Eindeutig zitierte URLs** - Die Anzahl der eindeutigen eigenen URLs, die zitiert wurden.
* **Gesamtzahl der angegebenen**: Gesamtzahl der Fälle, in denen eine eigene URL in KI-generierten Antworten zitiert wurde.
<!-- * **Total agentic hits** - The total number of hits from AI agents on your URLs.
* **Referral hits from LLMs** - The total number of hits directed from AI-generated answers to your URLs.-->

Trendindikatoren für jede Übersichtsmetrik zeigen, wie sich diese Werte im Zeitverlauf im Vergleich zum vorherigen Zeitraum ändern.

## Ihre zitierten URLs

Die Ansicht „zitierte URLs“ listet alle URLs Ihrer Marke auf, die in KI-generierten Antworten zitiert wurden, einschließlich unterstützender Metriken. Die Datentabelle verfügt auch über ein Suchfeld für den schnellen Zugriff auf bestimmte URLs. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle in das Reporting für Führungskräfte einzuschließen.

![zitierte URLs](/help/dashboards/assets/cited-urls.png)

Die folgenden Metriken werden bereitgestellt:

* **URL** - die analysierte URL.
* **Mal zitiert** - Die Häufigkeit, mit der die URL in KI-generierten Antworten zitiert wurde.
* **Eingabeaufforderungen in** - Die Anzahl der eindeutigen AI-Eingabeaufforderungen, die die URL angegeben haben.
* **Kategorien** - Die Produktkategorien oder Themen, die mit der URL verknüpft sind.
* **Regions** - Die geografische Region, in der die URL zitiert wurde.
* **Agententreffer** - Die Gesamtzahl der Treffer von KI-Agenten auf den URLs.
* **Verweistreffer** - Die Anzahl der Treffer, die von KI-generierten Antworten an die URLs weitergeleitet werden.

## Trend-URLs im Wettbewerb um Zitate

Die Ansicht der Trend-URLs, die um Zitate konkurrieren, zeigt externe URLs an, die derzeit in markenrelevanten Antworten zitiert werden, um zu messen, wer in Ihrem Raum die Zitate gewinnt. Die Datentabelle verfügt über ein Suchfeld für den schnellen Zugriff auf bestimmte URLs. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle in das Reporting für Führungskräfte einzuschließen.

![Trend-URLs, die um Zitate konkurrieren](/help/dashboards/assets/trend-url.png)

Die folgenden Metriken werden bereitgestellt:

* **URL** - die analysierte URL
* **Content-**: Der Typ des Inhalts (Inhaber, Social, Verdient, Mitbewerber).
* **Mal zitiert** - Die Häufigkeit, mit der die URL in KI-generierten Antworten zitiert wurde.
* **Eingabeaufforderungen in** - Die Anzahl der eindeutigen AI-Eingabeaufforderungen, die die URL angegeben haben.
* **Kategorien** - Die Produktkategorien oder Themen, die mit der URL verknüpft sind.
* **Regions** - Die geografische Region, in der die URL zitiert wurde.

### Fenster „Details“

Sowohl für die zitierte als auch für die Trendansicht verfügen die URLs über eine Schaltfläche **Details**, wenn Sie den Mauszeiger über eine bestimmte URL bewegen. Durch Klicken auf die Schaltfläche wird ein separates Fenster mit weiteren Details angezeigt. Das Detailfenster zeigt an, wie oft die URL zitiert wird, wie die Stimmung der KI-Antworten, wo sie erwähnt wird, die Themen und Eingabeaufforderungen, in denen sie angezeigt wird, und die Trends beim Agent- und Verweisdatenverkehr im Zeitverlauf (für eigene URLs).

![Detailfenster](/help/dashboards/assets/details-url.png)
