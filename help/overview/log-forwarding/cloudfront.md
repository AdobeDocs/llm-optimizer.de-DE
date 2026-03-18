---
title: Protokollweiterleitung - CloudFront
description: Erfahren Sie, wie Sie CDN-Protokolle zur Erfassung von agenten Traffic-Daten in LLM Optimizer von CloudFront an den S3-Bucket von Adobe weiterleiten.
feature: Agentic Traffic
source-git-commit: d1f98770b39f550c36d93ece9b89933c0e90f189
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---


# Protokollweiterleitung: CloudFront {#log-forwarding-cloudfront}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von CloudFront an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite bereitgestellten Schritte aus, um die Protokollweiterleitung in der CloudFront-Dashboard-Konsole zu konfigurieren.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/):

1. Navigieren Sie zum **Dashboard Kundenkonfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Geben Sie Ihre **AWS-Konto** ID ein.

   ![AWS-Konto-ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Wählen Sie **CloudFront (BYOCDN)**.

   ![CloudFront auswählen](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Klicken Sie **Onboard**.

   ![Onboard-Schaltfläche](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Schritt 2: Standardprotokollierung aktivieren (CloudFront-Konsole) {#step-2}

Um die Standardprotokollierung zu aktivieren, verwenden Sie die [AWS-Verwaltungskonsole](https://aws.amazon.com/console/):

1. Rufen Sie die [CloudFront-Konsole](https://console.aws.amazon.com/cloudfront/v4/home) auf und [aktualisieren Sie eine vorhandene Verteilung](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Öffnen Sie die **Protokollierung**.

1. Wählen Sie **Hinzufügen** aus und wählen Sie dann den Service aus, der Protokolle empfangen soll, in diesem Fall **Amazon S3**.

1. Wählen **/Ziel** Ressource aus oder erstellen Sie sie. Geben Sie den **Behälternamen** ein. Sie können den Wert von der LLM Optimizer CDN-Konfigurationsseite kopieren.

   ![CloudFront-Behältername](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Konfigurieren Sie **Zusätzliche Einstellungen**:

   - **Feldauswahl** — Wählen Sie die Protokolldateifelder aus. Die erforderlichen Felder finden Sie auf der Seite LLM Optimizer CDN-Konfiguration .

     ![CloudFront-Feldauswahl](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partitionierung** - Kopieren Sie das **Pfad-Suffix** von der LLM Optimizer-Konfigurationsseite.

     ![CloudFront-Partitionierung](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Ausgabeformat** - Das Format sollte JSON sein.

     ![CloudFront-Ausgabeformat](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Führen Sie die Schritte zum Aktualisieren oder Erstellen der Verteilung aus.

1. Bestätigen Sie auf **Seite** Protokolle“, dass **Aktiviert** neben der Verteilung angezeigt wird.

## Standardprotokollierung für kontoübergreifenden Versand aktivieren {#cross-account}

Das **Quellkonto** (mit der CloudFront-Verteilung) sendet Zugriffsprotokolle an das **Zielkonto** (der S3-Bucket, der auf der LLM Optimizer CDN-Konfigurationsseite angezeigt wird). Beide Konten müssen über die richtigen Berechtigungen verfügen.

Beispiel: Das Quellkonto `111111111111` sendet Protokolle an einen S3-Bucket im Zielkonto `222222222222`. Sie können die Befehlszeilenschnittstelle von [AWS verwenden](https://aws.amazon.com/cli/).

>[!NOTE]
>
>Ersetzen Sie in den folgenden Befehlen den ARN-Wert (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) des Versandziels durch den Wert **ARN des Versandziels** auf der LLM Optimizer-Konfigurationsseite.

![Versandziel-ARN](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Quellkonto konfigurieren {#source-account}

Als Nächstes müssen Sie das Quellkonto konfigurieren:

1. **Erstellen einer Versandquelle** - Ersetzen Sie den Namen und das Verteilungs-ARN:

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Versand erstellen** - Quelle mit Ziel verknüpfen; Verwenden Sie das Ziel-ARN aus dem Schritt „Zielkonto konfigurieren“:

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Verify:**

   - Im **source**-Konto: CloudFront-Konsole > Ihre Verteilung > **Protokollierung** Registerkarte. Unter **Typ** sollte der kontenübergreifende S3-Protokollversand angezeigt werden.
   - Im **Ziel**-Konto: S3-Konsole > -Bucket. Sie sollten das Präfix (z. B. `MyLogPrefix`) und die Protokolle in diesem Ordner sehen.
