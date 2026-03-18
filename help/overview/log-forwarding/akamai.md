---
title: Protokollweiterleitung - Akamai
description: Erfahren Sie, wie Sie CDN-Protokolle von Akamai an den S3-Bucket von Adobe für die Erfassung von Agentenverkehrsdaten in LLM Optimizer weiterleiten.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Protokollweiterleitung: Akamai {#log-forwarding-akamai}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von Akamai an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite angegebenen Schritte aus, um die Protokollweiterleitung im Akamai Control Panel zu konfigurieren.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/):

1. Navigieren Sie zum **Dashboard Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie **Erste Schritte**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Akamai (BYOCDN)** aus.

   ![Akamai auswählen](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Klicken Sie **Onboard**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Erstellen eines Streams in Akamai {#step-2}

Befolgen Sie im Akamai-Control Panel [https://control.akamai.com/ ](https://control.akamai.com/) Schritte in der offiziellen Akamai-Dokumentation, um [Stream zu erstellen](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Schritt 3: Auswählen der Datenparameter {#step-3}

Klicken Sie nach der Erstellung des Streams im Akamai-Control Panel auf Weiter , um zur Registerkarte **Datensätze** zu gelangen. Folgen Sie den Schritten in der offiziellen Akamai-Dokumentation, um die [Datenparameter“ ](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters). Die folgenden Felder aus der LLM Optimizer-Konfiguration werden benötigt:

![LLMO-Konfigurationsfelder](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

Die Zuordnung sollte wie folgt sein:

* **Protokollinformationen**
reqTimeSec -> Anfragezeit
* **Geodaten**
Land -> Land/Region
* **Nachrichtenaustauschdaten**
reqHost -> Host anfordern
reqPath -> Anfragepfad
queryStr -> Abfragezeichenfolge
reqMethod -> Request-Methode
UA -> Benutzeragent
statusCode -> HTTP-Status-Code
rspContentType -> Content-Type-Antwort
* **Header-Daten anfordern**
Referer -> Referer
* **Netzwerkleistungsdaten**
timeToFirstByte -> Zeit bis zum ersten Byte

Die Akamai-Datensatzfelder (einschließlich IDs) lauten wie folgt:

1100, # reqTimeSec -> Anfragezeit
2012, # Land -> Land/Region
1011, # reqHost -> Host anfordern
1013, # reqPath -> Anfragepfad
2009, # queryStr -> Abfragezeichenfolge
1012, # reqMethod -> Anforderungsmethode
1017, # ua -> Benutzeragent
1008, # statusCode -> HTTP Status Code
1032, # referer -> Referer
1016, # rspContentType -> Antwort Content-Type
2025 # timeToFirstByte -> Zeit bis zum ersten Byte

## Schritt 4: Konfigurieren des Ziels {#step-4}

Nachdem Sie die Datenströme erstellt und die Parameter ausgewählt haben, müssen Sie das Ziel konfigurieren. Gehen Sie wie folgt vor, um das Ziel zu konfigurieren:

1. Wählen **unter** die Option **S3** aus.
2. Geben **unter** eine für Menschen lesbare Beschreibung für das Ziel ein.
3. Kopieren **in „Bucket** den **Bucket-Namen** von der LLM Optimizer-Konfigurationsseite.

   ![Behältername](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. Kopieren **unter** den **Pfad** von der LLM Optimizer-Konfigurationsseite.

   ![Pfadkonfiguration](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. Kopieren Sie **Region** die **Region** von der LLM Optimizer-Konfigurationsseite.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. Kopieren **in „Zugriffsschlüssel** ID“ und **Geheimer Zugriffsschlüssel** beide Werte aus der LLM Optimizer-Konfigurationsseite.

   ![Zugriffsschlüssel](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Klicken Sie **Validieren und Speichern**, um die Verbindung zum Ziel zu überprüfen und die angegebenen Details zu speichern. Im Rahmen dieses Validierungsprozesses verwendet das System die bereitgestellte Zugriffsschlüsselkennung und den geheimen Zugriffsschlüssel, um eine Verifizierungsdatei in Ihrem S3-Ordner mit einem Zeitstempel im Dateinamen im `Akamai_access_verification_[TimeStamp].txt`-Format zu erstellen. Diese Datei wird nur angezeigt, wenn der Validierungsprozess erfolgreich war und Sie Zugriff auf den Amazon S3-Bucket und -Ordner haben, an den Sie Protokolle senden möchten.

8. Bearbeiten **im Menü** das Feld **Dateiname** wie folgt:

   a. Ändern Sie das **Präfix**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokolldateipräfix**:

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   B. Ändern Sie das **Suffix**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokolldateisuffix**.

9. Ändern Sie die **Push-Häufigkeit**. Kopieren Sie den Wert von der LLM Optimizer-Konfigurationsseite unter **Protokollintervall**.

   ![Protokollintervall](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Klicken Sie **Weiter**, um den Vorgang abzuschließen.

Vor der endgültigen Validierung sollte die Konfiguration wie im folgenden Beispiel aussehen:

![Konfigurationsvalidierung](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
