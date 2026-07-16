---
title: Adobe Analytics-Integration
description: Erfahren Sie, wie Sie Adobe Analytics mit LLM Optimizer verbinden, um KI-gestützte Auffindbarkeit, Site-Interaktion und Geschäftsergebnisse im Dashboard „Referral Traffic“ zu messen.
feature: Referral Traffic
autotag-review: '2026-07-15T16:46:49.693Z'
TQID: 'https://experienceleague.adobe.com/H0p8HV2bf1KuKYqF1ByAF2BpGlb4YScsWDQU5mMkTRY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 950
ht-degree: 92%

---


# Adobe Analytics-Integration

Die Adobe Analytics-Integration verbindet LLM Optimizer mit den Adobe Analytics-Daten Ihrer Organisation, sodass Sie messen können, wie KI-gestützte Erkenntnisse in tatsächliche Website-Interaktion und Geschäftsergebnisse umgesetzt werden. Nach Abschluss des Integrationsprozesses stehen die Daten im Dashboard **Referral Traffic** unter der Registerkarte **Geschäftliche Auswirkungen** zur Verfügung.

Durch die Verknüpfung von Analysedaten mit Erkenntnissen zur KI-Sichtbarkeit hilft Ihnen LLM Optimizer beim Tracking von:

* Benutzerinteraktion auf KI-gestützten Seiten.
* Konversionssignale im Zusammenhang mit KI-Auffindbarkeitsprozessen.
* Auswirkungen von GEO-Optimierungen auf die Leistung.

Diese Integration schließt die Lücke zwischen der Messung der KI-Sichtbarkeit und der Analyse der Performance des Unternehmens. Teams erhalten so nicht nur Erkenntnisse dazu, wo die Marke in KI-Antworten angezeigt wird, sondern auch dazu, was nach dem Ankommen von Benutzenden passiert.

## Verfügbarkeit {#availability}

>[!IMPORTANT]
>
>Die Adobe Analytics-Integration ist im kostenpflichtigen LLM Optimizer-Angebot enthalten. Kundschaften, die die kostenlose Testversion nutzen, können erst dann eine Verbindung zu Adobe Analytics herstellen, wenn sie ein Upgrade auf ein kostenpflichtiges Angebot durchführen.

## Verbinden von Adobe Analytics mit dem Dashboard „Referral Traffic“ {#connect}

Der Verbindungsfluss beginnt im Dashboard [Referral Traffic](/help/dashboards/referral-traffic.md) wie folgt:

1. Öffnen Sie das Dashboard [Referral Traffic](/help/dashboards/referral-traffic.md). Die Standardansicht ist **Traffic-Erkenntnisse**.

   ![Dashboard „Referral Traffic“, Registerkarte „Traffic-Erkenntnisse“](/help/dashboards/assets/aa-integration-01-referral-traffic-traffic-insights.png)

1. Wählen Sie die Registerkarte **Geschäftliche Auswirkungen** aus. Wenn kein Analyseanbieter verbunden ist, wird folgender Banner angezeigt: **Verbinden, um geschäftliche Auswirkungen anzuzeigen**, mit **Mit Analytics verbinden**.

   ![Registerkarte „Geschäftliche Auswirkungen“ mit „Mit Analytics verbinden“](/help/dashboards/assets/aa-integration-02-business-impact-connect.png)

1. Wählen Sie **Mit Analytics verbinden** aus. Dadurch wird das Dashboard [Kundenkonfiguration](/help/dashboards/customer-configuration.md) auf der Registerkarte **Analytics** geöffnet.

   ![Kundenkonfiguration, Registerkarte „Analytics“](/help/dashboards/assets/aa-integration-03-analytics-tab.png)

1. Geben Sie unter **Anmeldedaten** die **Client-ID** und das **Client-Geheimnis** ein und wählen Sie dann **Verifizieren und fortfahren** aus. Bitte beachten Sie Folgendes:

   * **Verifizieren und fortfahren** ist nur verfügbar, wenn beide Felder ausgefüllt sind.
   * Nach erfolgreicher Verifizierung werden die Report Suites geladen.
   * Verwenden Sie die **Client-ID** und das **Client-Geheimnis** eines [technischen Kontos](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/), das Zugriff auf die benötigte Report Suite hat.

   ![Analytics-Anmeldedaten und „Verifizieren und fortfahren“](/help/dashboards/assets/aa-integration-04-credentials.png)

1. Wählen Sie unter **Konfiguration** eine **Report Suite** aus.

   Wenn eine Report Suite ausgewählt wird, lädt LLM Optimizer die für diese Suite verfügbaren Optionen der **Seiten-URL-Dimension**.

   ![Report Suite ist ausgewählt und Dimensionen werden geladen](/help/dashboards/assets/aa-integration-05-report-suite.png)

1. Wählen Sie eine **Seiten-URL-Dimension** (Suite-spezifische Dimensionsliste) aus und klicken Sie dann auf **Speichern und aktivieren**.

   * **Seiten-URL-Dimension** bleibt deaktiviert, bis eine Report Suite ausgewählt und Dimensionen geladen wurden.
   * **Speichern und aktivieren** ist erst verfügbar, nachdem Sie eine Seiten-URL-Dimension ausgewählt haben.

   ![Seiten-URL-Dimension und „Speichern und aktivieren“](/help/dashboards/assets/aa-integration-06-page-url-dimension.png)

