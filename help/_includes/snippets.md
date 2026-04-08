---
source-git-commit: da789100d814004687de2f46e18a295671dec4b8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---
# Snippets

## Schritte zum Abrufen von API-Schlüsseln {#retrieve-byocdn-api-key}

**Schritte zum Abrufen Ihres Produktions-API-Schlüssels für Edge Optimize:**

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

   ![Navigieren Sie zur Kundenkonfiguration](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Suchen Sie den Abschnitt **Optimierungen für KI-Agenten bereitstellen**. Markieren Sie das **Optimierungs-Engine aktivieren**.

   ![Optimierungen für KI-Agenten bereitstellen - Ausstehend](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Wählen Sie im Bestätigungsdialog die Option **Aktivieren** aus.

   ![Bestätigungsdialogfeld für Optimierungsmodul aktivieren](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Wählen Sie **Details anzeigen** aus. Kopieren Sie im Dialogfeld **Optimierungsdetails bereitstellen** den **Produktions-API-Schlüssel** (verwenden Sie **Kopieren** neben dem Feld).

   ![Produktions-API-Schlüssel in den Details zur Bereitstellungsoptimierung](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >Das Dialogfeld zeigt möglicherweise an, dass die Einrichtung nicht abgeschlossen ist. Dies wird erwartet, bis das Routing überprüft wird - Sie können weiterhin den API-Schlüssel kopieren, damit Ihr IT- oder CDN-Team die Konfiguration abschließen kann.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich außerdem an Ihr Adobe-Account-Team oder an Ihren `llmo-at-edge@adobe.com`.

## Staging-Domain-API-Schlüssel (optional) {#retrieve-staging-edge-optimize-api-key}

Verwenden Sie einen Staging-Host-Namen, wenn Sie die Option Optimieren in Edge in einer niedrigeren Umgebung testen möchten, bevor der Produktions-Traffic die Routing-Regeln verwendet.

**Voraussetzungen**

* Der Staging-Hostname muss zur **gleichen registrierbaren Domain** wie Ihre Produktions-Site gehören (z. B. `https://staging.example.com` wenn die Produktion `https://www.example.com` wird).
* Für **Website kann nur** eine) Staging-Domain konfiguriert werden. Nachdem er gespeichert wurde, kann er ohne Hilfe nicht mehr geändert werden.

**Schritte**

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

2. Wählen Sie **Abschnitt „Optimierungen für KI** Agenten bereitstellen“ die Option **Staging-Domain hinzufügen** (oder **Staging-Domain**, wenn bereits eine Staging-Domain konfiguriert ist).

3. Geben Sie im Dialogfeld **Staging** die vollständige Staging-URL einschließlich `https://` ein und wählen Sie **Domain festlegen**.

   ![Dialogfeld „Domain-Eingabe bereitstellen“](/help/assets/optimize-at-edge/byocdn-staging-domain-input.png)

4. Bestätigen Sie die Domain in der nächsten Eingabeaufforderung. Wenn der Workflow abgeschlossen ist, zeigt **Dialogfeld „Staging-**&quot; die konfigurierte Domain und ihren **API-Schlüssel** an. Wählen Sie **Kopieren** aus, um den Schlüssel der Staging-API zu kopieren.

   ![Staging-Domain-API-Schlüssel](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Wenn Sie Hilfe benötigen, wenden Sie sich an `llmo-at-edge@adobe.com`.

## Routing-Status in LLM Optimizer überprüfen {#verify-routing-status-in-ui}

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![Optimierung für KI-Agenten bereitstellen - abgeschlossen](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Zurück zur Übersicht {#return-to-overview}

Weitere Informationen zu „Optimieren bei Edge&quot;, einschließlich verfügbarer Opportunitys, Workflows für die automatische Optimierung und häufig gestellte Fragen, finden Sie unter &quot;[&#x200B; bei Edge - Überblick](/help/dashboards/optimize-at-edge/overview.md).
