---
title: Optimieren bei Edge - Cloudflare (BYOCDN)
description: Erfahren Sie, wie Sie Cloudflare BYOCDN for Optimize bei Edge in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 1%

---


# Cloudflare (BYOCDN)

Diese Konfiguration leitet den Agentenverkehr (Anfragen von KI-Bots und LLM-Benutzeragenten) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besucher und SEO-Bots werden weiterhin von Ihrem Ursprung aus bedient. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

**Voraussetzungen**

Bevor Sie die Routing-Regeln für Cloudflare-Worker einrichten, stellen Sie sicher, dass Sie über Folgendes verfügen:

* Ein Cloudflare-Konto mit aktivierten Workers in Ihrer Domain.
* Zugriff auf die DNS-Einstellungen Ihrer Domain in Cloudflare.
* Onboarding-Prozess für LLM Optimizer abgeschlossen.
* CDN-Protokollweiterleitung an LLM Optimizer abgeschlossen.
* Einen Edge Optimize-API-Schlüssel, der von der LLM Optimizer-Benutzeroberfläche abgerufen wurde.

{{retrieve-byocdn-api-key}}

**Funktionsweise des Routings**

Bei korrekter Konfiguration wird eine Anfrage an Ihre Domain (z. B. `www.example.com/page.html`) von einem Agent-Benutzeragenten vom Cloudflare-Worker abgefangen und an das Edge Optimizer-Backend weitergeleitet. Die Backend-Anfrage enthält die erforderlichen Kopfzeilen.

**Testen der Backend-Anfrage**

Sie können das Routing überprüfen, indem Sie eine direkte Anfrage an das Backend von Edge Optimize stellen.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**Erforderliche Kopfzeilen**

Bei Anfragen an das Backend von Edge Optimize müssen die folgenden Kopfzeilen festgelegt werden:

| Kopfzeile | Beschreibung | Beispiel |
|--------|-------------|---------|
| `x-forwarded-host` | Der ursprüngliche Host der Anfrage. Erforderlich zum Identifizieren der Website-Domain. | `www.example.com` |
| `x-edgeoptimize-url` | Der ursprüngliche URL-Pfad und die Abfragezeichenfolge der Anfrage. | `/page.html` oder `/products?id=123` |
| `x-edgeoptimize-api-key` | Der von Adobe für Ihre Domain bereitgestellte API-Schlüssel. | `your-api-key-here` |
| `x-edgeoptimize-config` | Konfigurations-String zur Cache-Schlüsseldifferenzierung. | `LLMCLIENT=TRUE;` |

**Schritt 1: Erstellen des Cloudflare-Sekundärs**

1. Melden Sie sich bei Ihrem Cloudflare-Dashboard an.
2. Navigieren Sie in **Seitenleiste zu** Arbeiter und Seiten“.
3. Klicken Sie **Anwendung erstellen** und dann **Worker erstellen**.
4. Benennen Sie Ihren Worker (z. B. `edge-optimize-router`).
5. Klicken Sie **Bereitstellen**, um den Worker mit dem Standard-Code zu erstellen.

