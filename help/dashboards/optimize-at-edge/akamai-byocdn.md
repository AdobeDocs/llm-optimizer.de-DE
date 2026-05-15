---
title: Optimize at Edge – Akamai (BYOCDN)
description: Erfahren Sie, wie Sie Akamai BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-05-15T17:34:47.891Z'
TQID: 'https://experienceleague.adobe.com/oGtqsnvHYn0BSNLl40-KpVl0TjCZHESRgH1LcVmjOiY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 809
ht-degree: 62%

---


# Akamai (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Bevor Sie die Regeln für den Akamai Property Manager einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Zugriff auf den Akamai Property Manager für Ihre Domain.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Anweisungen hierzu finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Informationen zum Testen des Staging-Routings finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Konfiguration**

Die folgende Akamai Property Manager-Regel leitet den Seitendatenverkehr von Agent HTML an Edge Optimize weiter. Die Konfiguration umfasst die folgenden Schritte:

**1. Routing-Kriterien festlegen (Traffic-Übereinstimmung zwischen Benutzeragent und HTML)**

Legen Sie das Routing für die folgenden Benutzeragenten fest:

```
 *AdobeEdgeOptimize-AI*
 *ChatGPT-User*
 *GPTBot*
 *OAI-SearchBot*
 *PerplexityBot*
 *Perplexity-User*
```

>[!NOTE]
>
>Wenden Sie die Routingregel „Optimieren bei Edge&quot; nur auf den agenten HTML-Seiten-Traffic an. Bei einer gängigen Einrichtung werden anforderungsseitige Kriterien wie &quot;**&quot; verwendet** um `html` und `EMPTY_STRING` für Seiten-URLs ohne Erweiterung abzugleichen. Wenn Ihre Site HTML über andere URL-Muster bereitstellt oder erweiterungslose Nicht-Seiten-Routen wie API-Endpunkte enthält, verfeinern Sie die Regel mit zusätzlichen pfadbasierten Kriterien.

