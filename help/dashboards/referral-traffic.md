---
title: Empfehlungsverkehr
description: Erfahren Sie, wie Sie mit dem Dashboard für Empfehlungs-Traffic anzeigen können, wie Besucher von externen Plattformen, KI-Zitaten und Verweis-Links zu Ihrer Site gelangen.
source-git-commit: e8ea9ae0d6592ea3d1e9945ec117f852112ba9d7
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---


# Empfehlungsverkehr

Der Verweis-Traffic zeigt an, wie Besucher von externen Plattformen, KI-Zitaten und Verweis-Links zu Ihrer Site gelangen. Es verfolgt und analysiert Traffic-Quellen, Verweismuster und Konversionsmetriken von externen Websites und Plattformen. Auf diese Weise lässt sich erkennen, welche Quellen, Regionen und Seiten den am meisten interagierenden Traffic leiten. Die Daten werden entweder aus den CDN-Protokollen oder dem AEM Operational Telemetry **(Link hinzufügen)**. Beide Quellen schützen die Privatsphäre und erfassen keine personenbezogenen Benutzerdaten.

Es gibt auch anpassbare Filter, mit denen Sie die angezeigten Daten verfeinern können.

Auf dieser Seite wird Folgendes beschrieben:

* [Setup](#setup)
* [Filter](#filters)
* [Gesamtleistung der Empfehlung](#overall-performance)
* [Top-Verweis-URLs](#top-referrals)
* [Details zum Empfehlungs-Traffic](#traffic-details)

## Setup {#setup}

Bei der ersten Anmeldung kann das Dashboard für den Empfehlungs-Traffic leer erscheinen. Um Ihre Daten anzuzeigen, müssen Sie einen Anbieter für Empfehlungs-Traffic konfigurieren.

![Verweiseinrichtung](/help/dashboards/assets/referral-setup.png)

1. Wählen Sie Ihre Source aus (entweder CDN-Protokolle oder operative Telemetrie von AEM).
2. Primäre Kontakt-E-Mail eingeben.
3. Klicken Sie auf **Aktivierung anfordern**, um die Datenaufnahme zu aktivieren.

Nach der Aktivierung wird das Dashboard mit Traffic-Metriken für Verweise gefüllt.

## Filter {#filters}

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

**Datumsbereich** - Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel in den letzten 4 Wochen. Sie haben auch die Möglichkeit, den Zeitraum anzupassen, indem Sie die Option **Benutzerdefinierte Wochen** auswählen.
**Platform** - Wählen Sie eine bestimmte Traffic-Quelle wie Google, OpenAI oder Social Media aus.
**Kanal** - Filtern zwischen Kanälen, wie „verdient“ oder „bezahlt“. Wenn Sie einen Mix zwischen den beiden bevorzugen, wählen Sie die Option **Alle Kanäle** aus.
**Channel Source** - Filtern nach der Kanalquelle. Zu den Optionen gehören: Anzeige, Suche, Empfehlung, Video und Social Media. Sie können auch die Option **Alle Plattformen** verwenden, um alle Kanalquellen anzuzeigen.
**Gerätetyp** - Analysiert den Traffic anhand des Gerätetyps des Besuchers, entweder Desktop, Mobilgerät oder alle Geräte.
**Region** - Verweismuster über verschiedene Regionen hinweg anzeigen.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden** um die Auswahl auf das Dashboard anzuwenden.

## Gesamtleistung der Empfehlung {#overall-performance}

Das Dashboard zeigt die Gesamtleistung der Empfehlung durch die Anzeige der folgenden Schlüsselmetriken an:

* **Total Referral Traffic** - Der gesamte Empfehlungs-Traffic aus allen Quellen.
* **Einverständnisrate** - Der Prozentsatz der Besucherinnen und Besucher, die eine Einverständnisaufforderung akzeptieren.
* **Absprungrate** - Der Prozentsatz der Sitzungen aus Empfehlungsquellen, die kein Interaktionsereignis hatten.

![Empfehlungsseite](/help/dashboards/assets/referral-traffic.png)

Neben den oben dargestellten Gesamtleistungsmetriken schlüsselt der Bereich **Top-Regionen** den Traffic nach Geografie auf. Währenddessen zeigt das Bedienfeld **Top-Empfehlungsquellen** die Plattformen an, auf denen die meisten Besuche stattfinden.

## Top-Verweis-URLs {#top-referrals}

Die Liste der Top-Referrer-URLs zeigt die am häufigsten besuchten Seiten Ihrer Site aus Empfehlungen an.

![Top-Referrer-URLs](/help/dashboards/assets/top-url.png)

## Details zum Empfehlungs-Traffic {#traffic-details}

Die Tabelle mit Traffic-Details für Empfehlungen hilft Ihnen, sowohl das Traffic-Volumen als auch die Qualität zu bewerten. Er bietet eine detaillierte Aufschlüsselung nach Quelle, einschließlich der Anzahl der Besuche, der Absprungraten und des Kanaltyps.

![Details zum Empfehlungs-Traffic](/help/dashboards/assets/traffic-details.png)

Die Tabelle enthält die folgenden Kategorien:

**Source** - Die Quelle des Verweisdatenverkehrs.
**Besuche** - Die Gesamtzahl der Besuche für jede Quelle.
**Absprungrate** - Der Prozentsatz der Sitzungen von der Empfehlungsquelle, die kein Interaktionsereignis hatten.
**channel** - der Kanal für die Quelle, entweder verdient, bezahlt oder beides.

Sie können die Option **Exportieren** verwenden, um die CSV-Tabelle herunterzuladen und die Einblicke mit Ihrem Team zu teilen oder die Tabelle Verweisdatenverkehr in das Reporting für Führungskräfte aufzunehmen.
