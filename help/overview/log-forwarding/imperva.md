---
title: Protokollweiterleitung – Imperva
description: Erfahren Sie, wie Sie CDN-Protokolle von Imperva an den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:57:30.264Z'
TQID: 'https://experienceleague.adobe.com/l-DYz7pXzFDqZn1rnZWUOG9PpRqosq00LmGrlsOMqNk'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3aid: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: dd952468-5202-43af-a365-6e0d2e67a703id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 352
ht-degree: 100%

---


# Protokollweiterleitung: Imperva {#log-forwarding-imperva}

In diesem Handbuch wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Daten zu Agent-basiertem Traffic von Imperva an den S3-Bucket von Adobe weiterleiten. Verwenden Sie die CDN-Konfigurationsseite in LLM Optimizer für das Onboarding bei LLM Optimizer. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite aufgeführten Schritte aus, um die Protokollweiterleitung von der Imperva-Web-Konsole zu konfigurieren.

## Schritt 1: Durchführen des Onboardings in LLM Optimizer {#step-1}

Führen Sie auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/) folgende Schritte aus:

1. Navigieren Sie zu **Konfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die Registerkarte **CDN-Konfiguration**.

   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Klicken Sie auf **Erste Schritte**.
1. Klicken Sie neben **KI-Traffic-Erkenntnisse aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)
1. Wählen Sie **Imperva (BYOCDN)** aus.

   ![Auswählen von Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Klicken Sie auf **Integrieren**.

## Schritt 2: Konfigurieren der Protokollweiterleitung in Imperva {#step-2}

Führen Sie in der [Imperva-Konsole](https://my.imperva.com) folgende Schritte aus:

>[!NOTE]
>
>Protokolle sollten täglich gesendet werden.

1. Melden Sie sich bei Ihrem Imperva-Konto unter [https://my.imperva.com](https://my.imperva.com) an.

2. Navigieren Sie in der Seitenleiste zu **Protokolle** > **Protokolleinrichtung** (oder **Protokollintegration**).

3. Wählen Sie **Amazon S3 ARN** als Verbindungstyp (Protokollziel) aus.

4. Geben Sie Folgendes ein:

   | Feld | Beschreibung | Hinweis |
   |---|---|---|
   | **Verbindungsname** | Ein beschreibender Name für die Verbindung (z. B. „S3-Produktionsprotokolle“). Sie können den Standard umbenennen. | |
   | **Pfad** | Der Speicherort des Ordners, in dem Protokolldateien gespeichert werden. Verwenden Sie das Format `<Amazon S3 bucket name>/<log folder>`. Beispiel: `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` ist der **Bucket-Name** von der LLM Optimizer-Konfigurationsseite. ![Bucket-Name](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) Der Protokollordner ist **Pfad** von der LLM Optimizer-Konfigurationsseite. ![Pfad](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Klicken Sie auf **Verbindung testen**. Imperva führt einen vollständigen Test durch, bei dem eine Testdatei (ohne echte Daten) an den designierten Ordner gesendet und nach Abschluss der Übertragung wieder entfernt wird.

   - **Verfügbar**: Speicherdetails sind gültig. Sie können die Protokolle so konfigurieren, dass diese Verbindung verwendet wird.
   - **Nicht definiert**: Entweder fehlen die erforderlichen Details oder der Test ist fehlgeschlagen.

6. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.

7. Konfigurieren Sie die Protokolloptionen (Protokolltypen, Protokollstufe, Format, Komprimierung) und die **Protokollebenen**. Die Werte können Sie der LLM Optimizer-Konfigurationsseite entnehmen.

   | Feld | Hinweis |
   |---|---|
   | Protokollintegrationsmodus | ![Protokollintegrationsmodus](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Bereitstellungsmethode | ![Bereitstellungsmethode](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Protokolltypen | ![Protokolltypen](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Protokollebene | ![Protokollebene](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Format | ![Format](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Protokolle komprimieren | ![Protokolle komprimieren](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
