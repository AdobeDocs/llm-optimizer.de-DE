---
title: BYOCDN-Protokollweiterleitung – Überblick
description: Erfahren Sie, wie Sie CDN-Protokolle von Ihrem Anbieter an den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer weiterleiten.
feature: Agentic Traffic
autotag-review: '2026-07-15T18:07:52.453Z'
TQID: 'https://experienceleague.adobe.com/iN1Tm-7j2FTQ1UodWvCZpOSy0FnQEyMkBMZIL9z3t38'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: dd952468-5202-43af-a365-6e0d2e67a703
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 100%

---


# BYOCDN-Protokollweiterleitung – Überblick {#cdn-log-forwarding}

Die Protokollweiterleitung für ein kundenseitig verwaltetes CDN (BYOCDN) ist der Prozess des Sendens Ihrer CDN-Zugriffsprotokolle an den Amazon S3-Bucket von Adobe, damit LLM Optimizer Daten zu Agent-basiertem Traffic erfassen und analysieren kann. Ohne CDN-Protokollweiterleitung kann das Dashboard [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md) keine Metriken anzeigen.

Die unten bereitgestellten Handbücher folgen demselben zweiphasigen Workflow:

1. **Durchführen des Onboardings in LLM Optimizer**: Registrieren Sie Ihr CDN auf der Seite [CDN-Konfiguration](/help/dashboards/customer-configuration.md), um die erforderlichen S3-Anmeldedaten und Pfaddetails zu generieren.
2. **Konfigurieren Ihres CDN**: Verwenden Sie diese Details, um einen Protokollweiterleitungsauftrag (oder das manuelle Hochladen von Protokollen) in der Konsole Ihres CDN-Anbieters zu erstellen. Für CloudFront können Sie die Konsole verwenden oder die Bereitstellungseinrichtung nur mit der **AWS-CLI** abschließen. Siehe [CloudFront (AWS-CLI)](/help/overview/log-forwarding/cloudfront-cli.md).

## CDN-Anbieter {#cdn-providers}

Befolgen Sie das entsprechende Handbuch für Ihren CDN-Anbieter.

| CDN-Anbieter | Handbuch |
|---|---|
| Akamai | [Handbuch anzeigen](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Handbuch anzeigen](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (Konsole) | [Handbuch anzeigen](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (AWS-CLI) | [Handbuch anzeigen](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Handbuch anzeigen](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Handbuch anzeigen](/help/overview/log-forwarding/imperva.md) |
| Andere Anbieter (manuelles/nicht unterstütztes CDN) | [Handbuch anzeigen](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Wenn Ihr CDN-Anbieter oben nicht aufgeführt ist, verwenden Sie das Handbuch **Anderer Anbieter (manuelles/nicht unterstütztes CDN)**, das manuelle Uploads, Ad-hoc-Skripte und jedes nicht nativ unterstützte CDN behandelt.