![Cloudflare-Workers-Dashboard](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Schritt 2: Fügen Sie den Worker-Code hinzu**

Klicken Sie nach dem Erstellen des Workers auf **Code bearbeiten** und ersetzen Sie den Standard-Code durch Folgendes:

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

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

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

Klicken Sie **Speichern und Bereitstellen**, um den Worker zu veröffentlichen.

![Cloudflare-Worker-Code-Editor](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Schritt 3: Konfigurieren von Umgebungsvariablen**

Umgebungsvariablen speichern vertrauliche Konfigurationen wie Ihren API-Schlüssel sicher.

1. Navigieren Sie in den Einstellungen Ihres Sekundärs zu **Einstellungen** > **Variablen**.
2. Klicken **unter &quot;**&quot; auf **Variable hinzufügen**.
3. Fügen Sie die folgenden Variablen hinzu:

   | Variablenname | Beschreibung | Erforderlich |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Ihr von Adobe bereitgestellter API-Schlüssel für Edge Optimize. | Ja |
   | `EDGE_OPTIMIZE_TARGET_HOST` | Der Ziel-Host für Edge Optimize-Anfragen (als `x-forwarded-host`-Header gesendet) und die Ursprungs-Domain für das Failover. Darf nur die Domain ohne Protokoll sein (z. B. `www.example.com`, nicht `https://www.example.com`). | Ja |

4. Klicken Sie für den API-Schlüssel auf **Verschlüsseln**, um ihn sicher zu speichern.
5. Klicken Sie **Speichern und bereitstellen**.

![Cloudflare-Umgebungsvariablen](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

**Schritt 4: Hinzufügen einer Route zu Ihrer Domain**

So aktivieren Sie den Worker in Ihrer Domain:

1. Navigieren Sie zu den **Einstellungen** > **Trigger**.
2. Klicken **unter „Routen** auf **Route hinzufügen**.
3. Geben Sie Ihr Domain-Muster ein (z. B. `www.example.com/*` oder `example.com/*`).
4. Wählen Sie Ihre Zone im Dropdown-Menü aus.
5. Klicken Sie auf **Speichern**.

Alternativ können Sie Routen auf Zonenebene konfigurieren:

1. Navigieren Sie zu Ihrer Domain in Cloudflare.
2. Gehen Sie zu **Arbeiter-Routen**.
3. Klicken Sie **Route hinzufügen** und geben Sie das Muster und den Worker an.

![Cloudflare-Arbeitsrouten](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Überprüfen des Failover-Verhaltens**

Wenn Edge Optimize nicht verfügbar ist oder einen Fehler zurückgibt, führt der Worker automatisch ein Failover zu Ihrer Herkunft durch. Die Failover-Antworten enthalten die `x-edgeoptimize-fo`:

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Sie können Failover-Ereignisse in den Cloudflare Workers-Protokollen überwachen, um Probleme zu beheben.

**Verstehen der Worker-Logik**

Der Cloudflare-Worker implementiert die folgende Logik:

1. **Erkennung von Benutzeragenten:** Prüft, ob der Benutzeragent der eingehenden Anfrage mit einem der definierten Agentbots übereinstimmt (ignoriert Groß-/Kleinschreibung).

2. **Pfad-Targeting** Filtert Anfragen optional nach Zielpfaden. Standardmäßig werden alle HTML-Seiten (URLs, die mit `/`, keiner Erweiterung oder `.html` enden) weitergeleitet. Sie können bestimmte Pfade mithilfe des `TARGETED_PATHS`-Arrays angeben.

3. **Schleifenschutz:** Der `x-edgeoptimize-request`-Header verhindert unendliche Schleifen. Wenn Edge Optimize Anfragen an Ihren Ursprung zurücksendet, wird diese Kopfzeile auf `"1"` festgelegt, und der Worker übergibt die Anfrage an , ohne sie zurück an Edge Optimize zu leiten.

4. **Header-Sicherheit:** Bevor Sie Edge Optimize-Header festlegen, entfernt der Worker alle vorhandenen `x-edgeoptimize-*`-Header aus der eingehenden Anfrage, um Header-Injection-Angriffe zu verhindern.

5. **Header-Zuordnung:** Der Worker legt die erforderlichen Header für Edge Optimize fest:
   * `x-forwarded-host` - Identifiziert die ursprüngliche Site-Domain.
   * `x-edgeoptimize-url` - Behält den ursprünglichen Anfragepfad und die Abfragezeichenfolge bei.
   * `x-edgeoptimize-api-key` - Authentifiziert die Anfrage mit Edge Optimize.
   * `x-edgeoptimize-config` - Stellt die Konfiguration des Cache-Schlüssels bereit.

6. **Failover-Logik:** Wenn Edge Optimize einen Fehlerstatus-Code (4XX-Client- oder 5XX-Server-Fehler) zurückgibt oder die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt, schlägt der Worker mithilfe von `EDGE_OPTIMIZE_TARGET_HOST` automatisch auf Ihren Ursprung fehl. Die Failover-Antwort enthält den `x-edgeoptimize-fo: 1`-Header, um anzugeben, dass ein Failover aufgetreten ist.

7. **Umleitungshandhabung:** Die Option &quot;`redirect: "manual"`&quot; stellt sicher, dass Umleitungsantworten von Edge Optimize an den Client weitergeleitet werden, ohne dass der Worker ihnen folgt.

**Anpassen der Konfiguration**

Sie können das Workerverhalten anpassen, indem Sie die Konfigurationskonstanten oben im Code ändern:

**Agent-Bot-Liste**

Ändern Sie das `AGENTIC_BOTS`-Array, um Benutzeragenten hinzuzufügen oder zu entfernen:

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

Standardmäßig werden alle HTML-Seiten an Edge Optimizer weitergeleitet. Um das Routing auf bestimmte Pfade zu beschränken, ändern Sie das `TARGETED_PATHS`-Array:

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Failover-Konfiguration**

Standardmäßig schlägt der Worker bei einem 4XX- oder 5XX-Fehler von Edge Optimize fehl. Dieses Verhalten anpassen:

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

* **Failover-Verhalten:** Der Worker führt automatisch ein Failover zu Ihrem Ursprung durch, wenn Edge Optimize einen Fehler zurückgibt (Status-Codes 4XX oder 5XX) oder wenn die Anfrage aufgrund eines Netzwerkfehlers fehlschlägt. Bei Failover wird `EDGE_OPTIMIZE_TARGET_HOST` als Ursprungs-Domain verwendet (ähnlich wie bei Fastly `F_Default_Origin` oder CloudFront `Default_Origin`). Failoverantworten enthalten den `x-edgeoptimize-fo: 1`-Header, den Sie zum Überwachen und Debuggen verwenden können.

* **Caching:** Cloudflare speichert Antworten standardmäßig basierend auf der URL zwischen. Da der Agent-Traffic andere Inhalte erhält als menschlicher Traffic, stellen Sie sicher, dass dies in der Cache-Konfiguration berücksichtigt wird. Erwägen Sie die Verwendung der Cache-API oder Cache-Kopfzeilen, um zwischengespeicherte Inhalte zu unterscheiden. Die `x-edgeoptimize-config`-Kopfzeile sollte in Ihrem Cache-Schlüssel enthalten sein.

* **Ratenbegrenzung:** Überwachen Sie die Nutzung von Edge Optimize und erwägen Sie bei Bedarf die Implementierung einer Ratenbegrenzung für den agenten Traffic.

* **Testen** Testen Sie die Konfiguration immer in einer Staging-Umgebung, bevor Sie sie in der Produktion bereitstellen. Stellen Sie sicher, dass sich der Traffic von Agenten und Menschen erwartungsgemäß verhält. Testen Sie das Failover-Verhalten durch Simulation von Edge Optimize-Fehlern.

* **Protokollierung:** Sie die Protokollierung von Cloudflare-Sekundären, um Anfragen zu überwachen und Probleme zu beheben. Navigieren Sie **Worker** > **Ihr Worker** > **Protokolle**, um Echtzeit-Protokolle anzuzeigen. Der Worker protokolliert Failover-Ereignisse zu Debugging-Zwecken.

**Fehlerbehebung**

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| Keine `x-edgeoptimize-request-id`-Kopfzeile in Antwort | Arbeitsroute nicht zugeordnet oder Benutzeragent nicht in der Agentenbots-Liste. | Stellen Sie sicher, dass Ihr Routenmuster mit der Anfrage-URL übereinstimmt. Prüfen Sie, ob sich der Benutzeragent im `AGENTIC_BOTS`-Array befindet. |
| 401- oder 403-Fehler von Edge Optimize | Ungültiger oder fehlender API-Schlüssel. | Stellen Sie sicher, dass `EDGE_OPTIMIZE_API_KEY` in Umgebungsvariablen korrekt festgelegt ist. Adobe kontaktieren, um zu bestätigen, dass Ihr API-Schlüssel aktiv ist. |
| Unendliche Weiterleitungen oder Schleifen | Schleifenschutz-Kopfzeile wird nicht richtig eingestellt oder überprüft. | Stellen Sie sicher, dass die `x-edgeoptimize-request` Kopfzeilenprüfung vorhanden ist. |
| Betroffener Menschenhandel | Routing-Logik für Worker ist zu breit angelegt. | Stellen Sie sicher, dass die Zuordnungslogik des Benutzeragenten korrekt ist und nicht zwischen Groß- und Kleinschreibung unterschieden wird. Überprüfen Sie, ob `TARGETED_PATHS` richtig konfiguriert ist. |
| Langsame Reaktionszeiten | Netzwerklatenz zum Edge Optimize-Backend. | Dies ist für die erste Anfrage zu erwarten. Nachfolgende Anfragen werden bei Edge Optimize zwischengespeichert. |
| `x-edgeoptimize-fo: 1` in Antwort | Edge Optimize hat einen Fehler zurückgegeben, und es ist ein Failover zum Ursprung aufgetreten. | Überprüfen Sie die Cloudflare Workers-Protokolle auf den spezifischen Fehler-Code. Überprüfen Sie den Service-Status von Edge Optimize mit Adobe. |
| Failover funktioniert nicht | Failover-Flags deaktiviert oder Fehler in der Failover-Logik. | Überprüfen Sie, ob `FAILOVER_ON_4XX` und `FAILOVER_ON_5XX` auf `true` eingestellt sind. Überprüfen Sie die Worker-Protokolle auf Fehlermeldungen. |
| Bestimmte Pfade werden nicht optimiert | Pfad stimmt nicht mit den Zielpfaden oder dem HTML-Seitenmuster überein. | Stellen Sie sicher, dass der Pfad in `TARGETED_PATHS` ist (falls angegeben) und mit dem HTML-Seiten-Regex-Muster übereinstimmt. |
| Fehlgeschlagene Anfragen mit ungültigem Host | `EDGE_OPTIMIZE_TARGET_HOST` umfasst das -Protokoll (z. B. `https://`). | Nur den Domain-Namen ohne Protokoll verwenden (z. B. `example.com`, nicht `https://example.com`). |
| 530-Fehler beim Failover | Cloudflare kann keine Verbindung zur Quelle herstellen, oder die Failover-Anfrage hat ungültige Kopfzeilen. | Stellen Sie sicher, dass die Failover-Funktion Edge Optimize-Kopfzeilen entfernt. Stellen Sie sicher, dass auf Ihre Herkunft zugegriffen werden kann und dass das DNS korrekt konfiguriert ist. |

{{verify-setup-byocdn}}

{{return-to-overview}}
