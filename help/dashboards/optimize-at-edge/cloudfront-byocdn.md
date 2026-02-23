---
title: Optimieren bei Edge - CloudFront (BYOCDN)
description: Erfahren Sie, wie Sie CloudFront BYOCDN für „Optimieren“ bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 1253d0f0a58f6523699c52fbfab23028dc469c82
workflow-type: tm+mt
source-wordcount: '2228'
ht-degree: 1%

---


# CloudFront (BYOCDN)

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Stellen Sie vor dem Einrichten der CloudFront-Konfiguration sicher, dass Sie über Folgendes verfügen:

* Eine vorhandene CloudFront-Distribution, die Ihre Website bedient.
* AWS IAM-Berechtigungen zum Erstellen von Lambda-Funktionen, IAM-Rollen, CloudFront-Distributionen und Cache-Richtlinien.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

{{retrieve-byocdn-api-key}}

**Schritt 1: Edge Optimize Origin erstellen**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Registerkarte „Ursprünge“

1. Klicken Sie **Herkunft erstellen**.

2. Konfigurieren Sie den Ursprung:
   * **Ursprungs-Domain:** `live.edgeoptimize.net`
   * **Name:** `EdgeOptimize_Origin`

3. Belassen Sie alle anderen Felder mit ihren Standardwerten.

4. Hinzufügen benutzerdefinierter Kopfzeilen:

   | Kopfzeile | Wert |
   |--------|-------|
   | `x-edgeoptimize-api-key` | Ihr API-Schlüssel |
   | `x-forwarded-host` | `www.example.com` |

   Ersetzen Sie `www.example.com` durch Ihre eigentliche Website-Domain und `Your API key` durch den von Ihrem Adobe-Support-Mitarbeiter bereitgestellten API-Schlüssel für die Edge-Optimierung.

5. Klicken Sie **Herkunft erstellen**.

