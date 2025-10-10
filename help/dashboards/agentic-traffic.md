---
title: Agenturverkehr
description: Dies ist die Artikelübersicht.
source-git-commit: f92ca3eaa81d05135c65df60267280314c6e2d6f
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---


# Agenturverkehr {#agentic-traffic}

Das Dashboard für den Agentenverkehr zeigt an, wie KI-Agenten (Crawler und Chatbots) mit Ihrer Site interagieren. Mithilfe dieser Ansicht können Sie die Gesamtzahl der Anfragen und allgemeine leistungsbezogene Metriken verfolgen. Sie können auch die Verteilung des Traffics auf Märkte, Kategorien, Seiten und Agenten anzeigen. Die von diesem Dashboard verwendeten Daten stammen aus den CDN-Protokollen. Daher müssen Sie **CDN-Protokollweiterleitung“**, um Metriken anzuzeigen. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

Auf dieser Seite wird Folgendes beschrieben:

* [Filter](#filters)
* [CDN-Setup](#cdn-setup)
* [Verkehrsverteilung](#traffic-distribution)
* [Trends beim Agentenverkehr](#agentic-trends)
* [Top- und Bottom-Mover](#top-bottom-movers)
* [Benutzeragent- und URL-Leistungsanalyse](#user-url-performance)

## CDN-Setup {#cdn-setup}

Bei der ersten Anmeldung ist das Dashboard für den Agentenverkehr leer. Um agentische Interaktionen anzuzeigen, müssen Sie die **CDN-Protokollweiterleitung“**. **TBD Verweisen Sie auf das CDN-Setup in „Schnellstart/Onboarding“**

![CDN-Setup](/help/dashboards/assets/ag-log-forward.png)

1. Wählen Sie Ihren CDN-Provider aus (z. B. Akamai, Adobe-Managed Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare oder andere).
2. Primäre Kontakt-E-Mail eingeben.
3. Klicken Sie **Aktivierungsanfrage**, um die Protokollweiterleitung zu aktivieren.

Nach der Aktivierung werden Protokolle aufgenommen und im Dashboard Metriken wie Gesamtanzahl der Agenteninteraktionen, Erfolgsrate, Treffer nach Markt, Analyse der Benutzeragenten und Leistung auf URL-Ebene angezeigt.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
* **Kategorie** - Filtert die angezeigten Ergebnisse nach vordefinierten Kategorien. Sie können diesem Feld auch benutzerdefinierte Kategorien hinzufügen (**SR**-how?).
* **Platform** - Wählen Sie die zu analysierende KI-Engine aus.
* **Agent-Typ** - Filtern Sie nach dem Typ des KI-Agenten, der mit Ihrer Site interagiert hat. Sie können nach Crawlern, Chatbots oder allen Agenten filtern.
* **Erfolgsrate** - Filtern nach der Interaktionsqualität (hoch, mittel oder niedrig). Diese Metrik stellt den Prozentsatz erfolgreicher HTTP-Anfragen dar, einschließlich sowohl direkter erfolgreicher Antworten als auch Umleitungen.
* **Content-Typ** - Filtern nach Content-Typ, entweder HTML oder TXT.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Verkehrsverteilung {#traffic-distribution}

Die Ansicht Traffic-Verteilung zeigt, wie der Agent-Traffic auf Märkte, Kategorien und Seitentypen verteilt wird. So können Sie mithilfe dieser Ansicht ermitteln, auf welche Regionen, Produktbereiche oder Inhaltsformate KI-Agenten bei der Interaktion mit Ihrer Site am häufigsten zugreifen.

![Traffic-Verteilung](/help/dashboards/assets/ag-main.png)

Oben auf der Seite gibt es drei Schlüsselmetriken, die Sie beachten müssen:

* **Agenteninteraktionen** - Diese Metrik stellt die Gesamtzahl der Anfragen dar, die von KI-Agenten an Ihre Website gesendet wurden. Dies umfasst den gesamten Traffic von Suchmaschinen, Chatbots und anderem nicht-menschlichen Traffic.
* **Erfolgsrate** - Diese Metrik stellt den Prozentsatz erfolgreicher HTTP-Anfragen dar, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Durchschnittliche TTFB** - Zeit bis zum ersten Byte (Time To First Byte, TTFB) misst die Zeit, die für das erste Byte der Daten benötigt wird, die vom Server empfangen werden. Niedrigere Werte bedeuten kürzere Serverreaktionszeiten.

Trendindikatoren für jede Schlüsselmetrik zeigen, wie sich diese Werte im Laufe der Zeit im Vergleich zum vorherigen Zeitraum ändern.

## Trends beim Agentenverkehr {#agentic-trends}

Verwenden Sie das Diagramm Agentenmäßige Traffic-Trends , um die wöchentlichen Gesamtwerte von erfolgreichen, fehlgeschlagenen und allgemeinen Treffern zu verfolgen. Auf diese Weise können Sie Veränderungen der Agentenaktivität und -leistung im Zeitverlauf überwachen. Sie können auch den Mauszeiger über das Diagramm bewegen, um die Datenentwicklung über den wöchentlichen Zeitrahmen hinweg zu sehen.

![Agentische Traffic-Trends](/help/dashboards/assets/ag-trends.png)

## Top- und Bottom-Mover {#top-bottom-movers}

Mit diesen beiden Metriken werden die URLs wie folgt sortiert:

* **Top Movers** - Die URLs mit dem größten Anstieg des Agent-Traffics von der ältesten zur neuesten Woche.
* **Bottom Movers** - URLs mit dem größten Rückgang im Agentenverkehr von der ältesten zur neuesten Woche.

## Benutzeragent- und URL-Leistungsanalyse {#user-url-performance}

Die Ansichten Benutzeragent und URL-Leistungsanalyse bieten weitere Datenaufschlüsselungen zur Interaktion von Crawlern und Chatbots mit Ihrer Site. Klicken Sie auf die Registerkarten unten, um detaillierte Beschreibungen anzuzeigen.

![Benutzeragent- und URL-Leistungsanalyse](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Benutzeragenten-Analyse]

Die Tabelle Benutzeragentenanalyse enthält eine Aufschlüsselung des Traffics nach Seitentyp und Agententyp (z. B. Crawler im Vergleich zu Chatbots). Auf diese Weise ist es einfach zu verstehen, welche KI-Agenten welche Teile Ihrer Site durchsuchen. Es umfasst die folgenden Kategorien:

* **Seitentyp** - Der Seitentyp.
* **Agent Type** - Der KI-Agent, der die Seite durchsucht, entweder ein Crawler oder ein Chatbot.
* **Treffer** - Die Gesamtzahl der Anfragen, die von KI-Agenten für diesen bestimmten Seitentyp gestellt wurden.

Sie können auch die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Agentenanalyse für Ihr Team freizugeben oder in das Reporting für Führungskräfte aufzunehmen.

>[!TAB URL-Leistungsanalyse]

Die Tabelle URL-Leistungsanalyse zeigt eine detaillierte Ansicht der einzelnen URLs. Dazu gehören Treffer, eindeutige Agenten, Top-Agenten, Erfolgsraten und Kategorien. Auf diese Weise können Sie hochwertige Seiten identifizieren, Durchforstungslücken erkennen und Inhalte für KI-Engines optimieren. Die URLs werden nach Traffic-Volumen sortiert. Die Tabelle enthält die folgenden Kategorien:

* **URL** - Die untersuchte URL.
* **Treffer insgesamt** - Gesamtzahl der Anfragen, die von KI-Agenten an die URL gesendet wurden.
* **Eindeutige Agenten** - Die Anzahl der verschiedenen KI-Agenten, die auf die URL zugegriffen haben.
* **Top-Agent** - Der KI-Agent, der den meisten Traffic zur URL generiert hat.
* **Top-Agent-**: Der Typ des KI-Agenten, der den meisten Traffic zu dieser URL generiert hat.
* **Erfolgsrate** - Der Prozentsatz erfolgreicher HTTP-Anfragen, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Kategorie** - Die Kategorie, die dem Inhalt Ihrer Seite am ehesten entspricht.

Die URL-Leistungstabelle enthält ein Suchfeld für den schnellen Zugriff auf URLs. Außerdem können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle in das Reporting für Führungskräfte einzuschließen.

>[!ENDTABS]
