---
title: Abrufen Ihrer API-Schlüssel
description: Abrufen der Produktions- und Staging-API-Schlüssel von Edge Optimize aus LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:58:10.897Z'
TQID: 'https://experienceleague.adobe.com/4R-cx6wv75Oowj9ZvEPGCzQbQBSoppgDuI5Ut1IbObA'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 1%

---


# Abrufen Ihrer API-Schlüssel

Rufen Sie vor dem Konfigurieren Ihres CDN Ihre Edge Optimize-API-Schlüssel von der LLM Optimizer-Benutzeroberfläche ab. Sie benötigen einen **Produktions** API-Schlüssel für Live-Traffic. Optional können Sie auch einen API-Schlüssel **Staging** abrufen, um das Routing zuerst auf einem Staging-Host-Namen zu testen.

## Produktions-API-Schlüssel

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

   ![Navigieren zu „Kundenkonfiguration“](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Suchen Sie den Abschnitt **Optimierungen für KI-Agenten bereitstellen**. Markieren Sie das **Optimierungs-Engine aktivieren**.

   ![Optimierungen für KI-Agenten bereitstellen - Ausstehend](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Wählen Sie im Bestätigungsdialog die Option **Aktivieren** aus.

   ![Bestätigungsdialogfeld für Optimierungsmodul aktivieren](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Wählen Sie **Details anzeigen** aus. Kopieren Sie im Dialogfeld **Optimierungsdetails bereitstellen** den **Produktions-API-Schlüssel** (verwenden Sie **Kopieren** neben dem Feld).

   ![Produktions-API-Schlüssel in den Details zur Bereitstellungsoptimierung](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >Das Dialogfeld zeigt möglicherweise an, dass die Einrichtung nicht abgeschlossen ist. Dies wird erwartet, bis das Routing überprüft wird - Sie können weiterhin den API-Schlüssel kopieren, damit Ihr IT- oder CDN-Team die Konfiguration abschließen kann.

Wenn Sie Hilfe bei den oben genannten Schritten benötigen, wenden Sie sich an Ihr Adobe-Account-Team oder `llmo-at-edge@adobe.com`.

## Staging-API-Schlüssel (optional)

Um das Routing in einer niedrigeren Umgebung zu validieren, bevor Sie das Produktions-Routing aktivieren, können Sie einen Staging-Host-Namen konfigurieren.

**Anforderungen**

* Der Staging-Hostname muss sich auf derselben **registrierbaren Domain** wie die Produktion befinden (z. B. `https://staging.example.com`, wenn die Produktion `https://www.example.com` wird).
* Nur **eine** Staging-Domain pro Site. Nachdem er gespeichert wurde, kann er nicht mehr geändert werden, ohne Adobe zu kontaktieren.

**Schritte**

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.
2. Wählen **unter „Optimierungen für KI** Agenten bereitstellen“ die Option **Staging-Domain hinzufügen** (oder **Staging-Domain**, wenn bereits eine Staging-Domain konfiguriert ist).
3. Geben Sie die vollständige Staging-URL einschließlich `https://` ein und wählen Sie **Domain festlegen**.
4. Kopieren Sie den **Staging** API-Schlüssel aus dem Bestätigungsdialogfeld.

   ![Staging-Domain-API-Schlüssel](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Stellen Sie dieselben Routing-Regeln mithilfe des Staging-API-Schlüssels in Ihrer Staging-Umgebung bereit.

Wenn Sie Hilfe benötigen, wenden Sie sich an `llmo-at-edge@adobe.com`.

## Nächste Schritte

Nachdem Sie Ihre API-Schlüssel abgerufen haben, kehren Sie zu Ihrem [CDN-Setup-Handbuch](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) zurück, um das Routing zu konfigurieren.
