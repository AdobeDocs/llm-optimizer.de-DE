---
title: Optimize at Edge – Cloudflare (BYOCDN)
description: Erfahren Sie, wie Sie Cloudflare BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-05-15T17:40:49.847Z'
TQID: 'https://experienceleague.adobe.com/HkaDwdHRGZJnip-1Bp-4Z-ovwcBPxFUSDqeLUVNu0zo'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: f1c0ad79ff4e71515da0b0d86632a558b0e99661
workflow-type: tm+mt
source-wordcount: 1915
ht-degree: 97%

---


# Cloudflare (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Bevor Sie die Routing-Regeln für den Cloudflare Worker einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Ein Cloudflare-Konto mit für Ihre Domain aktiviertem Workers.
* Zugriff auf die DNS-Einstellungen Ihrer Domain in Cloudflare.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Die einzelnen Schritte finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Weitere Informationen zum Staging-Routing finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Funktionsweise des Routings**

Bei korrekter Konfiguration wird eine Anfrage an Ihre Domain (z. B. `www.example.com/page.html`) von einem Agent-basierten Benutzer-Agent durch den Cloudflare Worker abgefangen und an das Edge Optimize-Backend weitergeleitet. Die Backend-Anfrage enthält die erforderlichen Header.

**Testen der Backend-Anfrage**

Sie können das Routing überprüfen, indem Sie eine direkte Anfrage an das Backend von Edge Optimize stellen.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**Erforderliche Header**

Bei Anfragen an das Backend von Edge Optimize müssen die folgenden Header festgelegt werden:

| Kopfzeile | Beschreibung | Beispiel |
|--------|-------------|---------|
| `x-forwarded-host` | Der ursprüngliche Host der Anfrage. Erforderlich zum Identifizieren der Sitedomain. | `www.example.com` |
| `x-edgeoptimize-url` | Der ursprüngliche URL-Pfad und die Abfragezeichenfolge der Anfrage. | `/page.html` oder `/products?id=123` |
| `x-edgeoptimize-api-key` | Der von Adobe für Ihre Domain bereitgestellte API-Schlüssel. | `your-api-key-here` |
| `x-edgeoptimize-config` | Konfigurationszeichenfolge zur Unterscheidung von Cache-Schlüsseln. | `LLMCLIENT=TRUE;` |

## Einrichtungsoptionen

Es gibt zwei Möglichkeiten, Cloudflare Worker für Edge Optimize einzurichten:

