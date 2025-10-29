---
title: Empfehlungsverkehr
description: Erfahren Sie, wie Sie mit dem Dashboard für Empfehlungs-Traffic anzeigen können, wie Besucher von externen Plattformen, KI-Zitaten und Verweis-Links zu Ihrer Site gelangen.
feature: Referral Traffic
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---


# Empfehlungsverkehr

Der Verweis-Traffic zeigt an, wie Besucher von externen Plattformen, KI-Zitaten und Verweis-Links zu Ihrer Site gelangen. Es verfolgt und analysiert Traffic-Quellen, Verweismuster und Konversionsmetriken von externen Websites und Plattformen. Auf diese Weise lässt sich erkennen, welche Quellen, Regionen und Seiten den am meisten interagierenden Traffic leiten. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.--> Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Empfehlungsseite](/help/dashboards/assets/referral-traffic.png)

Auf dieser Seite wird Folgendes beschrieben:

* [Setup](#setup)
* [Filter](#filters)
* [Gesamtleistung der Empfehlung](#overall-performance)
* [Top-Verweis-URLs](#top-referrals)
* [Details zum Empfehlungs-Traffic](#traffic-details)

## Setup {#setup}

Bei der ersten Anmeldung kann das Dashboard für den Empfehlungs-Traffic leer erscheinen. Um Ihre Daten anzuzeigen, müssen Sie die [CDN-Protokollweiterleitung](/help/dashboards/customer-configuration.md#cdn-configuration) konfigurieren, indem Sie **Zur Konfiguration wechseln** auswählen.

![Verweiseinrichtung](/help/dashboards/assets/referral-setup1.png)

<!--- 1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM-->

Nach der Aktivierung wird das Dashboard mit Verweisungs-Traffic-Metriken gefüllt.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
* **Platform** - Wählen Sie eine bestimmte Traffic-Quelle wie Google, OpenAI oder Social Media aus.
* **Seitenabsicht** - Filtern des Verweisdatenverkehrs nach der Benutzerabsicht.
* **Channel Source** - Filtern nach der Kanalquelle. Zu den Optionen gehören: LLMs, verdiente, bezahlte oder gemischte Empfehlungskanäle.
* **Gerätetyp** - Analysiert den Traffic anhand des Gerätetyps des Besuchers, entweder Desktop, Mobilgerät oder alle Geräte.
  **Region** - Verweismuster über verschiedene Regionen hinweg anzeigen.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Gesamtleistung der Empfehlung {#overall-performance}

Das Dashboard zeigt die Gesamtleistung der Empfehlung durch die Anzeige von Schlüsselmetriken an, darunter:

* **Total Referral Traffic** - Der gesamte Empfehlungs-Traffic aus allen Quellen.
* **Empfehlungs-Traffic von LLMs** - Der gesamte Empfehlungs-Traffic von LLMs.
* **Einverständnisrate** - Der Prozentsatz der Besucherinnen und Besucher, die eine Einverständnisaufforderung akzeptieren.
* **Absprungrate** - Der Prozentsatz der Sitzungen aus Empfehlungsquellen, die kein Interaktionsereignis hatten.

![Empfehlungsseite](/help/dashboards/assets/referral-traffic.png)

Neben den oben vorgestellten allgemeinen Leistungsmetriken gibt es drei zusätzliche Bedienfelder, die die Traffic-Verteilung auf verschiedene Märkte, Verweisquellen und Seitenabsichtskategorien anzeigen <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->

<!--## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)-->

## Details zu Empfehlungsquellen und URL-Leistungsanalyse {#traffic-details}

Die Tabellen Details zu Verweisquellen und URL-Leistungsanalyse helfen Ihnen dabei, sowohl das Traffic-Volumen als auch die Qualität zu bewerten. Klicken Sie auf die einzelnen Registerkarten unten, um weitere Details anzuzeigen:

![Details zum Empfehlungs-Traffic](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Details zu Empfehlungsquellen]

Die Ansicht Details zu Verweisquellen enthält Traffic, der von verschiedenen Plattformen wie OpenAI, Microsoft, Google und Perplexity stammt. Es werden Schlüsselmetriken wie Besuche, Absprungrate und Kanaltyp angezeigt, damit Sie verstehen können, welche KI- und Suchquellen den meisten interaktiven Traffic zu Ihrer Site leiten.

* **Source** - Die Quelle des Verweisdatenverkehrs.
* **Besuche** - Die Gesamtzahl der Besuche für jede Quelle.
* **Absprungrate** - Der Prozentsatz der Sitzungen von der Empfehlungsquelle, die kein Interaktionsereignis hatten.
* **channel** - der Kanal für die Quelle, entweder verdient, bezahlt oder beides.

>[!TAB URL-Leistungsanalyse]

Die Ansicht URL-Leistungsanalyse listet die leistungsstärksten Seiten auf, basierend auf dem Verweisdatenverkehr von LLMs und anderen Quellen. Es werden Metriken wie Traffic, Absprungrate, Einverständnisrate und Seitenabsicht hervorgehoben, damit Sie identifizieren können, welche Seiten die meisten interaktiven Besucher von KI-gesteuerten Empfehlungen anziehen und binden. Die Tabelle verfügt über ein Suchfeld für den schnellen Zugriff auf Themen.

>[!ENDTABS]

In beiden Tabellen können Sie die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabellen in das Reporting für Führungskräfte aufzunehmen. Darüber hinaus können Sie für beide Tabellen anpassen, welche Metriken angezeigt werden, indem Sie auf die Schaltfläche **Spalten konfigurieren** klicken.
