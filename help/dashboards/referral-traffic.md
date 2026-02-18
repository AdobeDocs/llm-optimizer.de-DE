---
title: Referral Traffic
description: Erfahren Sie, wie Sie mit dem Dashboard „Referral Traffic“ anzeigen können, wie Besuchende über externe Plattformen, KI-Zitierungen und Referenz-Links auf Ihre Site gelangen.
feature: Referral Traffic
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: ht
source-wordcount: '605'
ht-degree: 100%

---


# Referral Traffic

Unter „Referral Traffic“ sehen Sie, wie Besucherinnen und Besucher aus externen Plattformen, KI-Zitierungen und Referenz-Links auf Ihre Site gelangen. Hier werden Traffic-Quellen, Referenzmuster und Konversionsmetriken von externen Websites und Plattformen nachverfolgt und analysiert. So erkennen Sie, welche Quellen, Regionen und Seiten den Traffic mit den meisten Interaktionen fördern. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.-->Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

![Seite „Referral Traffic“](/help/dashboards/assets/referral-traffic.png)

Diese Seite beschreibt Folgendes:

* [Einrichtung](#setup)
* [Filter](#filters)
* [Referenzleistung insgesamt](#overall-performance)
* [Top-Referenz-URLs](#top-referrals)
* [Details zum Referral Traffic](#traffic-details)

## Einrichtung {#setup}

Bei der ersten Anmeldung kann das Dashboard „Referral Traffic“ leer angezeigt werden. Damit Daten angezeigt werden, müssen Sie die [CDN-Protokollweiterleitung](/help/dashboards/customer-configuration.md#cdn-configuration) konfigurieren, indem Sie **Zur Konfiguration wechseln** auswählen.

![Einrichtung von Referral Traffic](/help/dashboards/assets/referral-setup1.png)

<!--- 1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM-->

Nach der Aktivierung wird das Dashboard mit Referral-Traffic-Metriken gefüllt.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** – Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel die letzten 4 Wochen. Sie können den Zeitraum auch mit der Option **Benutzerdefinierte Wochen** anpassen.
* **Plattform** – Wählen Sie eine bestimmte Traffic-Quelle wie Google, OpenAI oder Social Media aus.
* **Seitenabsicht** – Filtern Sie den Referral Traffic nach Benutzerabsicht.
* **Kanalquelle** – Filtern Sie nach der Kanalquelle. Zu den Optionen gehören LLMs, verdiente, bezahlte oder gemischte Referenzkanäle.
* **Gerätetyp** – Analysieren Sie den Traffic anhand des Gerätetyps der Besuchenden, entweder Desktop, Mobilgerät oder alle Geräte.
  **Region** – Zeigen Sie Referenzmuster über verschiedene Regionen hinweg an.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden**, um Ihre Auswahl auf das Dashboard anzuwenden.

## Referenzleistung insgesamt {#overall-performance}

Das Dashboard zeigt die Gesamtleistung der Referenzen anhand von Schlüsselmetriken an, darunter die folgenden:

* **Referral Traffic insgesamt** – Der gesamte Referral Traffic aus allen Quellen.
* **Referral Traffic von LLMs** – Der gesamte Referral Traffic aus LLMs.
* **Einverständnisrate** – Der Prozentsatz der Besuchenden, die eine Einverständnisaufforderung akzeptieren.
* **Absprungrate** – Der Prozentsatz der Sitzungen aus Referenzquellen, die kein Interaktionsereignis hatten.

![Seite „Referral Traffic“](/help/dashboards/assets/referral-traffic.png)

Neben den oben vorgestellten allgemeinen Leistungsmetriken gibt es drei zusätzliche Panels, die die Traffic-Verteilung auf verschiedene Märkte, Referenzquellen und Seitenabsichtskategorien anzeigen <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->

<!--## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)-->

## Details zu Referenzquellen und URL-Leistungsanalyse {#traffic-details}

Die Tabellen „Details zu Referenzquellen“ und „URL-Leistungsanalyse“ helfen Ihnen dabei, sowohl das Traffic-Volumen als auch die Traffic-Qualität zu bewerten. Klicken Sie auf die einzelnen Registerkarten unten, um weitere Details anzuzeigen:

![Details zum Referral Traffic](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Details zu Referenzquellen]

Die Ansicht „Details zu Referenzquellen“ enthält Traffic, der aus verschiedenen Plattformen wie OpenAI, Microsoft, Google und Perplexity stammt. Sie zeigt Schlüsselmetriken wie Besuche, Absprungrate und Kanaltyp an, damit Sie analysieren können, welche KI- und Suchquellen den meisten interaktiven Traffic auf Ihre Site leiten.

* **Quelle** – Die Quelle des Referral Traffics.
* **Besuche** – Die Gesamtzahl der Besuche für jede Quelle.
* **Absprungrate** – Der Prozentsatz der Sitzungen aus der Referenzquelle, die kein Interaktionsereignis hatten.
* **Kanal** – Der Kanal für die Quelle, entweder verdient, bezahlt oder beides.

>[!TAB URL-Leistungsanalyse]

Die Ansicht „URL-Leistungsanalyse“ listet die leistungsstärksten Seiten auf, basierend auf dem Referral-Traffic-Volumen aus LLMs und anderen Quellen. Metriken wie Traffic, Absprungrate, Einverständnisrate und Seitenabsicht werden hervorgehoben, damit Sie erkennen können, welche Seiten die Besuchenden mit den meisten Interaktionen aus KI-gesteuerten Referenzen anziehen und binden. Die Tabelle verfügt über ein Suchfeld für den schnellen Zugriff auf Themen.

>[!ENDTABS]

In beiden Tabellen können Sie mit der Option **Exportieren** die CSV-Datei der Tabelle herunterladen und die Erkenntnisse mit Ihrem Team teilen oder die Tabellen in das Reporting für Führungskräfte aufnehmen.Darüber hinaus können Sie in beiden Tabellen mit der Schaltfläche **Spalten konfigurieren** anpassen, welche Metriken angezeigt werden.