* [**Option 1: Bereitstellen für Cloudflare (empfohlen)**](#option-1-deploy-to-cloudflare) – Es wird automatisch ein neuer Worker erstellt und Sie werden zur Eingabe der erforderlichen Umgebungsvariablen und Geheimnisse aufgefordert. Verwenden Sie diese Option, wenn kein Cloudflare Worker für diese Domain vorhanden ist.
* [**Option 2: Manuelle Einrichtung**](#option-2-manual-setup) – Detaillierte Anleitungen zum manuellen Erstellen und Konfigurieren des Workers. Verwenden Sie diese Option, wenn Sie bereits einen Cloudflare Worker in Ihrer Domain konfiguriert haben – Sie müssen den Edge Optimize-Code mit Ihrem bestehenden Worker zusammenführen (siehe [Schritt 2: Hinzufügen des Worker-Codes](#option-2-manual-setup)) – oder wenn Sie die vollständige Kontrolle über die Bereitstellung bevorzugen.

Unabhängig davon, welche Option Sie auswählen, müssen Sie den Worker manuell mit Ihrer Domain verknüpfen. Weitere Informationen dazu finden Sie unter [Schritt: Hinzufügen einer Route zu Ihrer Domain](#add-a-route-to-your-domain).

## Option 1: Bereitstellen in Cloudflare

Bei dieser Option wird die Schaltfläche **In Cloudflare bereitstellen** verwendet, um den Worker automatisch zu erstellen und die erforderlichen Umgebungsvariablen und Geheimnisse in Ihrem Cloudflare-Konto zu konfigurieren. Dies ist der schnellste Methode zum Einrichten eines neuen Workers.

>[!IMPORTANT]
>
>Verwenden Sie diese Option nur, wenn Sie über **keinen** bestehenden Cloudflare-Worker in Ihrer Domain verfügen. Wenn Sie bereits über einen Worker verfügen, verwenden Sie [Option 2: Manuelle Einrichtung](#option-2-manual-setup), um die Edge Optimize-Routing-Logik zu Ihrem bestehenden Worker hinzuzufügen.

**Schritt 1: Bereitstellen des Workers**

Klicken Sie auf die Schaltfläche unten, um den Edge Optimize-Worker in Ihrem Cloudflare-Konto bereitzustellen:

[![Bereitstellen in Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/cloudflare/automation)

**Schritt 2: Ausfüllen des Bereitstellungsformulars**

Durch Klicken auf die Schaltfläche wird die Seite zur Einrichtung des Workers geöffnet. Füllen Sie das Formular wie folgt aus:

![Seite zur Einrichtung von Cloudflare Workern](/help/assets/optimize-at-edge/cloudflare-deploy-form.png)

1. **Git-Konto**: Wählen Sie Ihr GitHub- oder GitLab-Konto aus dem Dropdown-Menü aus. Cloudflare schickt den Worker-Code in ein Repository in Ihrem Konto. Wenn kein Konto aufgeführt ist, können Sie eine neue Verbindung direkt aus dem Dropdown-Menü hinzufügen, indem Sie **+ Neue GitHub-Verbindung** oder **+ Neue GitLab-Verbindung** auswählen. Weitere Informationen finden Sie im [Handbuch zur Cloudflare-Git-Integration](https://developers.cloudflare.com/workers/ci-cd/builds/git-integration/github-integration/).

   ![Dropdown-Menü für Git-Konto mit den Optionen „Neue GitHub-Verbindung“ und „Neue GitLab-Verbindung“](/help/assets/optimize-at-edge/cloudflare-git-connection.png)
2. **Privates Git-Repository erstellen**: Lassen Sie diese Option aktiviert (Standardeinstellung).
3. **Projektname**: Belassen Sie diesen als `edge-optimize-router` oder geben Sie einen Namen Ihrer Wahl ein.
4. **EDGE_OPTIMIZE_API_KEY**: Fügen Sie Ihren von Adobe bereitgestellten Edge Optimize-API-Schlüssel ein. Dieser Wert wird als verschlüsseltes Geheimnis gespeichert.
5. **EDGE_OPTIMIZE_TARGET_HOST**: Geben Sie die Domain Ihrer Site ohne das Protokoll ein (z. B. `www.example.com`).
6. **Befehl erstellen**: Lassen Sie dieses Feld leer.
7. **Befehl bereitstellen**: Behalten Sie für dieses Feld `npm run deploy` bei (vorausgefüllt).
8. **Builds für produktionsfremde Verzweigungen**: Lassen Sie diese Option deaktiviert. Dies ist eine Workflow-Funktion für Entwickelnde und wird für diese Bereitstellung nicht benötigt.
9. Klicken Sie auf **Speichern und bereitstellen**.

Nachdem der Worker bereitgestellt wurde, fahren Sie mit [Hinzufügen einer Route zu Ihrer Domain](#add-a-route-to-your-domain) fort, um den Worker mit Ihrer Domain zu verknüpfen. Das Routing wird nicht automatisch konfiguriert und muss manuell abgeschlossen werden.

## Option 2: Manuelle Einrichtung

Führen Sie diese Schritte aus, um den Worker manuell zu erstellen und zu konfigurieren.

**Schritt 1: Cloudflare Worker erstellen**

1. Melden Sie sich bei Ihrem Cloudflare-Dashboard an.
2. Navigieren Sie in der Seitenleiste zu **Workers &amp; Pages**.
3. Klicken Sie auf **Create application** (Anwendung erstellen) und dann auf **Create Worker** (Worker erstellen).
4. Legen Sie einen Namen für Ihren Worker fest (z. B. `edge-optimize-router`).
5. Klicken Sie auf **Deploy** (Bereitstellen), um den Worker mit dem Standard-Code zu erstellen.

![Dashboard für Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Schritt 2: Worker-Code hinzufügen**

Klicken Sie nach dem Erstellen des Sekundärs auf **Code bearbeiten** und ersetzen Sie den Standardcode durch den Code aus [worker.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudflare/worker.js). Wenn Sie bereits über einen Cloudflare-Worker verfügen, führen Sie den Code mit Ihrem vorhandenen Worker-Code zusammen, anstatt ihn vollständig zu ersetzen.

Klicken Sie auf **Save and deploy** (Speichern und bereitstellen), um den Worker zu veröffentlichen.

**Schritt 3: Konfigurieren von Umgebungsvariablen**

Umgebungsvariablen speichern vertrauliche Konfigurationen wie Ihren API-Schlüssel auf sichere Weise.

1. Navigieren Sie in den Einstellungen Ihres Workers zu **Settings** (Einstellungen) > **Variables** (Variablen).
2. Klicken Sie unter **Environment Variables** (Umgebungsvariablen) auf **Add variable** (Variable hinzufügen).
3. Fügen Sie die folgenden Variablen hinzu:

   | Variablenname | Beschreibung | Erforderlich |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Ihr von Adobe bereitgestellter API-Schlüssel für Edge Optimize. | Ja |
   | `EDGE_OPTIMIZE_TARGET_HOST` | Der Ziel-Host für Edge Optimize-Anfragen (als `x-forwarded-host`-Header gesendet) und die Ursprungs-Domain für das Failover. Darf nur die Domain ohne Protokoll sein (z. B. `www.example.com`, nicht `https://www.example.com`). | Ja |

4. Klicken Sie für den API-Schlüssel auf **Encrypt** (Verschlüsseln), um ihn sicher zu speichern.
5. Klicken Sie auf **Save and deploy** (Speichern und bereitstellen).

![Cloudflare-Umgebungsvariablen](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

## Hinzufügen einer Route zu Ihrer Domain {#add-a-route-to-your-domain}

Unabhängig davon, welche Einrichtungsoption Sie verwendet haben, müssen Sie den Worker manuell mit Ihrer Domain verknüpfen. Dieser Schritt aktiviert den Worker in Ihrem Traffic.

1. Navigieren Sie zu **Settings** (Einstellungen) > **Triggers** (Auslöser) für Ihren Worker.
2. Klicken Sie unter **Routes** (Routen) auf **Add route** (Route hinzufügen).
3. Geben Sie Ihr Domain-Muster ein (z. B. `www.example.com/*` oder `example.com/*`).
4. Wählen Sie im Dropdown-Menü eine Zone aus.
5. Klicken Sie auf **Speichern**.

Alternativ können Sie Routen auf Zonenebene konfigurieren:

1. Navigieren Sie zu Ihrer Domain in Cloudflare.
2. Gehen Sie zu **Workers Routes** (Workers – Routen).
3. Klicken Sie auf **Add route** (Route hinzufügen) und geben Sie das Muster und den Worker an.

![Cloudflare Worker-Routen](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Überprüfen des Failover-Verhaltens**

Wenn Edge Optimize nicht verfügbar ist oder einen Fehler zurückgibt, führt der Worker automatisch ein Failover zu Ihrem Ursprung durch. Die Failover-Antworten enthalten den `x-edgeoptimize-fo`-Header:

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Sie können Failover-Ereignisse in den Cloudflare Workers-Protokollen überwachen, um Probleme zu beheben.

**Grundlegendes zur Worker-Logik**

Der Cloudflare Worker implementiert die folgende Logik:

1. **Erkennung von Benutzer-Agents:** Prüft, ob der Benutzer-Agent der eingehenden Anfrage mit einem der definierten Agent-basierten Bots übereinstimmt (keine Berücksichtigung der Groß-/Kleinschreibung).

2. **Pfad-Targeting:** Filtert Anfragen optional nach Zielpfaden. Standardmäßig werden alle HTML-Seiten (URLs, die auf `/` enden, keine Erweiterung haben oder auf `.html` enden) weitergeleitet. Sie können bestimmte Pfade mithilfe des Arrays `TARGETED_PATHS` angeben.

3. **Schleifenschutz:** Der `x-edgeoptimize-request`-Header verhindert Endlosschleifen. Wenn Edge Optimize Anfragen an Ihren Ursprung zurücksendet, wird dieser Header auf `"1"` festgelegt und der Worker übergibt die Anfrage, ohne sie an Edge Optimize zurückzuleiten.

4. **Header-Sicherheit:** Bevor Sie Edge Optimize-Header festlegen, entfernt der Worker alle vorhandenen `x-edgeoptimize-*`-Header aus der eingehenden Anfrage, um Header-Injection-Angriffe zu verhindern.

5. **Header-Zuordnung:** Der Worker legt die erforderlichen Header für Edge Optimize fest:
   * `x-forwarded-host` – Identifiziert die ursprüngliche Sitedomain.
   * `x-edgeoptimize-url` – Behält den ursprünglichen Anfragepfad und die Abfragezeichenfolge bei.
   * `x-edgeoptimize-api-key` – Authentifiziert die Anfrage bei Edge Optimize.
   * `x-edgeoptimize-config` – Stellt die Konfiguration des Cache-Schlüssels bereit.

6. **Failover-Logik:** Wenn Edge Optimize einen Fehlerstatus-Code (4XX-Client- oder 5XX-Server-Fehler) zurückgibt oder die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt, erfolgt automatisch ein Failover des Workers zu Ihrem Ursprung mithilfe von `EDGE_OPTIMIZE_TARGET_HOST`. Die Failover-Antwort enthält den `x-edgeoptimize-fo: 1`-Header, um anzugeben, dass ein Failover stattgefunden hat.

7. **Umleitungshandhabung:** Die Option `redirect: "manual"` stellt sicher, dass Umleitungsantworten von Edge Optimize an den Client weitergeleitet werden, ohne dass der Worker ihnen folgt.

**Anpassen der Konfiguration**

Sie können das Worker-Verhalten anpassen, indem Sie die Konfigurationskonstanten oben im Code ändern:

**Liste Agent-basierter Bots**

Ändern Sie das Array `AGENTIC_BOTS`, um Benutzer-Agents hinzuzufügen oder zu entfernen:

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  // Add additional user agents as needed
  'ClaudeBot',
  'Anthropic-AI'
];
```

**Zielpfade**

Standardmäßig werden alle HTML-Seiten an Edge Optimize weitergeleitet. Um das Routing auf bestimmte Pfade zu beschränken, ändern Sie das Array `TARGETED_PATHS`:

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Failover-Konfiguration**

Standardmäßig erfolgt ein Failover des Workers bei einem 4XX- oder 5XX-Fehler von Edge Optimize. Passen Sie dieses Verhalten an:

```javascript
// Default: failover on any 4XX or 5XX error
const FAILOVER_ON_4XX = true;
const FAILOVER_ON_5XX = true;

// Failover only on 5XX server errors (not 4XX client errors)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = true;

// Disable automatic failover (not recommended)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = false;
```

**Wichtige Aspekte**

* **Failover-Verhalten:** Der Worker führt automatisch ein Failover zu Ihrem Ursprung durch, wenn Edge Optimize einen Fehler zurückgibt (4XX- oder 5XX-Status-Code) oder wenn die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt. Bei einem Failover wird `EDGE_OPTIMIZE_TARGET_HOST` als Ursprungs-Domain verwendet (ähnlich wie bei `F_Default_Origin` von Fastly oder `Default_Origin` von CloudFront). Failover-Antworten enthalten den `x-edgeoptimize-fo: 1`-Header, den Sie für Monitoring und Debugging verwenden können.

* **Caching:** Cloudflare speichert Antworten standardmäßig basierend auf der URL zwischen. Da der Agent-basierten Traffic andere Inhalte erhält als menschlicher Traffic, müssen Sie sicherstellen, dass dies bei Ihrer Cache-Konfiguration berücksichtigt wird. Erwägen Sie die Verwendung der Cache-API oder von Cache-Headern, um zwischengespeicherte Inhalte zu unterscheiden. Der `x-edgeoptimize-config`-Header sollte in Ihrem Cache-Schlüssel enthalten sein.

* **Ratenbegrenzung:** Überwachen Sie die Nutzung von Edge Optimize und erwägen Sie bei Bedarf die Implementierung einer Ratenbegrenzung für Agent-basierten Traffic.

* **Testen:** Testen Sie die Konfiguration immer in einer Staging-Umgebung, bevor Sie sie in der Produktionsumgebung bereitstellen. Vergewissern Sie sich, dass sich Agent-basierter Traffic und menschlicher Traffic erwartungsgemäß verhalten. Testen Sie das Failover-Verhalten durch Simulation von Edge Optimize-Fehlern.

* **Protokollierung:** Aktivieren Sie die Cloudflare Workers-Protokollierung, um Anfragen zu überwachen und Probleme zu beheben. Navigieren Sie zu **Workers** > **Ihr Worker** > **Logs** (Protokolle), um Echtzeitprotokolle anzuzeigen. Der Worker protokolliert Failover-Ereignisse zu Debugging-Zwecken.

**Fehlerbehebung**

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| Kein `x-edgeoptimize-request-id`-Header in Antwort | Worker-Route nicht zugeordnet oder Benutzer-Agent nicht in der Liste der Agent-basierten Bots. | Überprüfen Sie, ob Ihr Routenmuster mit der Anfrage-URL übereinstimmt. Prüfen Sie, ob sich der Benutzer-Agent im Array `AGENTIC_BOTS` befindet. |
| 401- oder 403-Fehler von Edge Optimize | Ungültiger oder fehlender API-Schlüssel. | Überprüfen Sie, ob `EDGE_OPTIMIZE_API_KEY` in Umgebungsvariablen und Geheimnissen korrekt festgelegt ist. Wenden Sie sich an Adobe, um zu bestätigen, dass Ihr API-Schlüssel aktiv ist. |
| Unendliche Weiterleitungen oder Schleifen | Schleifenschutz-Header ist nicht korrekt festgelegt oder wird nicht richtig überprüft. | Stellen Sie sicher, dass die Überprüfung des `x-edgeoptimize-request`-Headers eingerichtet ist. |
| Betroffener menschlicher Traffic | Routing-Logik für Worker ist zu breit angelegt. | Überprüfen Sie, ob die Zuordnungslogik des Benutzer-Agents korrekt ist und nicht zwischen Groß- und Kleinschreibung unterschieden wird. Überprüfen Sie, ob `TARGETED_PATHS` richtig konfiguriert ist. |
| Langsame Antwortzeiten | Netzwerklatenz zum Edge Optimize-Backend. | Dies ist für die erste Anfrage zu erwarten. Nachfolgende Anfragen werden bei Edge Optimize zwischengespeichert. |
| `x-edgeoptimize-fo: 1`-Header in Antwort | Edge Optimize hat einen Fehler zurückgegeben und es hat ein Failover zum Ursprung stattgefunden. | Überprüfen Sie die Cloudflare Workers-Protokolle auf den spezifischen Fehler-Code. Informieren Sie sich bei Adobe über den Dienststatus von Edge Optimize. |
| Failover funktioniert nicht | Failover-Flags deaktiviert oder Fehler in der Failover-Logik. | Überprüfen Sie, ob `FAILOVER_ON_4XX` und `FAILOVER_ON_5XX` auf `true` festgelegt sind. Prüfen Sie die Worker-Protokolle auf Fehlermeldungen. |
| Bestimmte Pfade werden nicht optimiert | Pfad stimmt nicht mit den Zielpfaden oder dem HTML-Seitenmuster überein. | Überprüfen Sie, ob sich der Pfad in `TARGETED_PATHS` befindet (falls angegeben) und mit dem Regex-Muster der HTML-Seite übereinstimmt. |
| Anfragen schlagen aufgrund eines ungültigen Hosts fehl | `EDGE_OPTIMIZE_TARGET_HOST` enthält Protokoll (zum Beispiel `https://`). | Verwenden Sie nur den Domain-Namen ohne Protokoll (zum Beispiel `example.com`, nicht `https://example.com`). |
| 530-Fehler beim Failover | Cloudflare kann keine Verbindung zum Ursprung herstellen oder die Failover-Anfrage hat ungültige Header. | Stellen Sie sicher, dass die Failover-Funktion Edge Optimize-Header entfernt. Stellen Sie sicher, dass auf Ihren Ursprung zugegriffen werden kann und dass DNS korrekt konfiguriert ist. |

**Zulassen von „Optimize at Edge“ durch Firewall-Regeln (optional)**

{{waf-allowlist-setup}}

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