![CloudFront Origin Creation](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

**Schritt 2: Viewer-Anforderungsfunktion erstellen**

**Navigation:** AWS Console > CloudFront > Funktionen

1. Klicken Sie **Funktion erstellen**.

2. Konfigurieren:
   * **Name:** `edgeoptimize-routing`
   * **runtime:** `cloudfront-js-2.0`

3. Ersetzen Sie den Standard-Code durch den Code aus &quot;[-request.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/cloudfront-function/viewer-request.js).

   Passen Sie vor der Veröffentlichung die folgenden Werte im Code an:

   * `YOUR_DEFAULT_ORIGIN` - Ersetzen Sie durch den Namen Ihres vorhandenen Standardursprungs (zu finden in CloudFront > Distributionen > [Ihre Verteilung] > Registerkarte Ursprünge ).
   * `TARGETED_PATHS` - Wählen Sie `null` aus, um alle HTML-Seiten auszuwählen, oder legen Sie ein Array spezifischer Pfade fest, z. B. `['/', '/products', '/about']`.

4. Klicken Sie **Änderungen speichern** > **Veröffentlichungsfunktion**.

![Erstellung von CloudFront-Funktionen](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


**Schritt 3: Cache-Richtlinie konfigurieren**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

Überprüfen Sie die derzeit mit Ihrem Verhalten verknüpfte Cache-Richtlinie. Klicken Sie **Ihrem** auf „Bearbeiten“ und sehen Sie sich den Abschnitt **Cache-Schlüssel und -**&quot; an, um Ihr Szenario zu ermitteln:

* **Szenario A (Legacy):** wird ein Optionsfeld mit der Bezeichnung **Legacy-Cache-Einstellungen** ausgewählt. Es gibt kein Dropdown-Menü mit dem Richtliniennamen. Stattdessen werden Inline-TTL- und Kopfzeileneinstellungen angezeigt.
* **Szenario B (benutzerdefinierte Richtlinie):** Sie sehen **Cache-Richtlinie**, die mit einem von Ihnen oder Ihrem Team erstellten Richtliniennamen ausgewählt wurde (keine von AWS bereitgestellte Richtlinie).
* **Szenario C (verwaltete Richtlinie):** Sie sehen **Cache-Richtlinie** ausgewählt mit einem von AWS bereitgestellten Namen wie `CachingOptimized`, `CachingDisabled` oder `CachingOptimizedForUncompressedObjects` - diese können nicht bearbeitet werden.

**Szenario A: Alte Cache-Einstellungen**

Wenn für Ihr Verhalten ältere Cache-Einstellungen verwendet werden:

1. Unter **Cache-Schlüssel und -**&quot; wird &quot;**Cache-Einstellungen** ausgewählt.

2. Fügen Sie `x-edgeoptimize-config` und `x-edgeoptimize-url` zur Zulassungsliste **Kopfzeilen** hinzu:

   * Wählen **aus dem Dropdown-Menü** Folgende Kopfzeilen einschließen“ aus.
   * `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzufügen.
     ![CloudFront-Cache veraltet](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Wenn Sie **Alle** im Kopfzeilen-Dropdown-Menü ausgewählt haben, überspringen Sie diesen Schritt. Alle Kopfzeilen werden automatisch an den Ursprung weitergeleitet.

3. Überprüfen Sie die Einstellung **Objekt-Caching**:

   * Wenn auf **Anpassen** eingestellt, wird empfohlen, **Mindest-TTL** auf `0` festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.
   * Ist hierfür &quot;**-Cache-Kopfzeilen verwenden** festgelegt, ist keine Änderung erforderlich.

4. Klicken Sie **Änderungen speichern**.

**Szenario B: Nicht veraltet mit einer benutzerdefinierten Cache-Richtlinie**

Wenn für Ihr Verhalten bereits eine benutzerdefinierte Cache-Richtlinie verwendet wird (eine von Ihnen erstellte und keine von AWS verwaltete Richtlinie):

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Klicken Sie auf Ihre bestehende Richtlinie.

2. Klicken Sie auf **Bearbeiten**.

3. Es wird empfohlen, &quot;**TTL“** &quot;`0`&quot; festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.
   ![TTL-Einstellungen der Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. Fügen Sie unter **Cache-** > **Kopfzeilen** zusammen mit Ihren vorhandenen Einschlüssen `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzu.
   ![Cache-Richtlinienkopfzeilen](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Klicken Sie **Änderungen speichern**.

**Szenario C: Nicht veraltete mit einer verwalteten Cache-Richtlinie (AWS)**

Wenn für Ihr Verhalten eine AWS Managed Cache-Richtlinie verwendet wird (z. B. `CachingOptimized`), können Sie sie nicht bearbeiten. Sie müssen eine neue benutzerdefinierte Cache-Richtlinie erstellen, die die vorhandenen verwalteten Richtlinieneinstellungen repliziert und die Edge Optimize-Kopfzeilen oben hinzufügt.

**Teil 1: Notieren Sie sich Ihre aktuellen Einstellungen für verwaltete Cache-Richtlinien**

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Suchen Sie die verwaltete Cache-Richtlinie, die derzeit mit Ihrem Verhalten verbunden ist (z. B. `CachingOptimized`), und klicken Sie darauf.

2. Notieren Sie sich alle vorhandenen Einstellungen:
   * Minimale TTL, maximale TTL, Standard-TTL
   * Im Cache-Schlüssel enthaltene Kopfzeilen
   * Im Cache-Schlüssel enthaltene Cookies
   * Im Cache-Schlüssel enthaltene Abfragezeichenfolgen
   * Komprimierungsunterstützung (Gzip, Brotli)

**Teil 2: Erstellen Sie eine neue benutzerdefinierte Cache-Richtlinie mit denselben Einstellungen + Edge Optimize config**

**Navigation:** AWS Console > CloudFront > Richtlinien > Cache

1. Klicken Sie **Cache-Richtlinie erstellen**.

2. **Name:** `edgeoptimize-cache`

   ![Cache-Richtlinienname](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Replizieren Sie alle in Teil 1 genannten Einstellungen mit den folgenden Änderungen:

   * Es wird empfohlen, &quot;**TTL“** &quot;`0`&quot; festzulegen. Wenn Ihre aktuelle Mindest-TTL jedoch bereits sehr kurz ist, müssen Sie sie möglicherweise nicht ändern.

   ![TTL-Einstellungen der Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * Fügen Sie unter **Cache-** > **Headers** alles ein, was die verwaltete Richtlinie hatte, und fügen Sie `x-edgeoptimize-config` und `x-edgeoptimize-url` hinzu.

   ![Cache-Richtlinienkopfzeilen](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Klicken Sie auf **Erstellen**.

5. Kehren Sie zu Ihrem Verhalten zurück und verknüpfen Sie die neu erstellte Richtlinie:

   **Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

   1. Bearbeiten Sie Ihr Verhalten.
   2. Wählen **unter „Cache-Schlüssel und -**&quot; die Option **Cache-Richtlinie** aus.
   3. Wählen Sie `edgeoptimize-cache` aus dem Dropdown-Menü aus.
   4. Klicken Sie **Änderungen speichern**.

**Schritt 4: Erstellen der Funktion Lambda@Edge (Ursprungsanfrage und -antwort)**

>[!IMPORTANT]
>Lambda@Edge Funktionen **müssen in der Region `us-east-1` (N. Virginia) erstellt**. Dies ist eine AWS-Anforderung. Obwohl die Funktion in `us-east-1` erstellt wurde, repliziert AWS sie automatisch an allen CloudFront-Edge-Speicherorten weltweit, sodass sie am nächsten Edge-Speicherort für den Viewer ausgeführt wird. Vergewissern Sie sich, dass Sie sich in der AWS-Konsole in der `us-east-1` befinden, bevor Sie fortfahren.

**Erstellen der Lambda-Funktion**

**Navigation:** AWS Console > Lambda

1. Klicken Sie **Funktion erstellen**.

2. Wählen Sie **Von Grund auf erstellen**.

3. Konfigurieren:
   * **Funktionsname:** `edgeoptimize-origin`
   * Belassen Sie alle anderen Felder mit ihren Standardwerten.

4. Klicken Sie **Funktion erstellen**.

5. Ersetzen Sie im Code-Editor den Standard-Code durch den Code aus [origin-request-response.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/origin-request-response.js).

6. Klicken Sie **Bereitstellen**, um den Code zu speichern.

7. Beachten Sie den **Namen der Ausführungsrolle** der unter **Konfiguration** > **Berechtigungen** angezeigt wird (z. B. `edgeoptimize-origin-role-xxxxx`). Sie benötigen dies in den folgenden Schritten.

**Aktualisieren der Vertrauensrichtlinie der Ausführungsrolle**

Die automatisch erstellte Rolle vertraut nur `lambda.amazonaws.com`. Für Lambda@Edge müssen Sie auch `edgelambda.amazonaws.com` hinzufügen.

**Navigation:** AWS Console > IAM > Rollen > [Ihre Rolle aus dem vorherigen Schritt] > Registerkarte „Vertrauensstellungen“

1. Klicken Sie **Vertrauensrichtlinie bearbeiten**.

2. Ersetzen Sie die Richtlinie durch den Inhalt von [trust-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/trust-policy.json).

3. Klicken Sie **Richtlinie aktualisieren**.

>[!WARNING]
>Der `edgelambda.amazonaws.com`-Service-Prinzipal ist **erforderlich** für Lambda@Edge. Ohne sie kann CloudFront Ihre Funktion nicht an Edge-Speicherorten aufrufen.

**Korrigieren Sie die Berechtigungsrichtlinie CloudWatch Logs**

Die automatisch erstellte Rolle enthält eine für den regulären Lambda konfigurierte `AWSLambdaBasicExecutionRole`-Richtlinie, die den falschen Regionen- und Protokollgruppennamen für Lambda@Edge hat. Sie müssen sie aktualisieren.

**Navigation:** AWS Console > IAM > Rollen > [Ihre Rolle] > Registerkarte „Berechtigungen“ > Klicken Sie auf den Namen der angehängten Richtlinie (z. B. `AWSLambdaBasicExecutionRole-xxxx`)

1. Klicken Sie auf **Bearbeiten**.

2. Ersetzen Sie die Richtlinie durch den Inhalt von [cloudwatch-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/cloudwatch-policy.json).

   Ersetzen Sie in der JSON-Datei `ACCOUNT_ID` durch Ihre eigentliche AWS-Konto-ID (in der oberen rechten Ecke der AWS-Konsole) und `FUNCTION_NAME` Sie durch den Namen Ihrer Lambda-Funktion (z. B. `edgeoptimize-origin`).

3. Klicken Sie **Änderungen speichern**.

>[!WARNING]
>Die Region im ARN muss `*` sein. Lambda@Edge wird am nächsten Edge-Speicherort für den Viewer ausgeführt, sodass Protokolle in CloudWatch in der Region des Edge-Speicherorts geschrieben werden (z. B. `ap-south-1`, `eu-west-1`), nicht unbedingt `us-east-1`. Die Protokollgruppe verwendet einen regional vorangestellten Namen: `/aws/lambda/us-east-1.FUNCTION_NAME`, wobei `us-east-1` immer die Basisregion der Funktion ist.

**Version veröffentlichen**

1. Klicken Sie auf der Funktionsseite auf **Aktionen** (oben rechts) > **Neue Version**.

2. Beschreibung hinzufügen.

3. Klicken Sie auf **Veröffentlichen**.
   ![Lambda-Veröffentlichung](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Kopieren oder notieren Sie sich die **Funktion ARN** — Sie benötigen diese im nächsten Schritt.
   ![Lambda ARN](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

**Schritt 5: Verknüpfen der Funktionen und Cache-Richtlinie mit dem Verhalten**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

1. Bearbeiten Sie Ihr Verhalten.

2. Wenn Sie in Schritt 3 (Szenario C) eine neue Cache-Richtlinie erstellt haben, setzen Sie **Cache-Richtlinie** auf `edgeoptimize-cache`.
   ![Cache-Richtlinie](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. Konfigurieren **unter &quot;**&quot;:

   * **Viewer-Anfrage:** `edgeoptimize-routing`
   * **Ursprungsanfrage:** versionierte Funktion ARN aus Schritt 4 (in **Version veröffentlichen**)
   * **Ursprungsantwort:** versionierte ARN-Funktion aus Schritt 4 (in **Version veröffentlichen**)

   ![Konfiguration von Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Klicken Sie **Änderungen speichern**.

**Schritt 6: Testen Sie die Konfiguration**

**1. Bot-Traffic testen (sollte optimiert werden)**

Senden Sie eine Anfrage mit einem Agent-Bot-Benutzeragenten. Bei der **ersten Anfrage** gibt Edge Optimize möglicherweise eine Proxy-Antwort (nicht optimiert) zurück, während die Seite verarbeitet und zwischengespeichert wird. Sie können dies anhand der `x-edgeoptimize-proxy: 1` in der Antwort identifizieren.

Simulieren einer KI-Bot-Anfrage mithilfe eines agenten Benutzeragenten:

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

Die Antwort sollte **nicht** den `x-edgeoptimize-request-id`-Header enthalten. Seiteninhalt und Antwortzeit sollten vor der Aktivierung von Optimieren bei Edge identisch mit bleiben.

**3. Wie lassen sich die beiden Szenarien voneinander unterscheiden**

| Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Verkehr (nicht betroffen) |
|---|---|---|
| `x-edgeoptimize-request-id` | Präsenz - enthält eine eindeutige Anfrage-ID | Abwesend |
| `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover aufgetreten ist (Wert: `1`) | Abwesend |

Der Status des Traffic-Routings kann auch in der LLM Optimizer-Benutzeroberfläche überprüft werden. Navigieren Sie zu **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

![KI-Traffic-Routing-Status mit aktiviertem Routing](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

**4. Überprüfen Sie, ob die Protokolle ordnungsgemäß fließen**

Stellen Sie nach dem Ausführen der oben genannten Testanfragen sicher, dass Protokolle sowohl für die CloudFront- als auch für die Lambda@Edge-Funktion geschrieben werden.

*CloudFront-Funktionsprotokolle (`edgeoptimize-routing`)*

**Navigation:** AWS Console > CloudWatch > Protokollgruppen (in `us-east-1` oder der Region, in der Ihre CloudFront-Verteilung konfiguriert ist)

1. Suchen Sie nach einer Protokollgruppe mit dem Namen `/aws/cloudfront/function/edgeoptimize-routing`.
2. Öffnen Sie den neuesten Protokolldatenstrom.
3. Bei agenten Anfragen sollten Sie Einträge wie die folgenden sehen:
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Bei nicht-agenten Anfragen sollte Folgendes angezeigt werden:
   * `Routing to Default origin for userAgent: ...`

Sie können auch die Registerkarte **Metriken** unter **AWS Console > CloudFront > Funktionen > Edge-Routing** überprüfen, um Aufrufzählungen und Fehlerquoten anzuzeigen.

*Lambda@Edge-Protokolle (`edgeoptimize-origin`)*

>[!IMPORTANT]
>Lambda@Edge-Protokolle werden in CloudWatch in der **Region des Edge-Speicherorts** geschrieben, die die Anfrage verarbeitet hat, nicht `us-east-1`. Überprüfen Sie CloudWatch in der AWS-Region, die der Stelle am nächsten liegt, an der Sie den curl-Befehl ausgeführt haben.

**Navigation:** AWS Console > CloudWatch > Protokollgruppen (stellen Sie sicher, dass Sie sich in der richtigen Region befinden)

1. Suchen Sie nach einer Protokollgruppe mit dem Namen `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Öffnen Sie den neuesten Protokolldatenstrom.
3. Bei agenten Anfragen sollten Sie Einträge wie die folgenden sehen:
   * `Calling Edge Optimize Origin for agentic requests` - Primärer Pfad
   * `Calling Default Origin in case of failover for agentic requests` - Failover-Pfad
   * `Failover Triggered for agentic requests` - Failover-Erkennung von Ursprung und Antwort

Wenn die Protokollgruppe nicht vorhanden ist, überprüfen Sie, ob die IAM-Berechtigungen in Schritt 4 korrekt aktualisiert wurden. Überprüfen Sie auch andere benachbarte AWS-Regionen. Die Edge-Position, an der Ihre Anfrage verarbeitet wurde, kann von der erwarteten Position abweichen.

**Fehlerbehebung**

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| Keine `x-edgeoptimize-request-id` bei Anfragen durch Agenten | Ursprungsgruppe leitet nicht an Edge Optimize weiter | Überprüfen Sie, ob `YOUR_DEFAULT_ORIGIN` im CloudFront-Funktionscode korrekt ersetzt wurde (Schritt 2). |
| 403 Fehler bei Agent-Anfragen | Ungültiger oder fehlender API-Schlüssel | Überprüfen Sie den Wert der `x-edgeoptimize-api-key`-Kopfzeile in den benutzerdefinierten Kopfzeilen der Edge Optimize-Herkunft (Schritt 1). |
| CloudWatch-Protokolle für Lambda@Edge können nicht gefunden werden | Falsche IAM-Berechtigungen | Überprüfen Sie, ob die Berechtigungsrichtlinie für CloudWatch-Protokolle aktualisiert wurde (Schritt 4). Hinweis: Lambda@Edge -Protokolle werden in der Edge-Region angezeigt, die die Anfrage verarbeitet hat, nicht unbedingt `us-east-1`. |
| Cache berücksichtigt keine `cache-control: no-store` | Minimale TTL ist möglicherweise zu hoch | Setzen Sie die minimale TTL auf `0` in Ihrer Cache-Richtlinie (Schritt 3). Wenn die TTL für das Minimum bereits sehr kurz ist, ist dies möglicherweise nicht das Problem. |
| Regulärer (nicht-agentischer) Traffic nach der Einrichtung beschädigt | Falsche Konfiguration der Cache-Richtlinie | Wenn Sie eine neue Cache-Richtlinie erstellt haben (Szenario C), stellen Sie sicher, dass Sie alle Einstellungen aus der ursprünglich verwalteten Richtlinie repliziert haben. |

**Deaktivieren und erneutes Aktivieren von Optimieren in Edge**

Die Funktion Lambda@Edge (`edgeoptimize-origin`) ist mit den Ursprungsanfrage- und -antwortereignissen Ihres CloudFront-Verhaltens verknüpft. Da der Service bei jeder Anfrage, die dieses Verhalten durchläuft - sowohl bei Personen- als auch bei Agentenanforderungen - inline ausgeführt wird, wirkt sich ein Ausfall von Lambda@Edge auf den gesamten Live-Traffic aus, nicht nur auf die Agentenanforderungen. Wenn Sie einen Ausfall von Lambda@Edge feststellen, entfernen Sie die Funktionsverknüpfungen sofort, um den normalen Traffic-Fluss auf Ihren standardmäßigen Ursprung wiederherzustellen.

**So erkennen Sie einen Lambda@Edge-Ausfall**

* **AWS Service Health Dashboard** — Überprüfen Sie das [AWS Service Health Dashboard](https://health.aws.amazon.com/health/status) auf aktive Vorfälle, die **Amazon CloudFront** oder **AWS Lambda** betreffen. Ein hier gemeldeter globaler oder regionaler Ausfall ist die schnellste Möglichkeit, um zu bestätigen, dass das Problem auf der AWS-Infrastrukturseite und nicht in Ihrer Konfiguration liegt.
* **Lambda@Edge errors** — Navigieren Sie zu **AWS Console > CloudFront > Monitoring > [Ihre Distribution]**. Öffnen Sie die Registerkarte **Lambda@Edge** und überprüfen Sie das Diagramm **Ausführungsfehler** auf Ausführungsfehler. Wenn diese hoch sind, ist Lambda@Edge möglicherweise nicht verfügbar.

**Trennen der Funktion Lambda@Edge**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

1. Klicken Sie **Ihrem** auf „Bearbeiten“.

2. Scrollen Sie nach unten zum Abschnitt **Funktionszuordnungen** .

3. Legen Sie die folgenden Verknüpfungen auf &quot;**Verknüpfung“**:

   | Ereignis | Ändern in |
   |---|---|
   | Viewer-Anfrage | Keine Zuordnung |
   | Anfrage zur Herkunft | Keine Zuordnung |
   | Ursprungsantwort | Keine Zuordnung |

   ![Konfiguration von Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Klicken Sie **Änderungen speichern**.

5. Warten Sie, bis die Bereitstellung der CloudFront-Verteilung abgeschlossen ist. Der Status ändert sich von **Bereitstellung** zum Datum der letzten Änderung, in der Regel innerhalb weniger Minuten.

Nach der Bereitstellung werden alle Traffic-Routen direkt zu Ihrem standardmäßigen Ursprung geleitet. Es wird keine Konfiguration gelöscht. Die Lambda-Funktion und ihre Verknüpfungen können jederzeit wiederhergestellt werden.

**Erneutes Anhängen der Funktion Lambda@Edge**

**Navigation:** AWS Console > CloudFront > Verteilungen > [Ihre Verteilung] > Verhalten

1. Klicken Sie **Ihrem** auf „Bearbeiten“.

2. Scrollen Sie nach unten zum Abschnitt **Funktionszuordnungen** .

3. Stellen Sie die Verknüpfungen wieder her:

   | Ereignis | Auf festlegen |
   |---|---|
   | Viewer-Anfrage | `edgeoptimize-routing` (CloudFront-Funktion) |
   | Anfrage zur Herkunft | Lambda-ARN mit Versionsangabe aus Schritt 4 |
   | Ursprungsantwort | Lambda-ARN mit Versionsangabe aus Schritt 4 |

   Verwenden Sie die versionierte **Funktion ARN**, die Sie in Schritt 4 (in **Version veröffentlichen)**.

   ![Konfiguration von Funktionszuordnungen](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Klicken Sie **Änderungen speichern**.

5. Warten Sie, bis die Bereitstellung der Verteilung abgeschlossen ist, und überprüfen Sie dann, ob die Agentenanfragen die `x-edgeoptimize-request-id`-Kopfzeile zurückgeben, wie in Schritt 6 beschrieben.

{{return-to-overview}}
