---
title: Protokollweiterleitung - CloudFront (AWS CLI)
description: Weiterleiten von CloudFront CDN-Protokollen an den S3-Bucket von Adobe mithilfe der AWS-CLI für die Einrichtung und den Betrieb von Sendungen.
feature: Agentic Traffic
source-git-commit: 0d51bbde954c399dc6595522fa70b576461f458a
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Protokollweiterleitung: CloudFront (AWS CLI) {#log-forwarding-cloudfront-cli}

Auf dieser Seite wird beschrieben, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von CloudFront an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Führen Sie nach Abschluss des Onboarding-Prozesses die auf dieser Seite beschriebenen Schritte aus, um die Protokollweiterleitung mithilfe der [AWS-Befehlszeilenschnittstelle](https://aws.amazon.com/cli/) in [Schritt 2](#step-2-cli) zu konfigurieren.

>[!NOTE]
>
> In diesem Handbuch wird erläutert, wie die Protokollweiterleitung mithilfe der [AWS-Befehlszeilenschnittstelle](https://aws.amazon.com/cli/) konfiguriert wird. Wenn Sie die Protokollweiterleitung mithilfe der **CloudFront-Benutzeroberfläche) konfigurieren möchten** finden Sie weitere Informationen unter [Protokollweiterleitung: CloudFront](/help/overview/log-forwarding/cloudfront.md).

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

## Schritt 2: Einrichten der CDN-Protokollweiterleitung mit AWS CLI {#step-2-cli}

Richten Sie die CDN-Protokollweiterleitung mit AWS CLI wie folgt ein:

### Konfigurieren von AWS CLI-Anmeldeinformationen

Einrichten der AWS CLI-Anmeldedaten für MAC. Öffnen Sie ~/.aws/credentials und geben Sie die Werte für die folgenden Variablen ein:

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

### Versandquelle erstellen

Führen Sie auf dem Terminal, auf dem Schritt 3 ausgeführt wurde, den folgenden Befehl aus:

```bash
aws logs put-delivery-source --name llmo-cf-${CUSTOMER}-${CDN_ID} \
  --profile $PROFILE1 --region $REGION1 \
  --resource-arn arn:aws:cloudfront::${ACCT1}:distribution/${CDN_ID} \
  --log-type ACCESS_LOGS
```

>[!IMPORTANT]
>
>Wenn Sie den folgenden Fehler erhalten, suchen Sie nach der vorhandenen Versandquelle: *Beim Aufrufen des Vorgangs PutDeliverySource ist ein Fehler aufgetreten (ConflictException): Diese Ressourcen-ID wurde bereits in einer anderen Versand-Source in diesem Konto verwendet.*
>
>Führen Sie diesen Befehl aus, um nach der vorhandenen Versandquelle zu suchen:
>
>```bash
>aws logs describe-delivery-sources --region us-east-1 \
>--query "deliverySources[?contains(resourceArns[0], '<CDN DistributionID>')]"
>```
>
>Verwenden Sie im nächsten Befehl den Namen der Versandquelle aus den Ergebnissen des obigen Befehls.

### Erstellen der Versandkonfiguration

```bash
aws logs create-delivery \
  --profile "$PROFILE1" --region "$REGION1" \
  --delivery-source-name "llmo-cf-${CUSTOMER}-${CDN_ID}" \
  --delivery-destination-arn $DELIVERY_DEST_ARN \
  --s3-delivery-configuration '{"suffixPath":"/{yyyy}/{MM}/{dd}/{HH}"}' \
  --record-fields 'date' 'time' 'x-edge-location' 'cs-method' 'cs(Host)' 'cs-uri-stem' 'sc-status' 'cs(Referer)' 'cs(User-Agent)' 'time-to-first-byte' 'sc-content-type' 'x-host-header'
```

&lt;!—Richten Sie `--record-fields` und `--s3-delivery-configuration` an der Feldliste und dem Pfadsuffix aus, die auf Ihrer LLM Optimizer CDN-Konfigurationsseite angezeigt werden, wenn sich die Dokumentation oder die Produktwerte ändern.—>
