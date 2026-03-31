---
title: Adobe Analytics-Integration
description: Erfahren Sie, wie Sie Adobe Analytics mit LLM Optimizer verbinden, um die KI-gesteuerte Erkennung, Website-Interaktion und Geschäftsergebnisse im Referral Traffic-Dashboard zu messen.
feature: Referral Traffic
source-git-commit: e7c9bc1d40267dc92608baa005f85f4be21cfda1
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 4%

---


# Adobe Analytics-Integration

Die Adobe Analytics-Integration verbindet LLM Optimizer mit den Adobe Analytics-Daten Ihres Unternehmens, damit Sie messen können, wie die KI-gesteuerte Erkennung in echte Website-Interaktion und Geschäftsergebnisse übersetzt wird. Nach Abschluss des Integrationsprozesses sind die Daten im Dashboard **Referral Traffic** auf der Registerkarte **Geschäftsauswirkungen** verfügbar.

Durch die Verknüpfung von Analysedaten mit Einblicken in die KI-Sichtbarkeit hilft Ihnen LLM Optimizer beim Nachverfolgen:

* Benutzerinteraktion auf KI-referenzierten Seiten.
* Konversionssignale verknüpft mit KI-Discovery-Journey.
* Auswirkungen von GEO-Optimierungen auf die Leistung.

Diese Integration schließt die Lücke zwischen der Messung der KI-Sichtbarkeit und der Analyse der Geschäftsleistung. Teams können jetzt nicht nur sehen, wo die Marke in KI-Antworten angezeigt wird, sondern auch, was passiert, nachdem Benutzer ankommen.

## Verfügbarkeit {#availability}

>[!IMPORTANT]
>
>Die Adobe Analytics-Integration ist im kostenpflichtigen LLM Optimizer-Angebot enthalten. Kunden, die die kostenlose Testversion verwenden, können Adobe Analytics erst dann verbinden, wenn sie ein kostenpflichtiges Upgrade erhalten haben.

## Adobe Analytics mit dem Referral Traffic-Dashboard verbinden {#connect}

Der Verbindungsfluss beginnt wie folgt vom [Referral Traffic](/help/dashboards/referral-traffic.md)-Dashboard:

1. Öffnen Sie das Dashboard [Referral Traffic](/help/dashboards/referral-traffic.md). Die Standardansicht lautet **Traffic Insights**.

   ![Referral Traffic-Dashboard, Registerkarte „Traffic-Insights“](/help/dashboards/assets/aa-integration-01-referral-traffic-traffic-insights.png)

1. Wählen Sie die Registerkarte **Geschäftsauswirkungen** aus. Wenn kein Analytics-Anbieter verbunden ist, wird ein Banner angezeigt: **Verbinden, um geschäftliche Auswirkungen zu sehen**, mit **Mit Analytics verbinden**.

   ![Registerkarte „Geschäftsauswirkungen“ mit „Mit Analytics verbinden“](/help/dashboards/assets/aa-integration-02-business-impact-connect.png)

1. Wählen Sie **Mit Analytics verbinden** aus. Dadurch wird das Dashboard [Kundenkonfiguration](/help/dashboards/customer-configuration.md) auf der Registerkarte **Analytics** geöffnet.

   ![Kundenkonfiguration, Registerkarte „Analytics“](/help/dashboards/assets/aa-integration-03-analytics-tab.png)

1. Geben **unter** die Werte **Client-ID** und **Client-Geheimnis** ein und klicken Sie dann auf **Überprüfen und fortfahren**. Beachten Sie Folgendes:

   * **Überprüfen und fortfahren** ist nur verfügbar, wenn beide Felder ausgefüllt sind.
   * Nach erfolgreicher Überprüfung werden die Report Suites geladen.
   * Verwenden Sie **Client-ID** und **Client-Geheimnis** eines [technischen Kontos](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/), das Zugriff auf die benötigte Report Suite hat.

   ![Analytics-Anmeldedaten und Überprüfen und Fortfahren](/help/dashboards/assets/aa-integration-04-credentials.png)

1. Wählen **unter &quot;**&quot; eine **Report Suite**.

   Wenn eine Report Suite ausgewählt wird, lädt LLM Optimizer die für diese Suite verfügbaren **Seiten** URL-Dimension).

   ![Report Suite ausgewählt und Dimensionen werden geladen](/help/dashboards/assets/aa-integration-05-report-suite.png)

1. Wählen Sie eine **Seiten-URL** Dimension (Suite-spezifische Dimensionsliste) aus und klicken Sie dann auf **Speichern und aktivieren**.

   * **Seiten-URL Dimension** bleibt deaktiviert, bis eine Report Suite ausgewählt und Dimensionen geladen wurden.
   * **Speichern und aktivieren** ist erst verfügbar, nachdem Sie eine Seiten-URL-Dimension ausgewählt haben.

   ![Dimension Seiten-URL und Speichern und aktivieren](/help/dashboards/assets/aa-integration-06-page-url-dimension.png)

