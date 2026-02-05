---
title: URL-Überwachung
description: Erfahren Sie, wie Sie mit dem URL-Inspektor analysieren können, wie bestimmte Seiten in Ihrer Domain bei der KI-Suche funktionieren.
feature: URL Inspector
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 1%

---


# URL-Überwachung

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

* **Eindeutige Eingabeaufforderungen mit Eigene Zitierungen** - Die Gesamtzahl der eindeutigen KI-Eingabeaufforderungen mit Eigene Zitierungen.
* **Eindeutige Eingabeaufforderungen insgesamt** - Die Gesamtzahl der eindeutigen AI-Eingabeaufforderungen.
* **Eindeutig zitierte URLs** - Die Anzahl der eindeutigen eigenen URLs, die zitiert wurden.
* **Gesamtzahl der angegebenen**: Gesamtzahl der Fälle, in denen eine eigene URL in KI-generierten Antworten zitiert wurde.
* **Gesamtzahl der Agententreffer** - Die Gesamtzahl der Treffer von KI-Agenten auf Ihren URLs.
* **Verweistreffer von LLMs** - Die Gesamtzahl der Treffer, die von KI-generierten Antworten an Ihre URLs weitergeleitet werden.

Trendindikatoren für jede Übersichtsmetrik zeigen, wie sich diese Werte im Zeitverlauf im Vergleich zum vorherigen Zeitraum ändern.

## Ihre zitierten URLs

Die Ansicht „zitierte URLs“ listet alle URLs Ihrer Marke auf, die in KI-generierten Antworten zitiert wurden, einschließlich unterstützender Metriken. Beide Tabellen verfügen über ein Suchfeld für den schnellen Zugriff auf Themen. Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle in das Reporting für Führungskräfte einzuschließen.

![zitierte URLs](/help/dashboards/assets/cited-urls.png)

Die folgenden Metriken werden bereitgestellt:

* **URL** - die analysierte URL.
* **Mal zitiert** - Die Häufigkeit, mit der die URL in KI-generierten Antworten zitiert wurde.
* **Eingabeaufforderungen in** - Die Anzahl der eindeutigen AI-Eingabeaufforderungen, die die URL angegeben haben.
* **Kategorien** - Die Produktkategorien oder Themen, die mit der URL verknüpft sind.
* **Regions** - Die geografische Region, in der die URL zitiert wurde.
* **Agententreffer** - Die Gesamtzahl der Treffer von KI-Agenten auf den URLs.
* **Verweistreffer** - Die Anzahl der Treffer, die von KI-generierten Antworten an die URLs weitergeleitet werden.

## Um Zitierungen konkurrierende Trend-URLs

Die Ansicht der Trend-URLs, die um Zitate konkurrieren, zeigt externe URLs an, die derzeit in markenrelevanten Antworten zitiert werden, um zu messen, wer in Ihrem Raum die Zitate gewinnt. Die Datentabelle verfügt über ein Suchfeld für den schnellen Zugriff auf bestimmte URLs. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle in das Reporting für Führungskräfte einzuschließen.

![Trend-URLs, die um Zitate konkurrieren](/help/dashboards/assets/trend-url.png)

Die folgenden Metriken werden bereitgestellt:

* **URL** - die analysierte URL
* **Content-**: Der Typ des Inhalts (privat, sozial, verdient, andere).
* **Mal zitiert** - Die Häufigkeit, mit der die URL in KI-generierten Antworten zitiert wurde.
* **Eingabeaufforderungen in** - Die Anzahl der eindeutigen AI-Eingabeaufforderungen, die die URL angegeben haben.
* **Kategorien** - Die Produktkategorien oder Themen, die mit der URL verknüpft sind.
* **Regions** - Die geografische Region, in der die URL zitiert wurde.

### Fenster „Details“

Sowohl für die Zitat- als auch für die Trendansicht verfügen die URLs über **Schaltfläche** Details“ am Ende jeder Zeile. Durch Klicken auf die Schaltfläche wird ein separates Fenster mit weiteren Details angezeigt. Das Detailfenster zeigt an, wie oft die URL zitiert wird, <!--the sentiment of AI responses where it is mentioned,--> Themen und Eingabeaufforderungen, in denen sie angezeigt wird, sowie Trends beim Agent und Referral Traffic im Zeitverlauf (für eigene URLs).

![Detailfenster](/help/dashboards/assets/details-url.png)
