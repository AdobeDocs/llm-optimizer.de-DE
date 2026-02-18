---
title: Agent-basierter Traffic
description: Erfahren Sie, wie Sie mit dem Dashboard „Agent-basierter Traffic“ sehen können, wie AI Agents mit Ihrer Site interagieren.
feature: Agentic Traffic
source-git-commit: 26926f3ed4df3a408b74b0208f0d1eb064b97d28
workflow-type: ht
source-wordcount: '1316'
ht-degree: 100%

---


# Agent-basierter Traffic {#agentic-traffic}

Das Dashboard „Agent-basierter Traffic“ zeigt, wie AI Agents (Crawler und Chatbots) mit Ihrer Site interagieren. Mithilfe dieser Ansicht können Sie die Gesamtzahl der Anfragen und allgemeine leistungsbezogene Metriken verfolgen. Sie können auch die Verteilung des Traffics auf Märkte, Kategorien, Seiten und Agents anzeigen. Die von diesem Dashboard verwendeten Daten stammen aus den CDN-Protokollen. Daher müssen Sie die **CDN-Protokollweiterleitung** konfigurieren, um Metriken anzeigen zu können. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Traffic-Verteilung](/help/dashboards/assets/ag-main.png)

Diese Seite beschreibt Folgendes:

* [Filter](#filters)
* [CDN-Einrichtung](#cdn-setup)
* [Traffic-Verteilung](#traffic-distribution)
* [Trends bei Agent-basiertem Traffic](#agentic-trends)
* [Elemente mit Zunahme und Abnahme](#top-bottom-movers)
* [Benutzer-Agent- und URL-Leistungsanalyse](#user-url-performance)

## CDN-Protokollweiterleitung {#cdn-setup}

Ohne **CDN-Protokollweiterleitung** bleibt das Dashboard „Agent-basierter Traffic“ leer. Damit Agent-basierte Interaktionen angezeigt werden können, müssen Sie die **CDN-Protokollweiterleitung** konfigurieren.  Bei der ersten Anmeldung wird eine Meldung angezeigt, wie in der Abbildung unten dargestellt.

![CDN-Einrichtung](/help/dashboards/assets/ag-log-forward1.png)

Wählen Sie **Zur Konfiguration wechseln** aus. Sie navigieren dann automatisch zur Registerkarte **CDN-Konfiguration** im [Dashboard „Kundenkonfiguration“](/help/dashboards/customer-configuration.md).

![CDN-Einrichtung: Integrieren](/help/dashboards/assets/ag-log-forward2.png)

Wählen Sie auf dieser Registerkarte die Option **CDN integrieren** aus. Daraufhin wird das Fenster mit CDN-Anbietern angezeigt.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->
Im Fenster **CDN-Anbieter integrieren**:

1. Wählen Sie Ihren CDN-Anbieter aus (z. B. „Akamai“, „Von Adobe verwaltetes Fastly“, „Fastly“, „AWS Cloudfront“, „Azure CDN“, „Cloudflare“ oder „Sonstige“).
2. Klicken Sie auf **Integrieren**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an llmo-now@adobe.com wenden, um Hilfe zu erhalten.

Nach der Aktivierung werden Protokolle aufgenommen und Metriken wie Gesamtanzahl der Agent-basierten Interaktionen, Erfolgsrate, Treffer nach Markt, Benutzer-Agent-Analysen und Leistung auf URL-Ebene im Dashboard angezeigt.

LLM Optimizer verarbeitet eine Teilmenge der Felder aus den CDN-Protokollen. Auch wenn die Rohnamen der Protokollfelder je nach CDN-Anbieter variieren, werden sie normalisiert und wie folgt dargestellt:

* URL (nur Pfad)
* Benutzer-Agent
* Status-Code
* Referrer-Header
* Host-Header
* Zeit bis zum ersten Byte (TTFB)
* Anfragemethode
* Zeitstempel
* Inhaltstyp

Diese normalisierten Felder werden in der Agent-basierten Ansicht angezeigt. Im Dashboard [Referral Traffic](/help/dashboards/referral-traffic.md) werden CDN-Protokolle verwendet, um Seitentreffermetriken anzuzeigen. In keiner Phase der CDN-Protokollaufnahme oder der nachfolgenden Datenverarbeitung werden personenbezogene Daten (PII) verarbeitet oder gespeichert.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** – Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel die letzten 4 Wochen. Sie können den Zeitraum auch mit der Option **Benutzerdefinierte Wochen** anpassen.
* **Kategorie** – Filtert die angezeigten Ergebnisse nach vordefinierten Kategorien oder benutzerdefinierten Kategorien.
* **Plattform** – Wählen Sie die zu analysierende KI-Engine aus.
* **Agent-Typ** – Filtern Sie nach dem Typ des AI Agents, der mit Ihrer Site interagiert hat. Sie können nach Crawlern, Chatbots oder allen Agents filtern.
* **Erfolgsrate** – Filtern Sie nach Interaktionsqualität (hoch, mittel oder niedrig). Diese Metrik steht für den Prozentsatz erfolgreicher HTTP-Anfragen, einschließlich direkter erfolgreicher Antworten (Status-Codes „2xx“) und Umleitungen (Status-Codes „3xx“).
* **Inhaltstyp** – Zeigen Sie Agent-basierte Interaktionen für verschiedene Inhaltstypen wie HTML, PDF usw. an.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden**, um Ihre Auswahl auf das Dashboard anzuwenden.

## Traffic-Verteilung {#traffic-distribution}

Die Ansicht „Traffic-Verteilung“ zeigt, wie der Agent-Traffic auf Märkte, Kategorien und Seitentypen verteilt wird. So können Sie mit dieser Ansicht ermitteln, auf welche Regionen, Produktbereiche oder Inhaltsformate AI Agents bei der Interaktion mit Ihrer Site am häufigsten zugreifen.

![Traffic-Verteilung](/help/dashboards/assets/ag-main.png)

Oben auf der Seite gibt es drei Schlüsselmetriken, die Sie beachten müssen:

* **Agent-Interaktionen** – Diese Metrik stellt die Gesamtzahl der Anfragen dar, die von AI Agents an Ihre Website gesendet wurden. Hierzu zählt der gesamte Traffic von Suchmaschinen und Chatbots und anderer nicht-menschlicher Traffic.
* **Erfolgsrate** – Diese Metrik stellt den Prozentsatz erfolgreicher HTTP-Anfragen dar, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Durchschnittlicher TTFB** – Die durchschnittliche Zeit bis zum ersten Byte (TTFB) gibt an, wie lange es dauert, bis das erste Daten-Byte vom Server empfangen wird. Der Durchschnittswert wird auf der Grundlage der Anzahl der Anfragen gewichtet, die jeden Code zurückgeben, und schließt Anfragen aus, die zu Antworten des Typs „5xx“ geführt haben. Niedrigere Werte bedeuten kürzere Server-Antwortzeiten.

Für jede Schlüsselmetrik zeigen Trend-Indikatoren an, wie sich die Werte im Zeitverlauf verglichen mit dem vorherigen Zeitraum ändern.

## Trends bei Agent-basiertem Traffic {#agentic-trends}

Verwenden Sie das Diagramm „Trends bei Agent-basiertem Traffic“, um die wöchentlichen Gesamtwerte von erfolgreichen und fehlgeschlagenen Treffern und von Treffern insgesamt zu verfolgen. Auf diese Weise können Sie Veränderungen der Agent-Aktivität und -Leistung im Zeitverlauf überwachen. Sie können auch den Mauszeiger über das Diagramm bewegen, um die Datenentwicklung im wöchentlichen Zeitrahmen zu sehen.

![Trends bei Agent-basiertem Traffic](/help/dashboards/assets/ag-trends.png)

## Elemente mit Zunahme und Abnahme {#top-bottom-movers}

Die Ansicht der Elemente mit Zunahme und Abnahme zeigt URLs mit den größten wöchentlichen Änderungen beim Agent-basierten Traffic, also bei Besuchen oder Treffern von KI-Systemen, die auf Ihre Inhalte zugreifen. **Zunahme** zeigt Seiten, deren Sichtbarkeit oder Interaktionen zunehmen, während **Abnahme** die URLs mit den stärksten Rückgängen anzeigt. Auf diese Weise können Sie schnell erkennen, welche Inhalte nach oben tendieren, was möglicherweise Aufmerksamkeit erfordert und wo sich KI-gesteuerte Erkennungsmuster verschieben.

![Elemente mit Zunahme und Abnahme](/help/dashboards/assets/movers.png)

## Benutzer-Agent- und URL-Leistungsanalyse {#user-url-performance}

Die Ansichten „Benutzer-Agent-Analyse“ und „URL-Leistungsanalyse“ bietet weitere Datenaufschlüsselungen zu Interaktionen von Crawlern und Chatbots mit Ihrer Site. Klicken Sie auf die Registerkarten unten, um detaillierte Beschreibungen anzuzeigen.

![Benutzer-Agent- und URL-Leistungsanalyse](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Benutzer-Agent-Analyse]

Die Tabelle „Benutzer-Agent-Analyse“ enthält eine Aufschlüsselung des Traffics nach Seitentyp und Agent-Typ (z. B. Crawler oder Chatbots). So können Sie einfach erkennen, welche AI Agents welche Teile Ihrer Site crawlen. Sie enthält die folgenden Kategorien:

* **Seitentyp** – Der Typ der Seite.
* **Agent-Typ** – Der AI Agent, der die Seite crawlt, entweder ein Crawler oder ein Chatbot.
* **Treffer** – Die Gesamtzahl der Anfragen, die von AI Agents für diesen bestimmten Seitentyp gestellt wurden.

Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken.

>[!TAB URL-Leistungsanalyse]

Die Tabelle „URL-Leistungsanalyse“ zeigt eine detaillierte Ansicht der einzelnen URLs. Dazu gehören Treffer, eindeutige Agents, Top-Agents, Erfolgsraten und Kategorien. Dadurch können Sie hochwertige Seiten identifizieren, Lücken beim Crawling erkennen und Inhalte für KI-Engines optimieren. Die URLs werden nach Traffic-Volumen sortiert. Die Tabelle enthält die folgenden Kategorien:

* **URL** – Die untersuchte URL.
* **Treffer insgesamt** – Die Gesamtzahl der Anfragen von AI Agents an diese URL.
* **Eindeutige Agents** – Die Anzahl der verschiedenen AI Agents, die auf diese URL zugegriffen haben.
* **Top-Agent** – Der AI Agent, der den meisten Traffic für diese URL generiert hat.
* **Top-Agent-Typ** – Typ des AI-Agents, der den meisten Traffic für diese URL generiert hat.
* **Erfolgsrate** – Der Prozentsatz erfolgreicher HTTP-Anfragen, einschließlich direkter erfolgreicher Antworten und Weiterleitungen.
* **Kategorie** – Die Kategorie, die dem Inhalt Ihrer Seite am ehesten entspricht.
* **Durchschnittlicher TTFB** – Die Zeit bis zum ersten Byte gibt an, wie lange es dauert (in Millisekunden), bis das erste Daten-Byte vom Server empfangen wird. Der Durchschnittswert wird auf der Grundlage der Anzahl der Anfragen gewichtet, die jeden Code zurückgeben, und schließt Anfragen aus, die zu Antworten des Typs „5xx“ geführt haben. Niedrigere Werte bedeuten kürzere Server-Antwortzeiten.
* **Antwort-Codes** – Die HTTP-Status-Codes, die für die URL beobachtet werden.

Die Tabelle mit der URL-Leistung enthält ein Suchfeld für den schnellen Zugriff auf URLs. Sie können anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken. Sie können auch zusätzliche Details für jede URL anzeigen, indem Sie am Ende der gewünschten Zeile auf das Symbol **Details** klicken.

![URL-Details](/help/dashboards/assets/details.png)

Die Ansicht „URL-Details“ bietet einen ganzheitlichen Blick auf die Leistung einer Seite. Sie können erkennen, wie oft die Seite zitiert wird, wie bei Erwähnungen das Sentiment von KI-Antworten ausfällt, in welchen Themen und Prompts die Seite auftaucht und wie die zeitlichen Trends bei Agent-basiertem und Referral Traffic aussehen.

>[!ENDTABS]

In beiden Tabellen können Sie mit der Option **Exportieren** die `.csv`-Datei der Tabelle herunterladen und die Erkenntnisse mit Ihrem Team teilen oder die Tabellen in das Reporting für Führungskräfte aufnehmen.
