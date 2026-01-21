---
title: Agenturverkehr
description: Erfahren Sie, wie Sie das Dashboard für den Agentenverkehr verwenden, um zu sehen, wie KI-Agenten mit Ihrer Site interagieren.
feature: Agentic Traffic
source-git-commit: a75ce71dc0ab9ffe7956a3dbd09dca23ea5f7096
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---


# Agenturverkehr {#agentic-traffic}

Das Dashboard für den Agent-Traffic zeigt an, wie KI-Agenten (Crawler und Chatbots) mit Ihrer Site interagieren. Mithilfe dieser Ansicht können Sie die Gesamtzahl der Anfragen und allgemeine leistungsbezogene Metriken verfolgen. Sie können auch die Verteilung des Traffics auf Märkte, Kategorien, Seiten und Agenten anzeigen. Die von diesem Dashboard verwendeten Daten stammen aus den CDN-Protokollen. Daher müssen Sie **CDN-Protokollweiterleitung“**, um Metriken anzuzeigen. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Traffic-Verteilung](/help/dashboards/assets/ag-main.png)

Auf dieser Seite wird Folgendes beschrieben:

* [Filter](#filters)
* [CDN-Setup](#cdn-setup)
* [Verkehrsverteilung](#traffic-distribution)
* [Trends beim Agentenverkehr](#agentic-trends)
* [Top- und Bottom-Mover](#top-bottom-movers)
* [Benutzeragent- und URL-Leistungsanalyse](#user-url-performance)

## CDN-Protokollweiterleitung {#cdn-setup}

Ohne **CDN-Protokollweiterleitung** ist das Agent-Traffic-Dashboard leer. Um agentische Interaktionen anzuzeigen, müssen Sie die **CDN-Protokollweiterleitung“**.  Bei der ersten Anmeldung wird eine Meldung angezeigt, wie in der Abbildung unten dargestellt.

![CDN-Setup](/help/dashboards/assets/ag-log-forward1.png)

Wählen Sie **Wechseln zur Konfiguration** aus und Sie navigieren automatisch zur Registerkarte **CDN-Konfiguration** des Dashboards [Kundenkonfiguration](/help/dashboards/customer-configuration.md).

![Integriertes CDN-Setup](/help/dashboards/assets/ag-log-forward2.png)

Wählen Sie auf dieser Registerkarte die Option **Integriertes CDN** aus. Daraufhin wird das Fenster CDN-Anbieter angezeigt.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->
Im Fenster **Onboarding CDN Provider**:

1. Wählen Sie Ihren CDN-Provider aus (z. B. Akamai, Adobe-Managed Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare oder andere).
2. Klicken Sie **Onboard**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an llmo-now@adobe.com wenden, um Hilfe zu erhalten.

Nach der Aktivierung werden Protokolle aufgenommen und im Dashboard Metriken wie Gesamtanzahl der Agenteninteraktionen, Erfolgsrate, Treffer nach Markt, Analyse der Benutzeragenten und Leistung auf URL-Ebene angezeigt.

LLM Optimizer verarbeitet eine Teilmenge von Feldern aus den CDN-Protokollen. Obwohl die Namen der Rohprotokoll-Felder je nach CDN-Provider variieren, werden sie normalisiert und wie folgt dargestellt:

* URL (nur Pfad)
* Benutzeragent
* Status-Code
* Referrer-Kopfzeile
* Host-Kopfzeile
* Zeit bis zum ersten Byte (TTFB)
* Anforderungsmethode
* Zeitstempel
* Inhaltstyp

Diese normalisierten Felder werden über die agentische Ansicht verfügbar gemacht. Im Dashboard [Verweisdatenverkehr](/help/dashboards/referral-traffic.md) werden CDN-Protokolle zur Anzeige von Seitentreffermetriken verwendet. In keiner Phase der CDN-Protokollaufnahme oder der nachfolgenden Datenverarbeitung werden personenbezogene Daten (PII) verarbeitet oder gespeichert.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
* **Kategorie** - Filtert die angezeigten Ergebnisse nach vordefinierten Kategorien oder benutzerdefinierten Kategorien.
* **Platform** - Wählen Sie die zu analysierende KI-Engine aus.
* **Agent-Typ** - Filtern Sie nach dem Typ des KI-Agenten, der mit Ihrer Site interagiert hat. Sie können nach Crawlern, Chatbots oder allen Agenten filtern.
* **Erfolgsrate** - Filtern nach der Interaktionsqualität (hoch, mittel oder niedrig). Diese Metrik stellt den Prozentsatz erfolgreicher HTTP-Anfragen dar, einschließlich sowohl direkter erfolgreicher Antworten (2xx Status-Codes) als auch Umleitungen (3xx Status-Codes).
* **Content-**: Anzeigen der agenten Interaktion für verschiedene Inhaltstypen wie HTML, PDF usw.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Verkehrsverteilung {#traffic-distribution}

Die Ansicht Traffic-Verteilung zeigt, wie der Agent-Traffic auf Märkte, Kategorien und Seitentypen verteilt wird. So können Sie mithilfe dieser Ansicht ermitteln, auf welche Regionen, Produktbereiche oder Inhaltsformate KI-Agenten bei der Interaktion mit Ihrer Site am häufigsten zugreifen.

![Traffic-Verteilung](/help/dashboards/assets/ag-main.png)

Oben auf der Seite gibt es drei Schlüsselmetriken, die Sie beachten müssen:

* **Agenteninteraktionen** - Diese Metrik stellt die Gesamtzahl der Anfragen dar, die von KI-Agenten an Ihre Website gesendet wurden. Dies umfasst den gesamten Traffic von Suchmaschinen, Chatbots und anderem nicht-menschlichen Traffic.
* **Erfolgsrate** - Diese Metrik stellt den Prozentsatz erfolgreicher HTTP-Anfragen dar, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Durchschnittliche TTFB** - Zeit bis zum ersten Byte (Time To First Byte, TTFB) misst die Zeit, die für das erste Byte der Daten benötigt wird, die vom Server empfangen werden. Der Durchschnittswert wird auf der Grundlage der Anzahl der Anfragen gewichtet, die jeden Code zurückgeben, und schließt Anfragen aus, die zu Antworten von 5xx geführt haben. Niedrigere Werte bedeuten kürzere Serverreaktionszeiten.

Trendindikatoren für jede Schlüsselmetrik zeigen, wie sich diese Werte im Laufe der Zeit im Vergleich zum vorherigen Zeitraum ändern.

## Trends beim Agentenverkehr {#agentic-trends}

Verwenden Sie das Diagramm Agentenmäßige Traffic-Trends , um die wöchentlichen Gesamtwerte von erfolgreichen, fehlgeschlagenen und allgemeinen Treffern zu verfolgen. Auf diese Weise können Sie Veränderungen der Agentenaktivität und -leistung im Zeitverlauf überwachen. Sie können auch den Mauszeiger über das Diagramm bewegen, um die Datenentwicklung über den wöchentlichen Zeitrahmen hinweg zu sehen.

![Agentische Traffic-Trends](/help/dashboards/assets/ag-trends.png)

## Top- und Bottom-Mover {#top-bottom-movers}

Die Ansicht „Top-Mover“ und „Bottom Mover“ zeigen URLs mit den größten wöchentlichen Änderungen im agenten Traffic - Besuche oder Treffer von KI-Systemen, die auf Ihre Inhalte zugreifen. **Top Movers** zeigt Seiten, die an Sichtbarkeit oder Interaktion gewinnen, während **Bottom Movers** die URLs mit den stärksten Rückgängen anzeigt. Auf diese Weise können Sie schnell erkennen, welche Inhalte nach oben tendieren, was möglicherweise Aufmerksamkeit erfordert, und wo sich KI-gesteuerte Erkennungsmuster verschieben.

![Top und Bottom Mover](/help/dashboards/assets/movers.png)

## Benutzeragent- und URL-Leistungsanalyse {#user-url-performance}

Die Ansichten Benutzeragent und URL-Leistungsanalyse bieten weitere Datenaufschlüsselungen zur Interaktion von Crawlern und Chatbots mit Ihrer Site. Klicken Sie auf die Registerkarten unten, um detaillierte Beschreibungen anzuzeigen.

![Benutzeragent- und URL-Leistungsanalyse](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Benutzeragenten-Analyse]

Die Tabelle Benutzeragentenanalyse enthält eine Aufschlüsselung des Traffics nach Seitentyp und Agententyp (z. B. Crawler im Vergleich zu Chatbots). Auf diese Weise ist es einfach zu verstehen, welche KI-Agenten welche Teile Ihrer Site durchsuchen. Es umfasst die folgenden Kategorien:

* **Seitentyp** - Der Seitentyp.
* **Agent Type** - Der KI-Agent, der die Seite durchsucht, entweder ein Crawler oder ein Chatbot.
* **Treffer** - Die Gesamtzahl der Anfragen, die von KI-Agenten für diesen bestimmten Seitentyp gestellt wurden.

Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken.

>[!TAB URL-Leistungsanalyse]

Die Tabelle URL-Leistungsanalyse zeigt eine detaillierte Ansicht der einzelnen URLs. Dazu gehören Treffer, eindeutige Agenten, Top-Agenten, Erfolgsraten und Kategorien. Auf diese Weise können Sie hochwertige Seiten identifizieren, Durchforstungslücken erkennen und Inhalte für KI-Engines optimieren. Die URLs werden nach Traffic-Volumen sortiert. Die Tabelle enthält die folgenden Kategorien:

* **URL** - Die untersuchte URL.
* **Treffer insgesamt** - Gesamtzahl der Anfragen, die von KI-Agenten an die URL gesendet wurden.
* **Eindeutige Agenten** - Die Anzahl der verschiedenen KI-Agenten, die auf die URL zugegriffen haben.
* **Top-Agent** - Der KI-Agent, der den meisten Traffic zur URL generiert hat.
* **Top-Agent-**: Der Typ des KI-Agenten, der den meisten Traffic zu dieser URL generiert hat.
* **Erfolgsrate** - Der Prozentsatz erfolgreicher HTTP-Anfragen, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Kategorie** - Die Kategorie, die dem Inhalt Ihrer Seite am ehesten entspricht.
* **Durchschnittliche TTFB (ms)** - Die Zeit bis zum ersten Byte (TTFB) misst die Zeit, die für das erste Byte von Daten benötigt wird, die vom Server empfangen werden (in Millisekunden). Der Durchschnittswert wird auf der Grundlage der Anzahl der Anfragen gewichtet, die jeden Code zurückgeben, und schließt Anfragen aus, die zu Antworten von 5xx geführt haben. Niedrigere Werte bedeuten kürzere Serverreaktionszeiten.
* **Antwort-Codes** - die HTTP-Status-Codes, die für die URL beobachtet werden.

Die URL-Leistungstabelle enthält ein Suchfeld für den schnellen Zugriff auf URLs. Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken. Sie können auch zusätzliche Details für jede URL anzeigen, indem Sie auf das **Details**-Symbol am Ende jeder Zeile klicken.

![URL-Details](/help/dashboards/assets/details.png)

Die Ansicht „URL-Details“ bietet ein ganzheitliches Verständnis der Leistung einer Seite, das zeigt, wie oft sie zitiert wird, die Stimmung bei KI-Antworten, wo sie erwähnt wird, die Themen und Eingabeaufforderungen, in denen sie angezeigt wird, und die Trends beim Agent- und Verweisdatenverkehr im Laufe der Zeit.

>[!ENDTABS]

In beiden Tabellen können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabellen in das Reporting für Führungskräfte aufzunehmen.