1. Nach dem Speichern sollte für die Konfiguration der Status **Verbunden** angzeigt werden. Über **Zum Dashboard „Referral Traffic“** können Sie zum Dashboard „Referral Traffic“ zurückkehren. In **Referral Traffic** sollte auf der Registerkarte **Geschäftliche Auswirkungen** der Status als **Mit Adobe Analytics verbunden** angezeigt werden.

   ![„Mit Adobe Analytics verbunden“ in Konfiguration und „Geschäftliche Auswirkungen“](/help/dashboards/assets/aa-integration-07-connected.png)

### Nach Herstellen der Verbindung {#after-connect}

* LLM Optimizer stockt die **letzten vier vollen Kalenderwochen** und die **aktuelle Kalenderwoche bis heute** auf.
* Nach der Aufstockung werden die Daten **täglich** über einen Abruf des **ganzen Vortags** aktualisiert.

>[!NOTE]
>
>Die Aufstockung kann einige Stunden dauern.

## Siehe Geschäftliche Auswirkungen in Aktion

Die Sichtbarkeit der KI ist nur ein Teil der Geschichte. Um zu verstehen, ob Ihre Optimierungsbemühungen zu Geschäftsergebnissen führen, müssen Sie wissen, was passiert, nachdem Besucher auf Ihrer Site ankommen.

In diesem Video wird die Ansicht **Geschäftsauswirkungen** vorgestellt, die LLM Optimizer mit Adobe Analytics kombiniert, um zu zeigen, wie sich KI-bezogener Traffic in Interaktion, Konversionen und Umsatz niederschlägt. So können Sie den wahren Wert Ihrer KI-Präsenz messen.

>[!VIDEO](https://video.tv.adobe.com/v/3492512/?captions=ger&learn=on){transcript=true}

## Funktionsweise {#how-it-works}

### Konfiguration

Während der Einrichtung definieren Sie, welche Report Suite und Seitendimension LLM Optimizer für die Adobe Analytics-Aufnahme verwendet. Die Seitendimension kann je nach Report Suite die standardmäßige `variables/page`-Zuordnung oder eine benutzerdefinierte `eVar` sein.

### Identifizierung von LLM-Traffic

Der von LLM stammende Traffic wird mithilfe von den [Gesprächs-KI-Tools des Referrer-Typs](https://experienceleague.adobe.com/de/docs/analytics/components/dimensions/referrer-type#conversational-ai-tools) von Adobe Analytics identifiziert.

### Aufgenommene Daten {#data-ingested}

Die folgenden Daten werden von LLM Optimizer aufgenommen:

**Dimensionen**

* Referrer-Domain
* Referrer-Typ
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
* Warenkorbergänzungen
* Warenkorbentnahmen
* Warenkorbansichten
* Checkouts
* Bestellungen
* Umsatz
* Einheiten

### Verwendung dieser Daten durch LLM Optimizer

Dieser Datensatz ermöglicht LLM Optimizer-Erkenntnisse zu:

* LLM-Traffic-Leistung auf Seitenebene.
* Referrer-Leistung über LLM-Quellen hinweg.
* Trends in Regionen und auf Geräteebene.
* Nachgelagerte Handelsergebnisse.

## Häufig gestellte Fragen {#faq}

F: Ist die Adobe Analytics-Integration im Rahmen der Testversion verfügbar?

Nein. Die Integration ist nur für Kundschaften des kostenpflichtigen LLM Optimizer-Angebots verfügbar.

F: Welche Daten werden erfasst oder gespeichert?

Informationen dazu finden Sie im obigen Kapitel [Aufgenommene Daten](#data-ingested). LLM Optimizer arbeitet mit aggregierten Metriken aus den von Ihrer Organisation autorisierten Adobe Analytics-APIs und nicht mit den Rohdaten auf Trefferebene.

F: Wie werden Daten aufgenommen?

Ihre Organisation autorisiert LLM Optimizer, Adobe Analytics-APIs abzufragen. An LLM-Quellen angepasster Referral Traffic wird über diese APIs genutzt.

F: Wie oft werden die Daten aktualisiert?

Daten werden **täglich** aktualisiert (ganzer Vortag nach Abschluss der Aufstockung).

F: Werden in LLM Optimizer Rohdaten auf Trefferebene gespeichert?

Nein. Nur **aggregierte** Metriken werden zum Verständnis von Traffic-Mustern und -Trends verwendet.

F: Werden vollständige URLs, Abfragezeichenfolgen oder Seiteninhalte gespeichert?

Vollständige URLs, die für die ausgewählte Seitendimension verwendet werden, können aufgenommen werden. Abfragezeichenfolgen und Seiteninhalte werden für diese Integration nicht aufgenommen.

F: Werden Benutzerkennungen (ECID, IP-Adresse, Cookie-IDs) gespeichert?

Nein.

F: Wie lange werden Daten aufbewahrt?

Beachten Sie, dass sich die Aufbewahrungsrichtlinien ändern können. Derzeit werden Daten auf unbestimmte Zeit gespeichert.

F: Werden Daten während der Übertragung und im Ruhezustand verschlüsselt?

Derzeit werden die Daten während der Übertragung nicht im Ruhezustand verschlüsselt. Dies kann sich im Rahmen zukünftiger Updates ändern.

F: Werden historische Daten aufgestockt?

Ja. Nach einer erfolgreichen Einrichtung werden die letzten vier vollen Kalenderwochen und die aktuelle Kalenderwoche aufgestockt. Weitere Informationen finden Sie unter [Nach Herstellen der Verbindung](#after-connect).
