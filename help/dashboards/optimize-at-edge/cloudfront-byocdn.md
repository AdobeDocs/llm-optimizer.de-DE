---
title: Optimize at Edge – CloudFront (BYOCDN)
description: Erfahren Sie, wie Sie CloudFront BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-05-15T17:41:48.977Z'
TQID: 'https://experienceleague.adobe.com/fGlW2FIQooU-8nv8H1lH3WOxinOFUVK7RVNol7ACPq8'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 7097550211d1570d6ff65ab980f9a160f8d2a9e0
workflow-type: tm+mt
source-wordcount: 2343
ht-degree: 90%

---


# CloudFront (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Stellen Sie vor dem Einrichten der CloudFront-Konfiguration sicher, dass Sie über Folgendes verfügen:

* Eine vorhandene CloudFront-Verteilung für Ihre Website.
* AWS-IAM-Berechtigungen zum Erstellen von Lambda-Funktionen, IAM-Rollen, CloudFront-Verteilungen und Cache-Richtlinien.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Schritt 1: Erstellen von Edge Optimize-Ursprung**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Registerkarte „Ursprünge“

1. Klicken Sie auf **Ursprung erstellen**.

2. Konfigurieren Sie den Ursprung:
   * **Ursprungs-Domain:** `live.edgeoptimize.net`
   * **Name:** `EdgeOptimize_Origin`

3. Behalten Sie die Standardwerte aller anderen Felder bei.

4. Hinzufügen von benutzerdefinierten Headern:

   | Kopfzeile | Wert |
   |--------|-------|
   | `x-edgeoptimize-api-key` | Ihr API-Schlüssel |
   | `x-forwarded-host` | `www.example.com` |
   | `x-edgeoptimize-fetcher-key` | Ihr Abrufschlüssel (nur bei WAFS erforderlich) |

   Ersetzen Sie `www.example.com` durch Ihre tatsächliche Website-Domain und `Your API key` durch den vom Adobe-Support bereitgestellten Edge Optimize-API-Schlüssel.

5. Klicken Sie auf **Ursprung erstellen**.

