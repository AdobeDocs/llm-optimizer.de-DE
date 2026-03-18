---
title: Protokollweiterleitung - Imperva
description: Erfahren Sie, wie Sie CDN-Protokolle von Imperva an den S3-Bucket von Adobe für die Erfassung von agenten Traffic-Daten in LLM Optimizer weiterleiten.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 5%

---


# Protokollweiterleitung: Imperva {#log-forwarding-imperva}

In diesem Handbuch wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von Imperva an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite angegebenen Schritte aus, um die Protokollweiterleitung über die Imperva-Web-Konsole zu konfigurieren.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/):

1. Navigieren Sie zu **Konfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Klicken Sie **Erste Schritte**.
1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)
1. Wählen Sie **Imperva (BYOCDN)**.

   ![Wählen Sie Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Klicken Sie **Onboard**.

## Schritt 2: Konfigurieren der Protokollweiterleitung in Imperva {#step-2}

Auf der [Imperva-Konsole](https://my.imperva.com):

>[!NOTE]
>
>Protokolle sollten täglich gesendet werden.

1. Melden Sie sich bei Ihrem Imperva-Konto unter [https://my.imperva.com](https://my.imperva.com) an.

2. Navigieren Sie in der Seitenleiste zu **Protokolle** > **Protokolleinstellungen** (oder **Protokollintegration**).

3. Wählen Sie **Amazon S3 ARN** als Verbindungstyp (Protokollziel) aus.

4. Geben Sie Folgendes ein:

   | Feld | Beschreibung | Hinweis |
   |---|---|---|
   | **Verbindungsname** | Ein beschreibender Name für die Verbindung (z. B. S3-Produktionsprotokolle). Sie können den Standard umbenennen. | |
   | **Pfad** | Der Speicherort des Ordners, in dem Protokolldateien gespeichert werden. Verwenden Sie den `<Amazon S3 bucket name>/<log folder>`. Beispiel: `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` ist der **Behältername** auf der Seite LLM Optimizer-Konfiguration. ![Behältername](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) Der Protokollordner ist **Pfad** auf der LLM Optimizer-Konfigurationsseite. ![Pfad](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Klicken Sie **Verbindung testen**. Imperva führt einen vollständigen Test durch, bei dem eine Testdatei (keine echten Daten) an den vorgesehenen Ordner gesendet und dann entfernt wird, wenn die Übertragung abgeschlossen ist.

   - **Verfügbar** - Speicherdetails sind gültig; Sie können Protokolle konfigurieren, um diese Verbindung zu verwenden.
   - **Nicht definiert** - Entweder fehlen die erforderlichen Details oder der Test ist fehlgeschlagen.

6. Klicken Sie **Speichern**, um die Konfiguration zu speichern.

7. Konfigurieren Sie die Protokolloptionen (Protokolltypen, Protokollebene, Format, Komprimierung) und **Protokollebenen**. Sie können die Werte von der LLM Optimizer-Konfigurationsseite abrufen.

   | Feld | Hinweis |
   |---|---|
   | Log-Integrationsmodus | ![Log-Integrationsmodus](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Versandmethode | ![Versandmethode](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Protokolltypen | ![Protokolltypen](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Protokollebene | ![Protokollebene](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Format | ![Format](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Protokolle komprimieren | ![Protokolle komprimieren](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
