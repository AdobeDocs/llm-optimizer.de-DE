---
source-git-commit: e9309dc8f8d1d81b953483f17dcb424e46d5cd3b
workflow-type: tm+mt
source-wordcount: '457'
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

## Optional: Testen des Routings für einen Staging-Host-Namen {#retrieve-staging-edge-optimize-api-key}

**Optional: Testrouting für einen Staging-Host-Namen**

Wenn Sie das Routing in einer niedrigeren Umgebung vor der Aktivierung des Produktions-Routing überprüfen möchten, können Sie einen Staging-Host-Namen konfigurieren.

**Anforderungen**

* Der Staging-Hostname muss sich auf derselben **registrierbaren Domain** wie die Produktion befinden (z. B. `https://staging.example.com`, wenn die Produktion `https://www.example.com` wird).
* Nur **eine** Staging-Domain pro Site. Nachdem er gespeichert wurde, kann er nicht mehr geändert werden, ohne Adobe zu kontaktieren.

**Rufen Sie Ihren Staging-API-Schlüssel ab**

1. Öffnen Sie **Kundenkonfiguration** und wählen Sie **CDN-Konfiguration** aus.
2. Wählen **unter „Optimierungen für KI** Agenten bereitstellen“ die Option **Staging-Domain hinzufügen** (oder **Staging-Domain**, wenn bereits eine Staging-Domain konfiguriert ist).
3. Geben Sie die vollständige Staging-URL einschließlich `https://` ein und wählen Sie **Domain festlegen**.
4. Kopieren Sie den **Staging** API-Schlüssel aus dem Bestätigungsdialogfeld.

![Staging-Domain-API-Schlüssel](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Stellen Sie dieselben Routing-Regeln mithilfe des Staging-API-Schlüssels in Ihrer Staging-Umgebung bereit.

**Staging-Bot-Traffic testen**

Ersetzen Sie `https://staging.example.com/page.html` durch Ihre echte Staging-URL und Ihren Pfad. **Erfolg:** Die Antwort enthält die `x-edgeoptimize-request-id`.

Wenn Sie Hilfe benötigen, wenden Sie sich an `llmo-at-edge@adobe.com`.

## Routing-Status in LLM Optimizer überprüfen {#verify-routing-status-in-ui}

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![Optimierung für KI-Agenten bereitstellen - abgeschlossen](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Zulassen der Optimierung bei Edge durch Firewall-Regeln (optional) {#waf-allowlist-setup}

Wenn Ihr CDN einen WAF oder Bot Manager verwendet:

* Zulassungsliste des `*AdobeEdgeOptimize/1.0*`-Benutzeragenten in WAF oder Bot-Manager, damit der Service „Optimieren unter Edge&quot; Ihre Ursprungs-Inhalte abrufen kann.
* Wenn Ihre Firewall eine zusätzliche Überprüfung über den Benutzeragenten hinaus erfordert, generieren Sie ein Geheimnis (z. B. `openssl rand -hex 32`) und:
   * Fügen Sie `x-edgeoptimize-fetcher-key` mit dem Geheimnis in Ihren Routing-Regeln zusammen mit den anderen `x-edgeoptimize-*` Kopfzeilen hinzu.
   * Fügen Sie eine WAF- oder Bot-Manager-Regel hinzu, um Anfragen zuzulassen, bei denen `x-edgeoptimize-fetcher-key` mit demselben Geheimnis übereinstimmt.
* Bei Edge optimieren leitet diese Kopfzeile unverändert weiter - Sie besitzen den gesamten Schlüssellebenszyklus.

## Zurück zur Übersicht {#return-to-overview}

Weitere Informationen zu „Optimieren bei Edge&quot;, einschließlich verfügbarer Opportunitys, Workflows für die automatische Optimierung und häufig gestellte Fragen, finden Sie unter &quot;[ bei Edge - Überblick](/help/dashboards/optimize-at-edge/overview.md).