![Erstellung des CloudFront-Ursprungs](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

**Schritt 2: Erstellen der Viewer-Anforderungsfunktion**

**Navigation:** AWS Console > CloudFront > Funktionen

1. Klicken Sie auf **Funktion erstellen**.

2. Konfigurieren:
   * **Name:** `edgeoptimize-routing`
   * **Laufzeit:** `cloudfront-js-2.0`

3. Ersetzen Sie den Standard-Code durch den Code von [viewer-request.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/cloudfront-function/viewer-request.js).

   Passen Sie vor der Veröffentlichung die folgenden Werte im Code an:

   * `YOUR_DEFAULT_ORIGIN`: Ersetzen Sie dies durch den Namen des vorhandenen Standardursprungs (zu finden unter CloudFront > Verteilungen > [Ihre Verteilung] > Registerkarte „Ursprünge“).
   * `TARGETED_PATHS`: Wählen Sie `null` aus, um alle HTML-Seiten einzuschließen, oder legen Sie ein Array spezifischer Pfade fest, z. B. `['/', '/products', '/about']`.

4. Klicken Sie auf **Änderungen speichern** > **Funktion veröffentlichen**.

![Erstellung einer CloudFront-Funktion](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


**Schritt 3: Konfigurieren der Cache-Richtlinie**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

Überprüfen Sie die derzeit mit Ihrem Verhalten verknüpfte Cache-Richtlinie. Klicken Sie für Ihr Verhalten auf **Bearbeiten** und navigieren Sie zum Abschnitt **Cache-Schlüssel und Ursprungsanfragen**, um Ihr Szenario zu identifizieren:

* **Szenario A (veraltet):** Es wird ein ausgewähltes Optionsfeld mit dem Label **Veraltete Cache-Einstellungen** angezeigt. Es gibt kein Dropdown-Menü mit Richtliniennamen. Stattdessen werden Inline-TTL- und Header-Einstellungen angezeigt.
* **Szenario B (benutzerdefinierte Richtlinie):** **Cache-Richtlinie** ist ausgewählt und ein von Ihnen oder Ihrem Team erstellter Richtlinienname wird angezeigt (keine von AWS bereitgestellte Richtlinie).
* **Szenario C (verwaltete Richtlinie):** **Cache-Richtlinie** ist ausgewählt und ein von AWS bereitgestellter Name wie `CachingOptimized`, `CachingDisabled` oder `CachingOptimizedForUncompressedObjects` wird angezeigt (diese können nicht bearbeitet werden).

**Szenario A: Veraltete Cache-Einstellungen**

Wenn für Ihr Verhalten veraltete Cache-Einstellungen verwendet werden:

1. Unter **Cache-Schlüssel und Ursprungsanfragen** wird Ihnen **Veraltete Cache-Einstellungen** als ausgewählt angezeigt.

2. Fügen Sie `x-edgeoptimize-config` und `x-edgeoptimize-url` zur Zulassungsliste **Header** hinzu:

   * Wählen Sie **Folgende Header einschließen** vom Dropdown-Menü aus.
   * Fügen Sie `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzu.
     ![Veraltetes CloudFront-Cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Wenn Sie **Alle** im Dropdown-Menü „Header“ ausgewählt haben, überspringen Sie diesen Schritt. Alle Header werden automatisch an den Ursprung weitergeleitet.

3. Überprüfen Sie die Einstellung für **Objekt-Caching**:

   * Wenn sie auf **Anpassen** festgelegt ist, wird empfohlen, die **Mindest-TTL** auf `0` festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.
   * Wenn sie auf **Ursprungs-Cache-Header verwenden** festgelegt ist, ist keine Änderung erforderlich.

4. Klicken Sie auf **Änderungen speichern**.

**Szenario B: Nicht veraltet mit einer benutzerdefinierten Cache-Richtlinie**

Wenn für Ihr Verhalten bereits eine benutzerdefinierte Cache-Richtlinie verwendet wird (eine von Ihnen erstellte und keine von AWS verwaltete Richtlinie):

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Klicken Sie auf Ihre bestehende Richtlinie.

2. Klicken Sie auf **Bearbeiten**.

3. Es wird empfohlen, &quot;**TTL“** &quot;`0`&quot; festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.
   ![TTL-Einstellungen für Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. Fügen Sie unter **Cache-Schlüsseleinstellungen** > **Header** zusammen mit Ihren bestehenden Einschlüssen `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzu.
   ![Cache-Richtlinien-Header](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Klicken Sie auf **Änderungen speichern**.

**Szenario C: Nicht veraltet mit einer verwalteten Cache-Richtlinie (AWS)**

Wenn für Ihr Verhalten eine von AWS verwaltete Cache-Richtlinie verwendet wird (z. B. `CachingOptimized`), können Sie sie nicht bearbeiten. Sie müssen eine neue benutzerdefinierte Cache-Richtlinie erstellen, die die vorhandenen verwalteten Richtlinieneinstellungen repliziert und die Edge Optimize-Header oben hinzufügt.

**Teil 1: Notieren der aktuellen Einstellungen für verwaltete Cache-Richtlinien**

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Suchen Sie die derzeit mit Ihrem Verhalten verbundene verwaltete Cache-Richtlinie (z. B. `CachingOptimized`) und klicken Sie darauf.

2. Notieren Sie sich alle vorhandenen Einstellungen:
   * Mindest-TTL, Maximal-TTL, Standard-TTL
   * Im Cache-Schlüssel enthaltene Header
   * Im Cache-Schlüssel enthaltene Cookies
   * Im Cache-Schlüssel enthaltene Abfragezeichenfolgen
   * Komprimierungsunterstützung (Gzip, Brotli)

**Teil 2: Erstellen einer neuen benutzerdefinierten Cache-Richtlinie mit denselben Einstellungen + Edge Optimize-Konfiguration**

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Klicken Sie auf **Cache-Richtlinie erstellen**.

2. **Name:** `edgeoptimize-cache`

   ![Cache-Richtlinienname](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Replizieren Sie alle in Teil 1 genannten Einstellungen mit den folgenden Änderungen:

   * Es wird empfohlen, die **Mindest-TTL** auf `0` festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.

   ![TTL-Einstellungen für Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * Schließen Sie unter **Cache-Schlüsseleinstellungen** > **Header** alle Elemente der verwalteten Richtline ein und fügen Sie `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzu.

   ![Cache-Richtlinien-Header](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Klicken Sie auf **Erstellen**.

5. Kehren Sie zu Ihrem Verhalten zurück und verknüpfen Sie die neu erstellte Richtlinie:

   **Navigation:** AWS Console > CloudFront > Verteilungen >[Ihre Verteilung] > Verhalten

   1. Bearbeiten Sie Ihr Verhalten.
   2. Wählen Sie unter **Cache-Schlüssel und Ursprungsanfragen** **Cache-Richtlinie** aus.
   3. Wählen Sie `edgeoptimize-cache` aus dem Dropdown-Menü aus.
   4. Klicken Sie auf **Änderungen speichern**.

**Schritt 4: Erstellen der Lambda@Edge-Funktion (Ursprungsanfrage und -antwort)**

>[!IMPORTANT]
>Lambda@Edge-Funktionen **müssen in der Region `us-east-1` (N. Virginia)** erstellt werden. Dies ist eine AWS-Anforderung. Obwohl die Funktion in `us-east-1` erstellt wurde, repliziert AWS sie automatisch an allen CloudFront-Edge-Speicherorten weltweit, sodass sie am nächsten Edge-Speicherort für den Viewer ausgeführt wird. Vergewissern Sie sich, dass Sie sich in der AWS-Konsole in der Region `us-east-1` befinden, bevor Sie fortfahren.

**Erstellen der Lambda-Funktion**

**Navigation:** AWS Console > Lambda

1. Klicken Sie auf **Funktion erstellen**.

2. Wählen Sie **Von Grund auf erstellen**.

3. Konfigurieren:
   * **Funktionsname:** `edgeoptimize-origin`
   * Behalten Sie die Standardwerte aller anderen Felder bei.

4. Klicken Sie auf **Funktion erstellen**.

5. Ersetzen Sie im Code-Editor den Standard-Code durch den Code von [origin-request-response.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/origin-request-response.js).

6. Klicken Sie auf **Bereitstellen**, um den Code zu speichern.

7. Notieren Sie den **Namen der Ausführungsrolle** der unter **Konfiguration** > **Berechtigungen** angezeigt wird (z. B. `edgeoptimize-origin-role-xxxxx`). Sie benötigen diese Information für die folgenden Schritte.

**Aktualisieren der Vertrauensrichtlinie der Ausführungsrolle**

Die automatisch erstellte Rolle sieht nur `lambda.amazonaws.com` als vertrauenswürdig an. Für Lambda@Edge müssen Sie auch `edgelambda.amazonaws.com` hinzufügen.

**Navigation:** AWS Console > IAM > Rollen > [Ihre Rolle aus dem vorherigen Schritt] > Registerkarte „Vertrauensstellungen“

1. Klicken Sie auf **Vertrauensrichtlinie bearbeiten**.

2. Ersetzen Sie die Richtlinie durch den Inhalt von [trust-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/trust-policy.json).

3. Klicken Sie auf **Richtlinie aktualisieren**.

>[!WARNING]
>Der `edgelambda.amazonaws.com`-Service-Prinzipal ist **erforderlich** für Lambda@Edge. Ohne ihn kann CloudFront Ihre Funktion nicht an Edge-Speicherorten aufrufen.

**Korrigieren der Berechtigungsrichtlinie für CloudWatch-Protokolle**

Die automatisch erstellte Rolle verfügt über eine`AWSLambdaBasicExecutionRole`-Richtlinie, die für reguläres Lambda konfiguriert ist und die falsche Region und den falschen Protokollgruppennamen für Lambda@Edge aufweist. Sie müssen sie aktualisieren.

**Navigation:** AWS Console > IAM > Rollen >[Ihre Rolle] > Registerkarte „Berechtigungen“ > klicken Sie auf den Namen der zugehörigen Richtlinie (z. B.`AWSLambdaBasicExecutionRole-xxxx`).

1. Klicken Sie auf **Bearbeiten**.

2. Ersetzen Sie die Richtlinie durch den Inhalt von [cloudwatch-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/cloudwatch-policy.json).

   Ersetzen Sie im JSON `ACCOUNT_ID` durch Ihre tatsächliche AWS-Konto-ID (zu finden in der oberen rechten Ecke der AWS Console) und `FUNCTION_NAME` durch den Namen Ihrer Lambda-Funktion (z. B.`edgeoptimize-origin`).

3. Klicken Sie auf **Änderungen speichern**.

>[!WARNING]
>Die Region im ARN muss `*` lauten. Lambda@Edge wird am nächstgelegenen Edge-Standort zum Viewer ausgeführt, daher werden die Protokolle in der Region des Edge-Standorts (z. B.`ap-south-1`, `eu-west-1`) in CloudWatch geschrieben und nicht unbedingt in `us-east-1`. Die Protokollgruppe verwendet einen Namen mit dem Präfix der Region: `/aws/lambda/us-east-1.FUNCTION_NAME`, wobei `us-east-1` immer die Heimatregion der Funktion ist.

**Korrigieren Sie den Link CloudWatch-Protokolle**

Standardmäßig verweist der **CloudWatch-Protokolle anzeigen** Tastaturbefehl in der Lambda-Konsole auf `/aws/lambda/FUNCTION_NAME` in `us-east-1` - die falsche Protokollgruppe für Lambda@Edge. Konfigurieren Sie eine benutzerdefinierte Protokollgruppe so, dass der Link auf den richtigen Pfad verweist.

**Navigation:** AWS Console > Lambda > [Ihre Funktion] > Konfiguration > Überwachungs- und Betriebswerkzeuge

1. Klicken Sie auf **Bearbeiten**.

2. Wählen **unter „CloudWatch-Protokollgruppe** die Option **Benutzerdefiniert** aus.

3. Legen Sie den benutzerdefinierten Protokollgruppennamen auf `/aws/lambda/us-east-1.edgeoptimize-origin` fest.

4. Lassen **unter** das Kontrollkästchen **Erforderliche Berechtigungen hinzufügen** (**)**.

   ![Lambda-Konfiguration für benutzerdefinierte Protokollgruppen](/help/assets/optimize-at-edge/cloudfront-lambda-custom-log-group.png)

5. Klicken Sie auf **Speichern**.

>[!NOTE]
>Auch nach dieser Fehlerbehebung wird der Link **CloudWatch-** anzeigen) den richtigen Protokollgruppennamen öffnen, aber möglicherweise keine Daten anzeigen, wenn Sie sich in der falschen Region befinden. Lambda@Edge-Protokolle werden in der Edge-Region geschrieben, die die Anfrage verarbeitet hat (z. B. `eu-west-1`, `ap-south-1`), nicht `us-east-1`. Sie müssen weiterhin zur richtigen Region in CloudWatch wechseln, um die Protokolle anzuzeigen.

**Veröffentlichen einer Version**

1. Klicken Sie auf der Funktionsseite auf **Aktionen** (oben rechts) > **Neue Version veröffentlichen**.

2. Fügen Sie eine Beschreibung hinzu.

3. Klicken Sie auf **Veröffentlichen**.
   ![Lambda-Veröffentlichung](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Notieren Sie sich den **Funktions-ARN**. Sie benötigen diesen im nächsten Schritt.
   ![Lambda-ARN](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

**Schritt 5: Verknüpfen von Funktionen und Cache-Richtlinie mit Verhalten**

**Navigation:** AWS Console > CloudFront > Verteilungen >[Ihre Verteilung] > Verhalten

1. Bearbeiten Sie Ihr Verhalten.

2. Wenn Sie in Schritt 3 (Szenario C) eine neue Cache-Richtlinie erstellt haben, setzen Sie **Cache-Richtlinie** auf `edgeoptimize-cache`.
   ![Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. Konfigurieren Sie unter **Funktionszuordnungen** Folgendes:

   * **Viewer-Anfrage:**`edgeoptimize-routing`
   * **Ursprungsanfrage:** Versionierter Funktions-ARN aus Schritt 4 (in **Veröffentlichen einer Version**)
   * **Ursprungsantwort:** Versionierter Funktions-ARN aus Schritt 4 (in **Veröffentlichen einer Version**)

   ![Konfiguration der Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Klicken Sie auf **Änderungen speichern**.

**Zulassen von „Optimize at Edge“ durch Firewall-Regeln (optional)**

{{waf-allowlist-setup}}

**Schritt 6: Testen der Konfiguration**

**1. Testen des Bot-Traffics (sollte optimiert werden)**

Senden Sie eine Anfrage mit einem Agent-basierten Bot-Benutzer-Agent. Bei der **ersten Anfrage** kann Edge Optimize während der Verarbeitung und dem Caching der Seite eine (nicht optimierte) Proxy-Antwort zurückgeben. Sie können dies anhand des `x-edgeoptimize-proxy: 1`-Header in der Antwort identifizieren.

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

**4. Überprüfen des korrekten Protokollflusses**

Stellen Sie nach dem Ausführen der oben genannten Testanfragen sicher, dass Protokolle sowohl für die CloudFront- als auch für die Lambda@Edge-Funktion geschrieben werden.

*CloudFront-Funktionsprotokolle (`edgeoptimize-routing`)*

**Navigation:** AWS Console > CloudWatch > Protokollgruppen (in `us-east-1` oder der Region, in der Ihre CloudFront-Verteilung konfiguriert ist)

1. Suchen Sie nach einer Protokollgruppe mit dem Namen `/aws/cloudfront/function/edgeoptimize-routing`.
2. Öffnen Sie den neuesten Protokoll-Stream.
3. Bei Agent-basierten Anfragen sollten Einträge wie die folgenden angezeigt werden:
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Bei Anfragen, die nicht Agent-basiert sind, sollte Folgendes angezeigt werden:
   * `Routing to Default origin for userAgent: ...`

Sie können auch die Registerkarte **Metriken** unter **AWS Console > CloudFront > Funktionen > edgeoptimize-routing** überprüfen, um Aufrufzählungen und Fehlerquoten anzuzeigen.

*Lambda@Edge-Protokolle (`edgeoptimize-origin`)*

>[!IMPORTANT]
>Lambda@Edge-Protokolle werden in CloudWatch in der **Region des Edge-Speicherorts** für die Anfrage geschrieben und nicht `us-east-1`. Überprüfen Sie CloudWatch in der AWS-Region, die dem Ort am nächsten liegt, an dem Sie den curl-Befehl ausgeführt haben.

**Navigation:** AWS Console > CloudWatch > Protokollgruppen (stellen Sie sicher, dass Sie sich in der richtigen Region befinden)

1. Suchen Sie nach einer Protokollgruppe mit dem Namen `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Öffnen Sie den neuesten Protokoll-Stream.
3. Bei Agent-basierten Anfragen sollten Einträge wie die folgenden angezeigt werden:
   * `Calling Edge Optimize Origin for agentic requests`: Primärer Pfad
   * `Calling Default Origin in case of failover for agentic requests`: Failover-Pfad
   * `Failover Triggered for agentic requests`: Failover-Erkennung von Ursprungsantwort

Wenn die Protokollgruppe nicht vorhanden ist, überprüfen Sie, ob die IAM-Berechtigungen in Schritt 4 korrekt aktualisiert wurden. Überprüfen Sie auch andere benachbarte AWS-Regionen. Der Edge-Speicherort, an dem Ihre Anfrage verarbeitet wurde, kann vom erwarteten Speicherort abweichen.

**Fehlerbehebung**

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| Kein `x-edgeoptimize-request-id` in Antwort für Agent-basierten Anfragen | Ursprungsgruppe leitet nicht an Edge Optimize weiter | Überprüfen Sie, ob `YOUR_DEFAULT_ORIGIN` im CloudFront-Funktions-Code korrekt ersetzt wurde (Schritt 2). |
| 403-Fehler bei Agent-basierten Anfragen | Ungültiger oder fehlender API-Schlüssel | Überprüfen Sie den Wert des `x-edgeoptimize-api-key`-Headers in den benutzerdefinierten Headern des Edge Optimize-Ursprungs (Schritt 1). |
| CloudWatch-Protokolle für Lambda@Edge können nicht gefunden werden. | Falsche IAM-Berechtigungen | Überprüfen Sie, ob die Berechtigungsrichtlinie für CloudWatch-Protokolle aktualisiert wurde (Schritt 4). Hinweis: Lambda@Edge-Protokolle werden in der Edge-Region für die Anfrage angezeigt und nicht unbedingt in `us-east-1`. |
| Cache berücksichtigt `cache-control: no-store` nicht | Der Mindest-TTL-Wert ist möglicherweise zu hoch | Setzen Sie in Ihrer Cache-Richtlinie den Mindest-TTL-Wert auf `0` (Schritt 3). Wenn Ihre Mindest-TTL bereits sehr kurz ist, liegt das Problem möglicherweise nicht daran. |
| Regulärer Datenverkehr (nicht Agent-basiert) wird nach der Einrichtung unterbrochen | Fehlkonfiguration der Cache-Richtlinie | Wenn Sie eine neue Cache-Richtlinie erstellt haben (Szenario C), stellen Sie sicher, dass Sie alle Einstellungen aus der ursprünglichen verwalteten Richtlinie repliziert haben. |

**Deaktivieren und Reaktivieren von „Optimize at Edge“**

Die Lambda@Edge-Funktion (`edgeoptimize-origin`) ist mit den Ursprungsanfrage- und Ursprungsantwortereignissen Ihres CloudFront-Verhaltens verknüpft. Da sie bei jeder durch dieses Verhalten laufenden Anfrage (sowohl menschlich als auch Agent-basiert) inline ausgeführt wird, beeinträchtigt ein Lambda@Edge-Ausfall den gesamten Live-Traffic, nicht nur Agent-basierte Anfragen. Wenn Sie einen Lambda@Edge-Ausfall feststellen, entfernen Sie umgehend die Funktionszuordnungen, um den normalen Traffic-Fluss zu Ihrem Standardursprung wiederherzustellen.

**Erkennen eines Lambda@Edge-Ausfalls**

* **Dashboard „AWS Service Health“**: Überprüfen Sie das Dashboard [AWS Service Health](https://health.aws.amazon.com/health/status) auf aktive Vorfälle, die **Amazon CloudFront** oder **AWS Lambda** betreffen. Ein hier gemeldeter globaler oder regionaler Ausfall ist der schnellste Weg, um zu bestätigen, dass das Problem mit der AWS-Infrastrukturseite und nicht mit Ihrer Konfiguration zusammenhängt.
* **Lambda@Edge-Fehler**: Navigieren Sie zu **AWS Console > CloudFront > Monitoring > [Ihre Verteilung]**. Öffnen Sie die Registerkarte **Lambda@Edge-Fehler** und überprüfen Sie das Diagramm **Ausführungsfehler** auf Ausführungsfehler. Wenn diese Werte hoch sind, könnte Lambda@Edge ausgefallen sein.

**Trennen der Lambda@Edge-Funktion**

**Navigation:** AWS Console > CloudFront > Verteilungen >[Ihre Verteilung] > Verhalten

1. Klicken Sie auf **Bearbeiten** für Ihr Verhalten.

2. Scrollen Sie nach unten zum Abschnitt **Funktionszuordnungen** .

3. Legen Sie die folgenden Zuordnungen auf **Keine Zuordnung** fest:

   | Ereignis | Ändern in |
   |---|---|
   | Viewer-Anfrage | Keine Zuordnung |
   | Ursprungsanfrage | Keine Zuordnung |
   | Ursprungsantwort | Keine Zuordnung |

   ![Konfiguration der Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Klicken Sie auf **Änderungen speichern**.

5. Warten Sie, bis die Bereitstellung der CloudFront-Verteilung abgeschlossen ist. Der Status ändert sich von **Wird bereitgestellt** zum Datum der letzten Änderung, in der Regel innerhalb weniger Minuten.

Nach der Bereitstellung werden alle Traffic-Routen direkt zu Ihrem Standardursprung geleitet. Es wird keine Konfiguration gelöscht. Die Lambda-Funktion und ihre Zuordnungen können jederzeit wiederhergestellt werden.

**Erneutes Anhängen der Lambda@Edge-Funktion**

**Navigation:** AWS Console > CloudFront > Verteilungen >[Ihre Verteilung] > Verhalten

1. Klicken Sie auf **Bearbeiten** für Ihr Verhalten.

2. Scrollen Sie nach unten zum Abschnitt **Funktionszuordnungen** .

3. Stellen Sie die Zuordnungen wieder her:

   | Ereignis | Festlegen auf |
   |---|---|
   | Viewer-Anfrage | `edgeoptimize-routing` (CloudFront-Funktion) |
   | Ursprungsanfrage | Versionierter Lambda-ARN aus Schritt 4 |
   | Ursprungsantwort | Versionierter Lambda-ARN aus Schritt 4 |

   Verwenden Sie den versionierten **Funktion-ARN**, den Sie in Schritt 4 notiert haben (in **Veröffentlichen einer Version**).

   ![Konfiguration der Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Klicken Sie auf **Änderungen speichern**.

5. Warten Sie, bis die Bereitstellung der Verteilung abgeschlossen ist, und überprüfen Sie dann, ob die Agent-basierten Anfragen den `x-edgeoptimize-request-id`-Header zurückgeben, wie in Schritt 6 beschrieben.

{{return-to-overview}}
