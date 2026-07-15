---
title: Protokollweiterleitung – Akamai
description: Erfahren Sie, wie Sie CDN-Protokolle von Akamai an den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:40:31.728Z'
TQID: 'https://experienceleague.adobe.com/I-FHVzjiUvTwncGnfR2aAV2lOgtyltvac8aRN5LEQoE'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 612
ht-degree: 93%

---


# Protokollweiterleitung: Akamai {#log-forwarding-akamai}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Daten zu Agent-basiertem Traffic von Akamai an den S3-Bucket von Adobe weiterleiten. Verwenden Sie die CDN-Konfigurationsseite in LLM Optimizer für das Onboarding bei LLM Optimizer. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite aufgeführten Schritte aus, um die Protokollweiterleitung im Akamai Control Panel zu konfigurieren.

## Schritt 1: Durchführen des Onboardings in LLM Optimizer {#step-1}

Führen Sie auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/) folgende Schritte aus:

1. Navigieren Sie zum Dashboard **Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die Registerkarte **CDN-Konfiguration**.

   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie auf **Erste Schritte**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Erkenntnisse aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Akamai (BYOCDN)** aus.

   ![Auswählen von Akamai](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Klicken Sie auf **Integrieren**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Erstellen eines Streams in Akamai {#step-2}

Befolgen Sie im Akamai Control Panel [https://control.akamai.com/](https://control.akamai.com/) die Schritte der offiziellen Akamai-Dokumentation, um [einen Stream zu erstellen](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Schritt 3: Auswählen der Datenparameter {#step-3}

Klicken Sie nach der Erstellung des Streams im Akamai-Control Panel auf **Weiter**, um zur Registerkarte **Datensätze** zu wechseln. Befolgen Sie die Schritten in der offiziellen Akamai-Dokumentation, um die [Datenparameter](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters) auszuwählen. Die folgenden Felder aus der LLM Optimizer-Konfiguration werden benötigt:

![LLMO-Konfigurationsfelder](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

Die Zuordnung sollte wie folgt sein:

* **Protokollinformation**
reqTimeSec -> Anfragezeit
* **Geodaten**
country -> Land/Region
* **Nachrichtenaustauschdaten**
reqHost -> Anfrage-Host
reqPath -> Anfragepfad
queryStr -> Abfragezeichenfolge (optional)
reqMethod -> Anfragemethode
ua -> Benutzer-Agent
statusCode -> HTTP-Status-Code
rspContentType -> Antwort-Content-Typ
* **Anfrage-Header-Daten**
referer -> Referrer
* **Netzwerkleistungsdaten**
timeToFirstByte -> Zeit bis zum ersten Byte

>[!NOTE]
>
>Der `queryStr` ist optional. Sie können es weglassen, wenn die Abfragezeichenfolge personenbezogene Daten enthält.

Die Akamai-Datensatzfelder (einschließlich IDs) lauten wie folgt:

1100, # reqTimeSec -> Anfragezeit
2012, # country -> Land/Region
1011, # reqHost -> Anfrage-Host
1013, # reqPath -> Anfragepfad
2009, # queryStr -> Abfragezeichenfolge (optional)
1012, # reqMethod -> Anfragemethode
1017, # ua -> Benutzer-Agent
1008, # statusCode -> HTTP-Status-Code
1032, # referer -> Referrer
1016, # rspContentType -> Antwort-Content-Typ
2025  # timeToFirstByte -> Zeit bis zum ersten Byte

## Schritt 4: Konfigurieren des Ziels {#step-4}

Nachdem Sie die Datenströme erstellt und die Parameter ausgewählt haben, müssen Sie das Ziel konfigurieren. Gehen Sie wie folgt vor, um das Ziel zu konfigurieren:

1. Wählen Sie unter **Ziel** **S3** aus.
2. Geben Sie unter **Name** eine für Menschen lesbare Beschreibung des Ziels ein.
3. Kopieren Sie für **Bucket** den **Bucket-Namen** von der LLM Optimizer-Konfigurationsseite.

   ![Bucket-Name](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. Kopieren Sie für **Ordnerpfad** den **Pfad** von der der LLM Optimizer-Konfigurationsseite.

   ![Pfadkonfiguration](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. Kopieren Sie für **Region** die **Region** von der LLM Optimizer-Konfigurationsseite.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. Kopieren Sie für **Zugriffsschlüssel-ID** und **Geheimer Zugriffsschlüssel** beide Werte von der LLM Optimizer-Konfigurationsseite.

   ![Zugriffsschlüssel](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Klicken Sie **Validieren und speichern**, um die Verbindung zum Ziel zu validieren und die angegebenen Details zu speichern. Im Rahmen dieses Validierungsprozesses verwendet das System die bereitgestellte Zugriffsschlüsselkennung und den geheimen Zugriffsschlüssel, um eine Verifizierungsdatei in Ihrem S3-Ordner mit einem Zeitstempel im Dateinamen im Format `Akamai_access_verification_[TimeStamp].txt` zu erstellen. Diese Datei wird nur angezeigt, wenn der Validierungsprozess erfolgreich war und Sie Zugriff auf den Amazon S3-Bucket und -Ordner haben, an den Sie Protokolle senden möchten.

8. Bearbeiten Sie im Menü **Bereitstellungsoptionen** das Feld **Dateiname** wie folgt:

   a. Ändern Sie das **Präfix**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokolldateipräfix**:

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   b. Ändern Sie das **Suffix**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokolldateisuffix**.

9. Ändern Sie die **Push-Häufigkeit**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokollintervall**.

   ![Protokollintervall](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Klicken Sie auf **Weiter**, um den Prozess abzuschließen.

Vor der endgültigen Validierung sollte die Konfiguration wie im folgenden Beispiel aussehen:

![Konfigurationsvalidierung](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
