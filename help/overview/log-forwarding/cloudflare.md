---
title: Protokollweiterleitung – Cloudflare
description: Erfahren Sie, wie Sie CDN-Protokolle von Cloudflare an den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:45:52.167Z'
TQID: 'https://experienceleague.adobe.com/6D7Xe-ysQOSsNMONyart2HaTfdyQR64l0r3AeFNsOpI'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 381
ht-degree: 100%

---


# Protokollweiterleitung: Cloudflare {#log-forwarding-cloudflare}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Daten zu Agent-basiertem Traffic von Cloudflare an den S3-Bucket von Adobe weiterleiten. Verwenden Sie die CDN-Konfigurationsseite in LLM Optimizer für das Onboarding bei LLM Optimizer. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite aufgeführten Schritte aus, um die Protokollweiterleitung in der Cloudflare-Dashboard-Konsole zu konfigurieren.

## Schritt 1: Durchführen des Onboardings in LLM Optimizer {#step-1}

Führen Sie auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/) folgende Schritte aus:

1. Navigieren Sie zum Dashboard **Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die Registerkarte **CDN-Konfiguration**.

   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie auf **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png) -->

1. Klicken Sie neben **KI-Traffic-Erkenntnisse aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Cloudflare (BYOCDN)** aus.

   ![Auswählen von Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-select.png)

1. Klicken Sie auf **Integrieren**.

   <!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Erstellen eines Logpush-Auftrags in Cloudflare {#step-2}

Führen Sie auf dem [Cloudflare-Dashboard](https://dash.cloudflare.com/login) die folgenden Schritte aus:

1. Navigieren Sie zur Seite **Logpush** auf der Ebene **Domain (Zone)**.
1. Wählen Sie **Logpush-Auftrag erstellen** aus.
1. Wählen Sie in **Ziel auswählen** **Amazon S3** aus.
1. Geben Sie folgende Zielinformationen ein:

   - **Bucket**: Der S3-Bucket-Name. Kopieren Sie den Wert auf der CDN-Konfigurationsseite in LLM Optimizer.

     ![Bucket-Name](/help/overview/assets/log-forwarding/common/bucket-name.png)

   - **Pfad**: Der Speicherort des Buckets innerhalb des Speicher-Containers. Kopieren Sie den Wert auf der CDN-Konfigurationsseite in LLM Optimizer.

     ![Cloudflare-Pfad](/help/overview/assets/log-forwarding/cloudflare/cloudflare-path.png)

   - **Organisieren Sie die Protokolle in täglichen Unterordnern** (empfohlen).

     ![Tägliche Unterordner](/help/overview/assets/log-forwarding/cloudflare/cloudflare-daily-subfolders.png)

   - **Bucket-Region**: Kopieren Sie den Wert von der CDN-Konfigurationsseite von LLM Optimizer.

     <!-- ![Region](/help/overview/assets/log-forwarding/cloudflare/cloudflare-region.png)-->

   - Wenn keine Server-seitige Verschlüsselung erforderlich ist, lassen Sie diese Option deaktiviert.

   Klicken Sie nach Abschluss der oben genannten Schritte auf **Weiter**.

1. Um die Eigentümerschaft nachzuweisen, sendet Cloudflare eine Datei an Ihr designiertes Ziel. Um das Token zu finden, klicken Sie auf die Schaltfläche **Öffnen** auf der Registerkarte **Überblick** der Datei für die Eigentümerabfrage. Kopieren Sie das Eigentums-Token von der CDN-Konfigurationsseite in LLM Optimizer und fügen Sie es dann in das Cloudflare-Dashboard ein, um Ihren Zugriff auf den Bucket zu überprüfen. Geben Sie das Eigentums-Token ein und wählen Sie **Weiter** aus.

   <!--![Ownership token](/help/overview/assets/log-forwarding/cloudflare/cloudflare-ownership-token.png)-->

1. Wählen Sie den Datensatz für **HTTP-Anfragen** aus, der an den Speicherdienst gesendet werden soll.

1. Konfigurieren Sie Ihren LogPush-Auftrag:

   - Geben Sie den **Auftragsnamen** ein.

   - In **Folgende Felder senden** werden die Werte für die LLM Optimizer-Konfigurationsseite angezeigt.

     ![Logpush-Felder](/help/overview/assets/log-forwarding/cloudflare/cloudflare-logpush-fields.png)

   - **Protokollformat**: JSON.

     <!--![JSON format](/help/overview/assets/log-forwarding/cloudflare/cloudflare-json-format.png)-->

1. In **Erweiterte Optionen**:

   - Wählen Sie das Format der Zeitstempelfelder in Ihren Protokollen aus: `RFC3339`.

     ![Zeitstempelformat](/help/overview/assets/log-forwarding/cloudflare/cloudflare-timestamp-format.png)

   - Wählen Sie für Sampling-Raten **Alle Protokolle** aus.

     ![Sampling-Rate](/help/overview/assets/log-forwarding/cloudflare/cloudflare-sampling-rate.png)

1. Wählen Sie **Senden** aus, sobald Sie die Konfiguration des LogPush-Auftrags abgeschlossen haben.
