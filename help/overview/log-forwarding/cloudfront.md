---
title: Protokollweiterleitung – CloudFront
description: Erfahren Sie, wie Sie CDN-Protokolle von CloudFront an den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:47:22.372Z'
TQID: 'https://experienceleague.adobe.com/0aPeInYmcNRZLHUdABG2cEpT-dXb6GhEMoNUqMLMusY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 466
ht-degree: 100%

---


# Protokollweiterleitung: CloudFront {#log-forwarding-cloudfront}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Daten zu Agent-basiertem Traffic von CloudFront an den S3-Bucket von Adobe weiterleiten. Verwenden Sie die CDN-Konfigurationsseite in LLM Optimizer für das Onboarding bei LLM Optimizer. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite aufgeführten Schritte aus, um die Protokollweiterleitung in der CloudFront-Dashboard-Konsole zu konfigurieren.

## Schritt 1: Durchführen des Onboardings in LLM Optimizer {#step-1}

Führen Sie auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/) folgende Schritte aus:

1. Navigieren Sie zum Dashboard **Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die Registerkarte **CDN-Konfiguration**.

   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie auf **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Erkenntnisse aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Geben sie Ihre **AWS-Konto**-ID ein.

   ![AWS-Konto-ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Wählen Sie **CloudFront (BYOCDN)** aus.

   ![Auswählen von CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Klicken Sie auf **Integrieren**.

   ![Schaltfläche „Integrieren“](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Schritt 2: Aktivieren der Standardprotokollierung (CloudFront-Konsole) {#step-2}

Um die Standardprotokollierung zu aktivieren, führen Sie folgende Schritte in der [AWS Management Console](https://aws.amazon.com/console/) aus:

1. Rufen Sie die [CloudFront-Konsole](https://console.aws.amazon.com/cloudfront/v4/home) auf und [aktualisieren Sie eine vorhandene Verteilung](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Öffnen Sie die Registerkarte **Protokollierung**.

1. Wählen Sie **Hinzufügen** und dann den Service aus, der Protokolle empfangen soll, in diesem Fall **Amazon S3**.

1. Wählen Sie als **Ziel** eine Ressource aus oder erstellen Sie sie. Geben Sie den **Bucket-Namen** ein. Sie können den Wert von der CDN-Konfigurationsseite in LLM Optimizer kopieren.

   ![CloudFront-Bucket-Name](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Konfigurieren Sie **zusätzliche Einstellungen**:

   - **Feldauswahl**: Wählen Sie die Protokolldateifelder aus. Die erforderlichen Felder finden Sie auf der CDN-Konfigurationsseite in LLM Optimizer.

     ![CloudFront-Feldauswahl](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partitionierung**: Kopieren Sie das **Pfadsuffix** von der LLM Optimizer-Konfigurationsseite.

     ![CloudFront-Partitionierung](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Ausgabeformat**: Das Format sollte JSON sein.

     ![CloudFront-Ausgabeformat](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Führen Sie die folgenden Schritte aus, um die Verteilung zu aktualisieren oder zu erstellen.

1. Überprüfen Sie auf der Seite **Protokolle**, ob neben der Verteilung **Aktiviert** angezeigt wird.

## Aktivieren der Standardprotokollierung für kontoübergreifende Bereitstellung {#cross-account}

Das **Quellkonto** (mit der CloudFront-Verteilung) sendet Zugriffsprotokolle an das **Zielkonto** (den S3-Bucket, der auf der CDN-Konfigurationsseite in LLM Optimizer angezeigt wird). Beide Konten müssen über die entsprechenden Berechtigungen verfügen.

Beispiel: Das Quellkonto `111111111111` sendet Protokolle an einen S3-Bucket im Zielkonto `222222222222`. Sie können die [AWS-Befehlszeilenschnittstelle](https://aws.amazon.com/cli/) verwenden.

>[!NOTE]
>
>Ersetzen Sie in den folgenden Befehlen den Wert des Bereitstellungsziel-ARN (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) durch den Wert des **Bereitstellungsziel-ARN** auf der LLM Optimizer-Konfigurationsseite.

![Bereitstellungsziel-ARN](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Konfigurieren des Quellkontos {#source-account}

Als Nächstes müssen Sie das Quellkonto konfigurieren:

1. **Erstellen einer Bereitstellungsquelle** – Ersetzen Sie Namen und Verteilungs-ARN:

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Erstellen der Bereitstellung** – Verknüpfen Sie Quelle mit Ziel und verwenden Sie den Ziel-ARN aus dem Schritt „Erstellen des Zielkontos“:

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Überprüfen Sie Folgendes:**

   - Im **Quellkonto**: CloudFront-Konsole > Ihre Verteilung > Registerkarte **Protokollierung**. Unter **Typ** sollte die kontoübergreifende S3-Protokollbereitstellung angezeigt werden.
   - Im **Zielkonto**: S3-Konsole > Bucket. In diesem Ordner sollten das Präfix (z. B. `MyLogPrefix`) und die Protokolle angezeigt werden.
