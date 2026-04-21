---
source-git-commit: b13f91d144d4899198891c4dcd841de8cfbb2355
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---
# Snippets

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

Weitere Informationen zu „Optimieren bei Edge&quot;, einschließlich verfügbarer Opportunitys, Workflows für die automatische Optimierung und häufig gestellte Fragen, finden Sie unter &quot;[&#x200B; bei Edge - Überblick](/help/dashboards/optimize-at-edge/overview.md).
