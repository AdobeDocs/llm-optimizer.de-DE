---
title: Agent-basierter Traffic
description: Erfahren Sie, wie Sie mit dem Dashboard „Agent-basierter Traffic“ sehen können, wie AI Agents mit Ihrer Site interagieren.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:38:14.233Z'
TQID: 'https://experienceleague.adobe.com/4pvsCwqZXkX7xOJWqKge6rkJYaAq27cSjLeTxaA4ysM'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1254
ht-degree: 97%

---


# Agent-basierter Traffic {#agentic-traffic}

Das Dashboard „Agent-basierter Traffic“ zeigt, wie AI Agents (Crawler und Chatbots) mit Ihrer Site interagieren. Mithilfe dieser Ansicht können Sie die Gesamtzahl der Anfragen und allgemeine leistungsbezogene Metriken verfolgen. Sie können auch die Verteilung des Traffics auf Märkte, Kategorien, Seiten und Agents anzeigen. Die von diesem Dashboard verwendeten Daten stammen aus den CDN-Protokollen. Daher müssen Sie die **CDN-Protokollweiterleitung** konfigurieren, um Metriken anzeigen zu können. Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können. Navigieren Sie zu **Agent Traffic** und wählen Sie die Site aus, für die Sie die Agentenverkehrseinblicke anzeigen möchten.

![Agent-basierter Traffic – Site-Auswahl (markenorientierte Oberfläche)](/help/assets/brand-centric-experience/agentic-traffic-dashboard.png)

<!-- ![Traffic Distribution](/help/dashboards/assets/ag-main.png)-->

Diese Seite beschreibt Folgendes:

* [Filter](#filters)
* [CDN-Einrichtung](#cdn-setup)
* [Traffic-Verteilung](#traffic-distribution)
* [Trends bei Agent-basiertem Traffic](#agentic-trends)
* [Elemente mit Zunahme und Abnahme](#top-bottom-movers)
* [Benutzer-Agent- und URL-Leistungsanalyse](#user-url-performance)

## CDN-Protokollweiterleitung {#cdn-setup}

Ohne **CDN-Protokollweiterleitung** bleibt das Dashboard „Agent-basierter Traffic“ leer. Damit Agent-basierte Interaktionen angezeigt werden können, müssen Sie die **CDN-Protokollweiterleitung** konfigurieren.

Sie können Informationen zur CDN-Protokollweiterleitung hinzufügen, indem Sie zu **Brands Management** navigieren und auf die **CDN**-Beschriftung klicken.

![Markenverwaltung – CDN-Protokollweiterleitung](/help/assets/brand-centric-experience/brands-management-cdn.png)

Einzelheiten zur Protokollweiterleitung bei Verwendung eines kundenseitig verwalteten CDN (BYOCDN) finden Sie unter [BYOCDN-Protokollweiterleitung – Überblick](/help/overview/log-forwarding/log-forwarding-overview.md)

LLM Optimizer verarbeitet eine Teilmenge der Felder aus den CDN-Protokollen. Auch wenn die Rohnamen der Protokollfelder je nach CDN-Anbieter variieren, werden sie normalisiert und wie folgt dargestellt:

* URL (Pfad- und Abfrageparameter)
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

Die Ansicht der Elemente mit Zunahme und Abnahme zeigt URLs mit den größten wöchentlichen Änderungen beim Agent-basierten Traffic, also bei Besuchen oder Treffern von KI-Systemen, die auf Ihre Inhalte zugreifen. **Zunahme** zeigt Seiten an, deren Sichtbarkeit oder Interaktionen zunehmen, während **Abnahme** die URLs mit den stärksten Rückgängen anzeigt. Auf diese Weise können Sie schnell erkennen, welche Inhalte nach oben tendieren, was möglicherweise Aufmerksamkeit erfordert und wo sich KI-gesteuerte Erkennungsmuster verschieben.

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
