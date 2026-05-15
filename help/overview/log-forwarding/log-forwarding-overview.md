---
title: Übersicht über die BYOCDN-Protokollweiterleitung
description: Erfahren Sie, wie Sie CDN-Protokolle von Ihrem Anbieter an den S3-Bucket von Adobe weiterleiten, um eine agentische Traffic-Datenerfassung in LLM Optimizer zu ermöglichen.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:53:26.846Z'
TQID: 'https://experienceleague.adobe.com/EPQ6GBjNXpIwYTuzj1xDKkIzuFLOWFPmu0lqSGUAX3I'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 2%

---


# Übersicht über die BYOCDN-Protokollweiterleitung {#cdn-log-forwarding}

Die Protokollweiterleitung für ein vom Kunden verwaltetes CDN (BYOCDN) ist der Prozess des Sendens Ihrer CDN-Zugriffsprotokolle an den Amazon S3-Bucket von Adobe, damit LLM Optimizer agentische Traffic-Daten erfassen und analysieren kann. Ohne CDN-Protokollweiterleitung kann das Dashboard [Agent Traffic](/help/dashboards/agentic-traffic.md) keine Metriken anzeigen.

Die unten bereitgestellten Handbücher folgen demselben zweiphasigen Workflow:

1. **In LLM Optimizer integrieren** - Registrieren Sie Ihr CDN auf der Seite [CDN-Konfiguration](/help/dashboards/customer-configuration.md), um die erforderlichen S3-Anmeldeinformationen und -Pfaddetails zu generieren.
2. **Konfigurieren Ihres CDN** - Verwenden Sie diese Details, um einen Protokollweiterleitungsauftrag (oder das manuelle Hochladen von Protokollen) in der Konsole Ihres CDN-Anbieters zu erstellen. Für CloudFront können Sie die Konsole verwenden oder die Bereitstellungseinrichtung nur mit der **AWS CLI** abschließen. Siehe [CloudFront (AWS CLI)](/help/overview/log-forwarding/cloudfront-cli.md).

## CDN-Anbieter {#cdn-providers}

Befolgen Sie die entsprechende Anleitung für Ihren CDN-Provider.

| CDN-Anbieter | Handbuch |
|---|---|
| Akamai | [Handbuch anzeigen](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Handbuch anzeigen](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (Konsole) | [Handbuch anzeigen](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (AWS CLI) | [Handbuch anzeigen](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Handbuch anzeigen](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Handbuch anzeigen](/help/overview/log-forwarding/imperva.md) |
| Sonstiges (manuelles/nicht unterstütztes CDN) | [Handbuch anzeigen](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Wenn Ihr CDN-Anbieter oben nicht aufgeführt ist, verwenden Sie das Handbuch **Sonstiges (manuelles/nicht unterstütztes CDN)** , das manuelle Uploads, Ad-hoc-Skripte und alle nicht nativ unterstützten CDN behandelt.
