---
title: Optimize at Edge – Cloudflare (BYOCDN)
description: Erfahren Sie, wie Sie Cloudflare BYOCDN für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-05-15T17:40:49.847Z'
TQID: 'https://experienceleague.adobe.com/HkaDwdHRGZJnip-1Bp-4Z-ovwcBPxFUSDqeLUVNu0zo'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1906
ht-degree: 68%

---


# Cloudflare (BYOCDN)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem `x-edgeoptimize-request-id`-Header.

**Voraussetzungen**

Bevor Sie die Routing-Regeln für den Cloudflare Worker einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Ein Cloudflare-Konto mit für Ihre Domain aktiviertem Workers.
* Zugriff auf die DNS-Einstellungen Ihrer Domain in Cloudflare.
* Einen API-Schlüssel für Edge Optimize, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde. Anweisungen hierzu finden Sie unter [Abrufen Ihrer API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Optional) Informationen zum Testen des Staging-Routings finden Sie unter [Staging-API-Schlüssel](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

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

## Setup-Optionen

Es gibt zwei Möglichkeiten, Cloudflare Worker für Edge Optimize einzurichten:

* [**Option 1: Für Cloudflare bereitstellen (empfohlen)**](#option-1-deploy-to-cloudflare) - Erstellt automatisch einen neuen Worker und fordert Sie zur Eingabe der erforderlichen Umgebungsvariablen und Geheimnisse auf. Verwenden Sie diese Option, wenn kein Cloudflare-Worker für diese Domain vorhanden ist.
* [**Option 2: Manuelles Setup**](#option-2-manual-setup) — Schrittweise Anleitungen zum Erstellen und Konfigurieren des Sekundärs selbst. Verwenden Sie diese Option, wenn Sie bereits einen Cloudflare-Worker in Ihrer Domain konfiguriert haben - Sie müssen den Edge Optimize-Code mit Ihrem bestehenden Worker zusammenführen (siehe [Schritt 2: Hinzufügen des Worker-Codes](#option-2-manual-setup)) oder wenn Sie die vollständige Kontrolle über die Bereitstellung bevorzugen.

Unabhängig davon, welche Option Sie auswählen, müssen Sie den Worker manuell mit Ihrer Domain verknüpfen - siehe [Schritt: Hinzufügen einer Route zu Ihrer Domain](#add-a-route-to-your-domain).

## Option 1: Für Cloudflare bereitstellen

Diese Option verwendet die Schaltfläche **In Cloudflare bereitstellen**, um den Worker automatisch zu erstellen und die erforderlichen Umgebungsvariablen und Geheimnisse in Ihrem Cloudflare-Konto zu konfigurieren. Dies ist der schnellste Einstieg, wenn Sie einen neuen Worker einrichten.

>[!IMPORTANT]
>
>Verwenden Sie diese Option nur, **Sie** vorhandenen Cloudflare-Worker in Ihrer Domain haben. Wenn Sie bereits einen Worker haben, verwenden Sie [Option 2: Manuelle Einrichtung](#option-2-manual-setup), um die Routing-Logik für Edge Optimize zu Ihrem bestehenden Worker hinzuzufügen.

**Schritt 1: Bereitstellen des Sekundärs**

Klicken Sie auf die Schaltfläche unten, um den Edge Optimize-Worker für Ihr Cloudflare-Konto bereitzustellen:

[![Bereitstellung für Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/cloudflare/automation)

**Schritt 2: Füllen Sie das Bereitstellungsformular aus**

Durch Klicken auf die Schaltfläche wird die Seite „Workers-Einrichtung“ geöffnet. Füllen Sie das Formular wie folgt aus:

![Cloudflare-Sekundäre - Einrichtungsseite](/help/assets/optimize-at-edge/cloudflare-deploy-form.png)

1. **Git-Konto** - Wählen Sie Ihr GitHub- oder GitLab-Konto aus der Dropdown-Liste aus. Cloudflare wandelt den Code des Sekundärs in ein Repository in Ihrem Konto um. Wenn kein Konto aufgeführt ist, können Sie eine neue Verbindung direkt aus der Dropdown-Liste hinzufügen, indem Sie **+ Neue GitHub-Verbindung**. **+ Neue GitLab-Verbindung**. Weitere Informationen finden Sie im [Handbuch zur Cloudflare-Git-Integration](https://developers.cloudflare.com/workers/ci-cd/builds/git-integration/github-integration/).

   ![Dropdown-Menü des Git-Kontos mit den Optionen Neue GitHub-Verbindung und Neue GitLab-Verbindung](/help/assets/optimize-at-edge/cloudflare-git-connection.png)
2. **Privates Git-Repository erstellen** — Lassen Sie diese Option aktiviert (Standard).
3. **Projektname** — Belassen Sie die `edge-optimize-router` oder geben Sie einen Namen Ihrer Wahl ein.
4. **EDGE_OPTIMIZE_API_KEY** — Fügen Sie den von Adobe bereitgestellten API-Schlüssel für Edge Optimize ein. Dieser Wert wird als verschlüsseltes Geheimnis gespeichert.
5. **EDGE_OPTIMIZE_TARGET_HOST** — Geben Sie die Domain Ihrer Site ohne das Protokoll ein (z. B. `www.example.com`).
6. **Befehl erstellen** - Leer lassen.
7. **Befehl bereitstellen** — Als `npm run deploy` beibehalten (vorausgefüllt).
8. **Builds für produktionsfremde Verzweigungen** — Deaktivieren Sie diese Option. Dies ist eine Workflow-Funktion für Entwickler und wird für diese Bereitstellung nicht benötigt.
9. Klicken Sie **Erstellen und bereitstellen**.

Nachdem der Worker bereitgestellt wurde, fahren Sie mit [Route zu Ihrer Domain hinzufügen](#add-a-route-to-your-domain) fort, um den Worker mit Ihrer Domain zu verknüpfen. Das Routing wird nicht automatisch konfiguriert und muss manuell abgeschlossen werden.

## Option 2: Manuelle Einrichtung

Führen Sie diese Schritte aus, um den Worker manuell zu erstellen und zu konfigurieren.

**Schritt 1: Cloudflare Worker erstellen**

1. Melden Sie sich bei Ihrem Cloudflare-Dashboard an.
2. Navigieren Sie in der Seitenleiste zu **Workers &amp; Pages**.
3. Klicken Sie auf **Create application** (Anwendung erstellen) und dann auf **Create Worker** (Worker erstellen).
4. Legen Sie einen Namen für Ihren Worker fest (z. B. `edge-optimize-router`).
5. Klicken Sie auf **Deploy** (Bereitstellen), um den Worker mit dem Standard-Code zu erstellen.

![Dashboard für Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Schritt 2: Worker-Code hinzufügen**

Klicken Sie nach dem Erstellen des Workers **Code bearbeiten** und ersetzen Sie den Standard-Code durch Folgendes. Wenn Sie bereits über einen Cloudflare-Worker verfügen, führen Sie den unten stehenden Code mit Ihrem vorhandenen Worker-Code zusammen, anstatt ihn vollständig zu ersetzen.

```javascript
/**
 * Edge Optimize BYOCDN - Cloudflare Worker
 *
 * This worker routes requests from agentic bots (AI/LLM user agents) to the
 * Edge Optimize backend service for optimized content delivery.
 *
 * Features:
 * - Routes agentic bot traffic to Edge Optimize backend
 * - Failover to origin on Edge Optimize errors (any 4XX or 5XX errors)
 * - Loop protection to prevent infinite redirects
 * - Human visitors and SEO bots are served from the origin as usual
 */

// List of agentic bot user agents to route to Edge Optimize
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User'
];

// Targeted paths for Edge Optimize routing
// Set to null to route all HTML pages, or specify an array of paths
const TARGETED_PATHS = null; // e.g., ['/', '/page.html', '/products']

// Failover configuration
// Failover on any 4XX client error or 5XX server error from Edge Optimize
const FAILOVER_ON_4XX = true; // Failover on any 4XX error (400-499)
const FAILOVER_ON_5XX = true; // Failover on any 5XX error (500-599)

export default {
  async fetch(request, env, ctx) {
    return await handleRequest(request, env, ctx);
  },
};

async function handleRequest(request, env, ctx) {
  const url = new URL(request.url);
  const userAgent = request.headers.get("user-agent")?.toLowerCase() || "";

  // Check if request is already processed (loop protection)
  const isEdgeOptimizeRequest = !!request.headers.get("x-edgeoptimize-request");

  // Construct the original path and query string
  const pathAndQuery = `${url.pathname}${url.search}`;

  // Check if the path matches HTML pages (no extension or .html extension)
  const isHtmlPage = /(?:\/[^./]+|\.html|\/)$/.test(url.pathname);

  // Check if path is in targeted paths (if specified)
  const isTargetedPath = TARGETED_PATHS === null
    ? isHtmlPage
    : (isHtmlPage && TARGETED_PATHS.includes(url.pathname));

  // Check if user agent is an agentic bot
  const isAgenticBot = AGENTIC_BOTS.some((ua) => userAgent.includes(ua.toLowerCase()));

  // Route to Edge Optimize if:
  // 1. Request is NOT already from Edge Optimize (prevents infinite loops)
  // 2. User agent matches one of the agentic bots
  // 3. Path is targeted for optimization
  if (!isEdgeOptimizeRequest && isAgenticBot && isTargetedPath) {

    // Build the Edge Optimize request URL
    const edgeOptimizeURL = `https://live.edgeoptimize.net${pathAndQuery}`;

    // Clone and modify headers for the Edge Optimize request
    const edgeOptimizeHeaders = new Headers(request.headers);

    // Remove any existing Edge Optimize headers for security
    edgeOptimizeHeaders.delete("x-edgeoptimize-api-key");
    edgeOptimizeHeaders.delete("x-edgeoptimize-url");
    edgeOptimizeHeaders.delete("x-edgeoptimize-config");
    edgeOptimizeHeaders.delete("x-edgeoptimize-fetcher-key"); // Optional (required only in case of WAF)

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

    // edgeOptimizeHeaders.set("x-edgeoptimize-fetcher-key", "<YOUR FETCHER KEY>"); // Optional (required only in case of WAF)

    try {
      // Send request to Edge Optimize backend
      const edgeOptimizeResponse = await fetch(new Request(edgeOptimizeURL, {
        headers: edgeOptimizeHeaders,
        redirect: "manual", // Preserve redirect responses from Edge Optimize
      }), {
        cf: {
          cacheEverything: true, // Enable caching based on origin's cache-control headers
        },
      });

      // Check if we need to failover to origin
      const status = edgeOptimizeResponse.status;
      const is4xxError = FAILOVER_ON_4XX && status >= 400 && status < 500;
      const is5xxError = FAILOVER_ON_5XX && status >= 500 && status < 600;

      if (is4xxError || is5xxError) {
        console.log(`Edge Optimize returned ${status}, failing over to origin`);
        return await failoverToOrigin(request, env, url);
      }

      // Return the Edge Optimize response
      return edgeOptimizeResponse;

    } catch (error) {
      // Network error or timeout - failover to origin
      console.log(`Edge Optimize request failed: ${error.message}, failing over to origin`);
      return await failoverToOrigin(request, env, url);
    }
  }

  // For all other requests (human users, SEO bots), pass through unchanged
  return fetch(request);
}

/**
 * Failover to origin server when Edge Optimize returns an error
 * @param {Request} request - The original request
 * @param {Object} env - Environment variables
 * @param {URL} url - Parsed URL object
 */
async function failoverToOrigin(request, env, url) {
  // Build origin URL
  const originURL = `${url.protocol}//${env.EDGE_OPTIMIZE_TARGET_HOST}${url.pathname}${url.search}`;

  // Prepare headers - clean Edge Optimize headers and add loop protection
  const originHeaders = new Headers(request.headers);
  originHeaders.set("Host", env.EDGE_OPTIMIZE_TARGET_HOST);
  originHeaders.delete("x-edgeoptimize-api-key");
  originHeaders.delete("x-edgeoptimize-url");
  originHeaders.delete("x-edgeoptimize-config");
  originHeaders.delete("x-forwarded-host");
  originHeaders.set("x-edgeoptimize-request", "fo");

  // Create and send origin request
  const originRequest = new Request(originURL, {
    method: request.method,
    headers: originHeaders,
    body: request.body,
    redirect: "manual",
  });

  const originResponse = await fetch(originRequest);

  // Add failover marker header to response
  const modifiedResponse = new Response(originResponse.body, {
    status: originResponse.status,
    statusText: originResponse.statusText,
    headers: originResponse.headers,
  });
  modifiedResponse.headers.set("x-edgeoptimize-fo", "1");
  return modifiedResponse;
}
```

Klicken Sie auf **Save and deploy** (Speichern und bereitstellen), um den Worker zu veröffentlichen.

![Code-Editor für Cloudflare Worker](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Schritt 3: Konfigurieren von Umgebungsvariablen und Geheimnissen**

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

Unabhängig davon, welche Setup-Option Sie verwendet haben, müssen Sie den Worker manuell mit Ihrer Domain verknüpfen. Dieser Schritt aktiviert den Worker in Ihrem Traffic.

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
| 401- oder 403-Fehler von Edge Optimize | Ungültiger oder fehlender API-Schlüssel. | Stellen Sie sicher, dass `EDGE_OPTIMIZE_API_KEY` in Umgebungsvariablen und Geheimnissen korrekt festgelegt ist. Wenden Sie sich an Adobe, um zu bestätigen, dass Ihr API-Schlüssel aktiv ist. |
| Unendliche Weiterleitungen oder Schleifen | Schleifenschutz-Header ist nicht korrekt festgelegt oder wird nicht richtig überprüft. | Stellen Sie sicher, dass die Überprüfung des `x-edgeoptimize-request`-Headers eingerichtet ist. |
| Betroffener menschlicher Traffic | Routing-Logik für Worker ist zu breit angelegt. | Überprüfen Sie, ob die Zuordnungslogik des Benutzer-Agents korrekt ist und nicht zwischen Groß- und Kleinschreibung unterschieden wird. Überprüfen Sie, ob `TARGETED_PATHS` richtig konfiguriert ist. |
| Langsame Antwortzeiten | Netzwerklatenz zum Edge Optimize-Backend. | Dies ist für die erste Anfrage zu erwarten. Nachfolgende Anfragen werden bei Edge Optimize zwischengespeichert. |
| `x-edgeoptimize-fo: 1`-Header in Antwort | Edge Optimize hat einen Fehler zurückgegeben und es hat ein Failover zum Ursprung stattgefunden. | Überprüfen Sie die Cloudflare Workers-Protokolle auf den spezifischen Fehler-Code. Informieren Sie sich bei Adobe über den Dienststatus von Edge Optimize. |
| Failover funktioniert nicht | Failover-Flags deaktiviert oder Fehler in der Failover-Logik. | Überprüfen Sie, ob `FAILOVER_ON_4XX` und `FAILOVER_ON_5XX` auf `true` festgelegt sind. Prüfen Sie die Worker-Protokolle auf Fehlermeldungen. |
| Bestimmte Pfade werden nicht optimiert | Pfad stimmt nicht mit den Zielpfaden oder dem HTML-Seitenmuster überein. | Überprüfen Sie, ob sich der Pfad in `TARGETED_PATHS` befindet (falls angegeben) und mit dem Regex-Muster der HTML-Seite übereinstimmt. |
| Anfragen schlagen aufgrund eines ungültigen Hosts fehl | `EDGE_OPTIMIZE_TARGET_HOST` enthält Protokoll (zum Beispiel `https://`). | Verwenden Sie nur den Domain-Namen ohne Protokoll (zum Beispiel `example.com`, nicht `https://example.com`). |
| 530-Fehler beim Failover | Cloudflare kann keine Verbindung zum Ursprung herstellen oder die Failover-Anfrage hat ungültige Header. | Stellen Sie sicher, dass die Failover-Funktion Edge Optimize-Header entfernt. Stellen Sie sicher, dass auf Ihren Ursprung zugegriffen werden kann und dass DNS korrekt konfiguriert ist. |

**Zulassen, dass in Edge durch Firewall-Regeln optimiert wird (optional)**

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
