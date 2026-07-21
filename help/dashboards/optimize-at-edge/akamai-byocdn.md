---
title: Optimize at Edge – Akamai (BYOCDN)
description: Erfahren Sie, wie Sie Akamai BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-07-15T17:40:02.356Z'
TQID: 'https://experienceleague.adobe.com/XlHpXbtxqPl-XQQKWeQc3rbsizCT7U0TF1bQkyv0iM8'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 9d2324e23e07f01e16c4fc16c96213d03214918f
workflow-type: tm+mt
source-wordcount: 795
ht-degree: 76%

---


# Akamai (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Bevor Sie die Regeln für den Akamai Property Manager einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Zugriff auf den Akamai Property Manager für Ihre Domain.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Konfiguration**

Die folgende Regel von Akamai Property Manager leitet Agent-basierten HTML-Seiten-Traffic an Edge Optimize weiter. Die Konfiguration umfasst die folgenden Schritte:

**1. Festlegen von Routing-Kriterien (Zuordnung von Benutzer-Agent und HTML-Traffic)**

Festlegen von Routing für die folgenden Benutzer-Agents:

```
 *AdobeEdgeOptimize-AI*
 *ChatGPT-User*
 *GPTBot*
 *OAI-SearchBot*
 *PerplexityBot*
 *Perplexity-User*
 *ClaudeBot*
 *Claude-User*
 *Claude-SearchBot*
```

>[!NOTE]
>
>Wenden Sie die Routing-Regel „Optimize at Edge“ nur auf Agent-basierten HTML-Seiten-Traffic an. Eine gängige Vorgehensweise ist die Verwendung von anfrageseitigen Kriterien wie **Dateierweiterung**, um `html` und `EMPTY_STRING` für Seiten-URLs ohne Erweiterung abzugleichen. Wenn Ihre Site HTML von anderen URL-Mustern bereitstellt oder nicht seitenbezogene Routen ohne Erweiterung wie API-Endpunkte enthält, verfeinern Sie die Regel mit zusätzlichen pfadbasierten Kriterien.