1. Nach dem Speichern sollte die Konfiguration den Status **Verbunden** anzeigen. Sie können mit „Zum Referral Traffic-Dashboard wechseln **zum Referral Traffic-Dashboard**. In **Referral Traffic** sollte auf der Registerkarte **Geschäftsauswirkungen** der Status als „Mit Adobe Analytics **&quot;**.

   ![Verbindung zu Adobe Analytics in Konfiguration und Geschäftsauswirkungen](/help/dashboards/assets/aa-integration-07-connected.png)

### Nach dem Verbinden {#after-connect}

* LLM Optimizer füllt die **letzten vier vollen Kalenderwochen** und die **aktuelle Kalenderwoche bis heute** auf.
* Nach der Aufstockung werden die Daten **täglich** mit einem Pull des **ganzen Vortags** aktualisiert.

>[!NOTE]
>
>Die Aufstockung kann einige Stunden dauern.

## Funktionsweise {#how-it-works}

### Konfiguration

Während des Setups definieren Sie, welche Report Suite- und Seitendimension LLM Optimizer für die Adobe Analytics-Aufnahme verwendet. Die Seitendimension kann je nach Report Suite die standardmäßige `variables/page` oder eine benutzerdefinierte `eVar` sein.

### So wird LLM-Traffic identifiziert

Der von LLM stammende Traffic wird mithilfe von Adobe Analytics [Referrer-Typ - Conversational AI-Tools](https://experienceleague.adobe.com/de/docs/analytics/components/dimensions/referrer-type#conversational-ai-tools) identifiziert.

### Aufgenommene Daten {#data-ingested}

Die folgenden Daten werden von LLM Optimizer aufgenommen:

**Dimensionen**

* Referrer-Domain
* Werbetyp
* Land
* Gerätetyp
* Ausgewählte Seitendimension

**Metriken**

* Seitenansichten
* Besuche
* Besuchende
* Einträge
* Ausstiege
* Absprünge
* Einzelseitenbesuche
* Verbrachte Zeit
* Warenkörbe
* Hinzufügungen zum Warenkorb
* Entnahmen aus Warenkorb
* Warenkorbansichten
* Checkouts
* Bestellungen
* Umsatz
* Einheiten

### Verwendung dieser Daten durch LLM Optimizer

Dieser Datensatz ermöglicht LLM Optimizer Insights für:

* LLM-Traffic-Leistung auf Seitenebene.
* Referrer-Leistung über LLM-Quellen hinweg.
* Trends auf regionaler und Geräteebene.
* Nachgelagerte Commerce-Ergebnisse.

## Häufig gestellte Fragen {#faq}

F.: Ist die Adobe Analytics-Integration während der Testphase verfügbar?

Nein. Die Integration ist nur für Kunden von Paid LLM Optimizer verfügbar.

F: Welche Daten werden erfasst oder gespeichert?

Siehe das obige [Aufgenommene Daten](#data-ingested). LLM Optimizer arbeitet mit aggregierten Metriken aus den von Ihrem Unternehmen autorisierten Adobe Analytics-APIs und nicht mit den rohen Daten auf Trefferebene.

F: Wie werden Daten aufgenommen?

Ihr Unternehmen autorisiert LLM Optimizer, Adobe Analytics-APIs abzufragen. An LLM-Quellen angepasste Referral Traffic werden über diese APIs genutzt.

F: Wie oft werden die Daten aktualisiert?

Daten werden aktualisiert **täglich** (voller Vortag nach Abschluss der Aufstockung).

F.: Werden in LLM Optimizer Daten auf Trefferebene gespeichert?

Nein. Nur **aggregierte** Metriken werden zum Verständnis von Traffic-Mustern und -Trends verwendet.

F.: Werden vollständige URLs, Abfragezeichenfolgen oder Seiteninhalte gespeichert?

Vollständige URLs, die für die ausgewählte Seitendimension verwendet werden, können aufgenommen werden. Abfragezeichenfolgen und Seiteninhalte werden für diese Integration nicht aufgenommen.

F.: Werden Benutzerkennungen (ECID, IP-Adresse, Cookie-IDs) gespeichert?

Nein.

F: Wie lange werden Daten aufbewahrt?

Beachten Sie, dass sich die Aufbewahrungs-Policys ändern können. Derzeit werden Daten unbegrenzt gespeichert.

F.: Werden Daten während der Übertragung und im Ruhezustand verschlüsselt?

Derzeit werden die Daten während der Übertragung nicht im Ruhezustand verschlüsselt. Dies kann sich in zukünftigen Updates ändern.

F.: Werden historische Daten aufgestockt?

Ja. Nach einer erfolgreichen Einrichtung werden die letzten vier vollen Kalenderwochen und die aktuelle Kalenderwoche aufgestockt. Siehe auch [Nach dem Verbinden](#after-connect).
