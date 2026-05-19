---
title: Protokollweiterleitung – CloudFront (AWS-CLI)
description: Leiten Sie CloudFront-CDN-Protokolle mithilfe der AWS-CLI an den S3-Bucket von Adobe weiter, um die Bereitstellung einzurichten und zu betreiben.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:42:44.992Z'
TQID: 'https://experienceleague.adobe.com/NoVv3qv1RbtqAWGMPYC1Rz4wO-5Au1yL2e8tRKd9Hao'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 379
ht-degree: 100%

---


# Protokollweiterleitung: CloudFront (AWS-CLI) {#log-forwarding-cloudfront-cli}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Daten zu Agent-basiertem Traffic von CloudFront an den S3-Bucket von Adobe weiterleiten. Verwenden Sie die CDN-Konfigurationsseite in LLM Optimizer für das Onboarding bei LLM Optimizer. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite aufgeführten Schritte mit der [AWS-Befehlszeilenschnittstelle](https://aws.amazon.com/cli/) in [Schritt 2](#step-2-cli) aus.

>[!NOTE]
>
> In diesem Handbuch wird die Konfiguration der Protokollweiterleitung über die [AWS-Befehlszeilenschnittstelle](https://aws.amazon.com/cli/) erläutert. Weitere Informationen zur Konfiguration der Protokollweiterleitung mithilfe der **CloudFront-Benutzeroberfläche** finden Sie unter [Protokollweiterleitung: CloudFront](/help/overview/log-forwarding/cloudfront.md).

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

<!--  ![AWS Account ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)-->

1. Wählen Sie **CloudFront (BYOCDN)** aus.

   ![Auswählen von CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Klicken Sie auf **Integrieren**.

<!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Einrichten der CDN-Protokollweiterleitung mit AWS-CLI {#step-2-cli}

Richten Sie die CDN-Protokollweiterleitung mit AWS-CLI wie folgt ein:

### Konfigurieren Sie die AWS-CLI-Anmeldedaten.

Richten Sie AWS-CLI-Anmeldedaten-MAC ein. Öffnen Sie ~/.aws/credentials und geben Sie die Werte für die folgenden Variablen ein:

```text
[LLMO]
aws_access_key_id=<VALUE_OF_ACCESS_KEY_ID>
aws_secret_access_key=<VALUE_OF_SECRET_KEY>
aws_session_token=<ONLY_IF_USING_SECURITY_TOKEN_SERVICE> ## Optional
```

### Testen der Verbindung

Führen Sie den folgenden Befehl aus, um die Verbindung zu testen:

```bash
aws sts get-caller-identity --profile LLMO
```

Beispiel für eine erfolgreiche Ausgabe:

```bash
aws sts get-caller-identity --profile LLMO
{
    "UserId": "AxxxxxxxxxxxP:user",
    "Account": "012345678912",
    "Arn": "arn:aws:sts::012345678912:assumed-role/klam-master-role-BatlY3dnPVinQLC/user"
}
```

### Initialisieren von Variablen

Ersetzen Sie `REPLACEME123@AdobeOrg` durch Ihre Adobe IMS-Organisations-ID und führen Sie den folgenden Befehl aus. Die Ausgabe-ID dieses Befehls wird als `TRANSFORM_IMS_ID` bezeichnet.

```bash
echo "REPLACEME123@AdobeOrg" | sed 's/@AdobeOrg$//' | tr '[:upper:]' '[:lower:]'
```

Geben Sie die Werte für `CUSTOMER`, `CDN_ID`, `ACCT1` und `TRANSFORM_IMS_ID` gemäß den unten stehenden Richtlinien ein und führen Sie dann Befehle von Ihrem Terminal aus.

```bash
export PROFILE1=LLMO
export REGION1=us-east-1
export CUSTOMER=<CUSTOMER_NAME> ## No Space, user letters,numbers and dash
export CDN_ID=<YOUR_CLOUDFRONT_DISTRIBUTION_ID>
export ACCT1=<YOUR_AWS_ACCOUNT_NUMBER>
export DELIVERY_DEST_ARN=arn:aws:logs:us-east-1:640168421876:delivery-destination:cdn-logs-<TRANSFORM_IMS_ID>-ams  ## Replace TRANSFORM_IMS_ID with the output of the command above
```

<!--Use the **Delivery destination ARN** and org values from the LLM Optimizer CDN configuration page if they differ from the pattern above.-->

### Erstellen der Bereitstellungsquelle

Führen Sie den folgenden Befehl auf dem Terminal aus, auf dem Schritt 3 ausgeführt wurde:

```bash
aws logs put-delivery-source --name llmo-cf-${CUSTOMER}-${CDN_ID} \
  --profile $PROFILE1 --region $REGION1 \
  --resource-arn arn:aws:cloudfront::${ACCT1}:distribution/${CDN_ID} \
  --log-type ACCESS_LOGS
```

>[!IMPORTANT]
>
>Wenn Sie den folgenden Fehler erhalten, suchen Sie nach der vorhandenen Bereitstellungsquelle: *Beim Aufrufen des PutDeliverySource-Vorgangs ist ein Fehler aufgetreten (ConflictException): Diese Ressourcen-ID wurde bereits in einer anderen Bereitstellungsquelle in diesem Konto verwendet.*
>
>Führen Sie diesen Befehl aus, um nach der vorhandenen Bereitstellungsquelle zu suchen:
>
>```bash
>aws logs describe-delivery-sources --region us-east-1 \
>--query "deliverySources[?contains(resourceArns[0], '<CDN DistributionID>')]"
>```
>
>Verwenden Sie im nächsten Befehl den Namen der Bereitstellungsquelle aus den Ergebnissen des obigen Befehls.

### Erstellen der Bereitstellungskonfiguration

```bash
aws logs create-delivery \
  --profile "$PROFILE1" --region "$REGION1" \
  --delivery-source-name "llmo-cf-${CUSTOMER}-${CDN_ID}" \
  --delivery-destination-arn $DELIVERY_DEST_ARN \
  --s3-delivery-configuration '{"suffixPath":"/{yyyy}/{MM}/{dd}/{HH}"}' \
  --record-fields 'date' 'time' 'x-edge-location' 'cs-method' 'cs(Host)' 'cs-uri-stem' 'sc-status' 'cs(Referer)' 'cs(User-Agent)' 'time-to-first-byte' 'sc-content-type' 'x-host-header'
```

&lt;!--Richten Sie `--record-fields` und `--s3-delivery-configuration` an der Feldliste und dem Pfadsuffix aus, die auf der CDN-Konfigurationsseite in LLM Optimizer angezeigt werden, wenn sich die Dokumentation oder die Produktwerte ändern.-->
