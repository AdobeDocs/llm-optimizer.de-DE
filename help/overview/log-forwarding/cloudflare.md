---
title: Protokollweiterleitung - Cloudflare
description: Erfahren Sie, wie Sie CDN-Protokolle zur Erfassung von agenten Traffic-Daten in LLM Optimizer von Cloudflare an den S3-Bucket von Adobe weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:41:23.688Z'
TQID: 'https://experienceleague.adobe.com/AfhcMa7tZ3L-4qCbNKiblInALmHaKxWLtL-O-Hkvc-U'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 381
ht-degree: 0%

---


# Protokollweiterleitung: Cloudflare {#log-forwarding-cloudflare}

Auf dieser Seite wird beschrieben, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von Cloudflare an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite bereitgestellten Schritte aus, um die Protokollweiterleitung in der Cloudflare-Dashboard-Konsole zu konfigurieren.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/):

1. Navigieren Sie zum **Dashboard Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png) -->

1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Cloudflare (BYOCDN)** aus.

   ![Cloudflare auswählen](/help/overview/assets/log-forwarding/cloudflare/cloudflare-select.png)

1. Klicken Sie **Onboard**.

   <!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Erstellen eines Logpush-Auftrags in Cloudflare {#step-2}

Gehen Sie im [Cloudflare](https://dash.cloudflare.com/login)Dashboard) wie folgt vor:

1. Navigieren Sie zur **Logpush**-Seite auf der Ebene **Domain (Zone** .
1. Wählen Sie **Erstellen eines LogPush-Auftrags**.
1. Wählen **unter „Ziel auswählen** die Option **Amazon S3**.
1. Geben Sie die folgenden Zielinformationen ein:

   - **Bucket** - der S3-Bucket-Name. Kopieren Sie den Wert von der Seite LLM Optimizer CDN-Konfiguration .

     ![Behältername](/help/overview/assets/log-forwarding/common/bucket-name.png)

   - **Path** - der Speicherort des Buckets im Speicher-Container. Kopieren Sie den Wert von der Seite LLM Optimizer CDN-Konfiguration .

     ![Cloudflare-Pfad](/help/overview/assets/log-forwarding/cloudflare/cloudflare-path.png)

   - **Organisieren von Protokollen in täglichen** (empfohlen).

     ![Tägliche Unterordner](/help/overview/assets/log-forwarding/cloudflare/cloudflare-daily-subfolders.png)

   - **Bucket-Region** - Kopieren Sie den Wert von der LLM Optimizer CDN-Konfigurationsseite.

     <!-- ![Region](/help/overview/assets/log-forwarding/cloudflare/cloudflare-region.png)-->

   - Wenn keine Server-seitige Verschlüsselung erforderlich ist, deaktivieren Sie diese Option.

   Klicken Sie nach Abschluss der oben genannten Schritte auf **Weiter**.

1. Um die Eigentümerschaft nachzuweisen, sendet Cloudflare eine Datei an Ihr bestimmtes Ziel. Um das Token zu finden, klicken Sie auf die Schaltfläche **Öffnen** auf der Registerkarte **Übersicht** der Datei für die Eigentümerabfrage. Kopieren Sie das Eigentümer-Token von der LLM Optimizer CDN-Konfigurationsseite und fügen Sie es dann in das Cloudflare-Dashboard ein, um Ihren Zugriff auf den Bucket zu überprüfen. Geben Sie das Ownership-Token ein und wählen Sie **Weiter**.

   <!--![Ownership token](/help/overview/assets/log-forwarding/cloudflare/cloudflare-ownership-token.png)-->

1. Wählen Sie den **HTTP-Anfragen**-Datensatz aus, der an den Speicher-Service gepusht werden soll.

1. Konfigurieren Sie Ihren LogPush-Auftrag:

   - Geben Sie den **Auftragsnamen“**.

   - Weitere Informationen **Senden der folgenden Felder** finden Sie auf der Seite LLM Optimizer-Konfiguration unter den Werten.

     ![Logpush-Felder](/help/overview/assets/log-forwarding/cloudflare/cloudflare-logpush-fields.png)

   - **Protokollformat**: JSON.

     <!--![JSON format](/help/overview/assets/log-forwarding/cloudflare/cloudflare-json-format.png)-->

1. Unter **Erweiterte Optionen**:

   - Wählen Sie das Format der Zeitstempelfelder in Ihren Protokollen aus: `RFC3339`.

     ![Zeitstempelformat](/help/overview/assets/log-forwarding/cloudflare/cloudflare-timestamp-format.png)

   - Wählen Sie für Stichprobenraten **Alle Protokolle** aus.

     ![Stichprobenrate](/help/overview/assets/log-forwarding/cloudflare/cloudflare-sampling-rate.png)

1. Wählen Sie **Senden** aus, sobald Sie die Konfiguration des LogPush-Auftrags abgeschlossen haben.