![Festlegen von Routing-Kriterien](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Festlegen der Herkunft und des SSL-Verhaltens**

Festlegen der Herkunft als `live.edgeoptimize.net` und von „SAN zuordnen“ auf `*.edgeoptimize.net`

>[!NOTE]
>
>Falls die Eigenschaftenaktivierung nach dem Hinzufügen der Regel „Optimize at Edge“ fehlschlägt, überprüfen Sie, ob die Regel einen anderen SSL-Verifizierungsmodus für den Ursprungsserver verwendet als die Standardregel. Falls dies der Fall ist, aktualisieren Sie die Regel „Optimize at Edge“, sodass sie der Standardregel entspricht. Wenn die Standardregel beispielsweise **Plattformeinstellungen** verwendet, verwenden Sie hier auch **Plattformeinstellungen**. Falls Sie die erforderliche Einstellung nicht verwenden können, wenden Sie sich bitte an den Akamai-Support.

![Festlegen der Herkunft und des SSL-Verhaltens](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Festlegen der Cache-Schlüsselvariablen**

Festlegen der Cache-Schlüsselvariablen `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` auf `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Festlegen der Cache-Schlüsselvariablen](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Caching-Regeln**

![Caching-Regeln](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Ändern der eingehenden Anfrage-Header**

Legen Sie folgende eingehende Anfrage-Header fest:
`x-edgeoptimize-api-key` auf den von LLMO abgerufenen API-Schlüssel
`x-edgeoptimize-config` in `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` auf `{{builtin.AK_URL}}`

![Ändern der eingehenden Anfrage-Header](/help/assets/optimize-at-edge/akamai-step5-request.png)

**Zulassen von „Optimize at Edge“ durch Firewall-Regeln (optional)**

{{waf-allowlist-setup}}

![Festlegen des x-edgeoptimize-fetcher-key-Headers im Property Manager](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Setzen Sie außerdem denBenutzer-Agent `*AdobeEdgeOptimize/1.0*` und den Header `x-edgeoptimize-fetcher-key` im Akamai Bot Manager auf die Zulassungsliste.

**6. Ändern der eingehenden Antwort-Header**

![Ändern der eingehenden Antwort-Header](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Cache-ID-Änderung**

![Cache-ID-Änderung](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Ändern der ausgehenden Anfrage-Header**

Festlegen des `x-forwarded-host`-Headers auf `{{builtin.AK_HOST}}`

![Ändern der ausgehenden Anfrage-Header](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Site-Failover**

Die Site-Failover-Konfiguration besteht aus zwei Teilen: einem Failover-Verhalten innerhalb der Haupt-Routing-Regel von Optimize at Edge und einer gleichrangigen Regel, die eine Antwort-Kopfzeile hinzufügt, wenn ein Fallback erfolgt.

**9a. Konfigurieren des Site-Failover-Verhaltens**

Erstellen Sie innerhalb der Routingregel „Optimieren bei Edge&quot; eine untergeordnete Regel mit dem Namen **Site-Failover-Verhalten**. Setzen Sie ihn auf **Übereinstimmung mit &quot;**&quot; und fügen Sie die folgenden Kriterien hinzu:

* **Antwort-Status-**) liegt im Bereich `400` bis `599`.
* **Ursprungs-Timeout** ist `Yes`.

![Site-Failover](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Konfigurieren des Site-Failover-Verhaltens](/help/assets/optimize-at-edge/akamai-step9-failover-settings.png)

**9b. Konfigurieren der Header-Regel für die Failover-Antwort**

>[!IMPORTANT]
>
>Erstellen Sie die Regel **EdgeOptimize Failover – Test-Header** als **gleichrangige Regel** (auf derselben Ebene) der Routing-Regeln – **nicht** in diese verschachtelt. In der Regelstruktur des Akamai Property Manager sollte die Hierarchie wie folgt aussehen:
>
>```
>▼ Optimize at Edge                         ← parent rule group
>   ▼ Optimize at Edge Routing               ← routing child
>       Site Failover Behavior                 ← nested child
>   EdgeOptimize Failover - Test Header      ← sibling of routing child
>```
>
>Die gleichrangige Regel wird ausgewertet, wenn Akamai die fehlgeschlagene Anfrage für den ursprünglichen Host-Namen neu erstellt. Das API-Schlüsselkriterium in der Routing-Regel verhindert, dass diese Anfrage erneut an Edge Optimize gesendet wird.
>
>Stellen Sie außerdem sicher, dass die Regel **Optimize at Edge Routing** nicht durch eine spätere übereinstimmende Regel überschrieben wird, die den Ursprung, das Caching-Verhalten oder die Cache-ID für dieselben Anfragen ändert. Wenn eine andere übereinstimmende Regel diese Verhaltensweisen zurücksetzt, funktionieren Routing oder Caching der Art „Optimize at Edge“ möglicherweise nicht wie erwartet.

![Konfigurieren der Header-Regel für die Failover-Antwort](/help/assets/optimize-at-edge/akamai-step9-failover-header.png)

Site Failover stellt sicher, dass Akamai die Anfrage für Ihren ursprünglichen Hostnamen neu erstellt, wenn Edge Optimize einen Fehler zurückgibt oder eine Zeitüberschreitung auftritt, sodass der Besucher weiterhin die normale Antwort der Site erhält.

| Szenario | Verhalten |
| --- | --- |
| Edge Optimize gibt `2XX` oder `3XX` zurück | Die optimierte Antwort wird bereitgestellt. `x-edgeoptimize-request-id` ist vorhanden. |
| Edge Optimize gibt `4XX`-`5XX` zurück oder die Herkunft überschreitet das Zeitlimit | Die Anfrage wird für den ursprünglichen Host-Namen neu erstellt. Die Antwort enthält `x-edgeoptimize-fo: true`. |

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
| `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover stattgefunden hat (Wert: `true`) | Abwesend |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
