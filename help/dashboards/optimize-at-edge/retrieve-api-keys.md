---
title: Abrufen Ihrer API-Schlüssel
description: So rufen Sie Ihre Edge Optimize-API-Schlüssel für Produktion und Staging von LLM Optimizer ab.
feature: Opportunities
autotag-review: '2026-07-15T18:05:12.505Z'
TQID: 'https://experienceleague.adobe.com/X3vIzxrlaqJ5Mx3K8rOpX2QqgGyxT6p8qfdLzTWC1gQ'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 100%

---


# Abrufen Ihrer API-Schlüssel

Bevor Sie Ihr CDN konfigurieren, rufen Sie Ihre Edge Optimize-API-Schlüssel über die LLM Optimizer-Benutzeroberfläche ab. Für den Live-Traffic benötigen Sie einen **Produktions**-API-Schlüssel. Optional können Sie auch einen **Staging**-API-Schlüssel abrufen, um das Routing zunächst auf einem Staging-Hostnamen zu testen.

## Produktions-API-Schlüssel

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration**.

   ![Navigieren zu „Kundenkonfiguration“](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Suchen Sie den Abschnitt **Optimierungen für AI Agents bereitstellen**. Aktivieren Sie das Kontrollkästchen **Optimierungs-Engine aktivieren**.

   ![Optimierungen für AI Agents bereitstellen – ausstehend](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Wählen Sie im Bestätigungsdialogfeld **Aktivieren** aus.

   ![Bestätigungsdialog „Optimierungs-Engine aktivieren“](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Wählen Sie **Details anzeigen** aus. Kopieren Sie im Dialogfeld **Optimierungsdetails bereitstellen** den **Produktions-API-Schlüssel** (verwenden Sie **Kopieren** neben dem Feld).

   ![Produktions-API-Schlüssel in „Optimierungsdetails bereitstellen“](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >Im Dialogfeld wird möglicherweise angezeigt, dass die Einrichtung nicht abgeschlossen ist. Dies ist normal, solange das Routing noch nicht verifiziert ist. Sie können den API-Schlüssel aber trotzdem kopieren, damit Ihr IT- oder CDN-Team die Konfiguration abschließen kann.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich an Ihr Adobe-Accountteam oder an `llmo-at-edge@adobe.com`.

## Staging-API-Schlüssel (optional)

Um das Routing in einer Testumgebung zu validieren, bevor das Produktions-Routing aktiviert wird, können Sie einen Staging-Hostnamen konfigurieren.

**Voraussetzungen**

* Der Staging-Hostname muss sich auf **derselben registrierbaren Domain** befinden wie der Produktions-Hostname (z. B.`https://staging.example.com`, wenn der Produktions-Hostname `https://www.example.com` lautet).
* Nur **eine** Staging-Domain pro Site. Nach dem Speichern kann die Datei nur noch durch Kontaktaufnahme mit Adobe geändert werden.

**Schritte**

1. Navigieren Sie in LLM Optimizer zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.
2. Wählen Sie unter **Optimierungen für AI Agents bereitstellen** **Staging-Domain hinzufügen** (oder **Staging-Domain**, falls bereits eine Staging-Domain konfiguriert ist).
3. Geben Sie die vollständige Staging-URL einschließlich `https://` ein und wählen Sie **Domain festlegen**.
4. Kopieren Sie den **Staging**-API-Schlüssel aus dem Bestätigungsdialogfeld.

   ![Staging-Domain-API-Schlüssel](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Stellen Sie dieselben Routing-Regeln in Ihrer Staging-Umgebung mithilfe des Staging-API-Schlüssels bereit.

Wenn Sie Hilfe benötigen, wenden Sie sich an `llmo-at-edge@adobe.com`.

## Nächste Schritte

Nachdem Sie Ihre API-Schlüssel abgerufen haben, kehren Sie zu Ihrem [CDN-Einrichtungshandbuch](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) zurück, um das Routing zu konfigurieren.