![Festlegen von Routing-Kriterien](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Festlegen der Herkunft und des SSL-Verhaltens**

Festlegen der Herkunft als `live.edgeoptimize.net` und von „SAN zuordnen“ auf `*.edgeoptimize.net`

>[!NOTE]
>
>Wenn die Eigenschaftenaktivierung nach dem Hinzufügen der Regel „Optimieren bei Edge&quot; fehlschlägt, überprüfen Sie, ob die Regel einen anderen SSL-Verifizierungsmodus für den Ursprungs-Server verwendet als die Standardregel. Wenn dies der Fall ist, aktualisieren Sie die Regel „Optimieren unter Edge&quot;, um sie an die Standardregel anzupassen. Wenn die Standardregel beispielsweise &quot;**&quot; verwendet** verwenden Sie auch **Plattformeinstellungen** hier. Wenn Sie die erforderliche Einstellung nicht verwenden können, wenden Sie sich an den Akamai-Support.

![Festlegen der Herkunft und des SSL-Verhaltens](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Festlegen der Cache-Schlüsselvariablen**

Festlegen der Cache-Schlüsselvariablen `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` auf `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Festlegen der Cache-Schlüsselvariablen](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Caching-Regeln**

![Caching-Regeln](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Ändern der eingehenden Anfrage-Header**

Legen Sie die folgenden Header für eingehende Anfragen fest:
`x-edgeoptimize-api-key` zum von LLMO abgerufenen API-Schlüssel
`x-edgeoptimize-config` in `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` zu `{{builtin.AK_URL}}`

![Ändern der eingehenden Anfrage-Header](/help/assets/optimize-at-edge/akamai-step5-request.png)

**Zulassen, dass in Edge durch Firewall-Regeln optimiert wird (optional)**

{{waf-allowlist-setup}}

![Legen Sie die Kopfzeile „x-edgeOptimize-fetcher-key“ im Eigenschaften-Manager fest](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Zulassungsliste des `*AdobeEdgeOptimize/1.0*`-Benutzeragenten und der `x-edgeoptimize-fetcher-key`-Kopfzeile in Akamai Bot Manager.

**6. Ändern der eingehenden Antwort-Header**

![Ändern der eingehenden Antwort-Header](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Cache-ID-Änderung**

![Cache-ID-Änderung](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Ändern der ausgehenden Anfrage-Header**

Festlegen des `x-forwarded-host`-Headers auf `{{builtin.AK_HOST}}`

![Ändern der ausgehenden Anfrage-Header](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Site-Failover**

Die Site-Failover-Konfiguration besteht aus zwei Teilen: dem Failover-Verhalten (konfiguriert innerhalb der Haupt-Routing-Regel von „optimize-at-edge“) und einer separaten Header-Regel für den Failover-Test.

**9a. Verhalten bei Site-Failover (innerhalb der Haupt-Routing-Regel von „optimize-at-edge“)**

Konfigurieren Sie innerhalb der Haupt-Routing-Regel das Verhalten bei Site-Failover und das erweiterte XML-Snippet wie folgt:

>[!IMPORTANT]
>
>Das XML-Fragment in diesem Schritt erfordert das **Erweitert**-Verhalten. In einigen Akamai-Umgebungen ist dieses Verhalten nicht für die Self-Service-Bearbeitung verfügbar. Wenn die Option **Erweitert** nicht angezeigt wird, wenden Sie sich an Ihr Akamai-Account-Team oder den Akamai-Support, um die erforderliche Konfiguration zu aktivieren.

![Site-Failover](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Fügen Sie den Anfrage-Header `x-edgeoptimize-request` mit dem Wert `fo` über Advanced XML hinzu:

```
<forward:availability.fail-action2>
<add-header>
<status>on</status>
<name>x-edgeoptimize-request</name>
<value>fo</value>
</add-header>
</forward:availability.fail-action2>
```

![Failover-Verhalten](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

**9b. Header-Regel für Failover-Test (gleichrangige Regel)**

>[!IMPORTANT]
>
>Erstellen Sie die Regel **EdgeOptimize Failover – Test-Header** als **gleichrangige Regel** (auf derselben Ebene) der Routing-Regeln – **nicht** in diese verschachtelt. In der Regelstruktur des Akamai Property Manager sollte die Hierarchie wie folgt aussehen:
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>Dadurch wird sichergestellt, dass die Header-Regel des Failover-Tests für **alle** Routing-Regeln und nicht nur für eine bewertet wird.
>
>Stellen Sie außerdem sicher **dass die Regel „Optimieren bei Edge-Routing** nicht durch eine spätere Übereinstimmungsregel überschrieben wird, die den Ursprung, das Caching-Verhalten oder die Cache-ID für dieselben Anfragen ändert. Wenn diese Verhaltensweisen durch eine andere übereinstimmende Regel zurückgesetzt werden, funktioniert das Routing oder Caching von Optimieren bei Edge möglicherweise nicht wie erwartet.

Wenn der Wert des Anfrage-Headers `x-edgeoptimize-request` gleich `fo` ist, legen Sie den ausgehenden Antwort-Header `x-edgeoptimize-fo` auf `true` fest.

![Failover-Regeln](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Site-Failover stellt sicher, dass die Anfrage automatisch an Ihren Standardursprung zurückgeleitet wird, wenn Edge Optimize einen `4XX`- oder `5XX`-Fehler zurückgibt, sodass der bzw. die Endbenutzende weiterhin eine Antwort erhält.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` zurück | Der Client erhält eine optimierte Antwort. |
| Edge Optimize gibt `4XX` oder `5XX` zurück | Die Anfrage wird an den Standardursprung zurückgeleitet. |

**Überprüfen des Setups**

Stellen Sie nach Abschluss des Setups sicher, dass Bot-Traffic an Edge Optimize weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

**1. Testen des Bot-Traffics (sollte optimiert werden)**

Simulieren Sie eine KI-Bot-Anfrage mithilfe eines Agent-basierten Benutzer-Agents:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Eine erfolgreiche Antwort enthält den `x-edgeoptimize-request-id`-Header, der bestätigt, dass die Anfrage über Edge Optimize weitergeleitet wurde:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Testen des menschlichen Traffics (sollte NICHT betroffen sein)**

Simulieren Sie eine normale menschliche Browser-Anfrage:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

Die Antwort sollte **nicht** den `x-edgeoptimize-request-id`-Header enthalten. Der Seiteninhalt und die Antwortzeit sollten nach der Aktivierung von „Optimize at Edge“ unverändert bleiben.

**3. So lassen sich die beiden Szenarien voneinander unterscheiden**

| Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Traffic (nicht betroffen) |
|---|---|---|
| `x-edgeoptimize-request-id` | Vorhanden – enthält eine eindeutige Anfrage-ID | Abwesend |
| `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover stattgefunden hat (Wert: `1`) | Abwesend |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
