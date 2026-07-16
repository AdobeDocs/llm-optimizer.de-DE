---
title: Protokollweiterleitung – Andere Anbieter (manueller Upload)
description: Erfahren Sie, wie Sie CDN-Protokolle manuell in den S3-Bucket von Adobe für die Erfassung von Daten zu Agent-basiertem Traffic in LLM Optimizer hochladen, wenn Sie einen nicht unterstützten CDN-Anbieter verwenden.
feature: Agentic Traffic
autotag-review: '2026-07-15T18:08:55.588Z'
TQID: 'https://experienceleague.adobe.com/tuB95AJnFbB4O0o2BYHiRP-W0RTxzMeMLNg-5OjF-8s'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: dd952468-5202-43af-a365-6e0d2e67a703
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 670
ht-degree: 100%

---


# Protokollweiterleitung: Andere Anbieter (manueller Upload) {#log-forwarding-other}

Die Bereitstellungsmethode **Anderes BYOCDN** ist eine allgemeine Option für Nutzende, die CDN-Protokolle an LLM Optimizer unter folgenden Bedingungen bereitstellen möchten:

- **Manuelle Uploads** werden bevorzugt, z. B. exportieren operative Teams Protokolle und laden sie regelmäßig hoch.
- **Automatisierte Ad-hoc-Prozesse** werden verwendet (einmalige Skripte, geplante Exporte, Server-lose Aufträge).
- Es wird ein **CDN verwendet, das von integrierten Integrationen für die Protokollweiterleitung nicht nativ unterstützt wird**.

Diese Methode imitiert das Modell der „kontinuierlichen Weiterleitung“: Protokolle werden generiert, an den erwarteten S3-Speicherort hochgeladen und schließlich automatisch von den Aufnahme-Pipelines verarbeitet.

## Schritt 1: Durchführen des Onboardings in LLM Optimizer {#step-1}

In [LLM Optimizer](https://llmo.now/):

1. Navigieren Sie zu **Konfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die Registerkarte **CDN-Konfiguration**.

   ![Registerkarte „CDN-Konfiguration“](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie auf **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Erkenntnisse aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Sonstige** aus.

   ![Auswählen von „Sonstige“](/help/overview/assets/log-forwarding/other/other-select.png)

1. Klicken Sie auf **Integrieren**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Vorbereiten und Hochladen von Protokollen {#step-2}

### Erforderliches Protokollformat (JSON-Zeilen) {#log-format}

Protokolle müssen als per Zeilenumbruch getrennte JSON hochgeladen werden (**ein JSON-Objekt pro Zeile**). Jede Protokollzeile muss die folgenden Felder enthalten und zwar **genau wie unten angegeben**.

#### Schema für jedes Feld {#schema}

| Feld | Typ | Beschreibung | Beispiel |
|---|---|---|---|
| **timestamp** | Zeichenfolge | Der Zeitstempel der Anfrage gemäß **ISO-8601**-Format. | `"2025-02-01T23:00:05Z"` |
| **host** | Zeichenfolge | Die vom Client angeforderte Web-Domain. | `"www.example.com"` |
| **url** | Zeichenfolge | Die **Pfad**- und **Abrfageparameter** sind erforderlich, während die Domain **nicht** eingeschlossen werden soll. | `"/home?utm_source=google"` |
| **request_method** | Zeichenfolge | Die HTTP-Anfragemethode, manchmal auch als HTTP-Verben bezeichnet. | `"GET"` |
| **request_user_agent** | Zeichenfolge | Der HTTP-Benutzer-Agent-Anfrage-Header. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **request_referer** | Zeichenfolge | Der HTTP-Referrer-Anfrage-Header (kann leer sein). | `"https://chatgpt.com"` |
| **response_status** | Ganzzahl | Der HTTP-Antwort-Status-Code. | `200` |
| **response_content_type** | Zeichenfolge | Der HTTP-Content-Typ-Anfrage-Header. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Ganzzahl | Die Zeit zwischen dem Herstellen einer Verbindung zum Server und dem Herunterladen des Inhalts einer Web-Seite in **Millisekunden**. Setzen Sie diese auf null, wenn sie unbekannt oder nicht verfügbar ist. | `42` |

#### Beispiel für Protokollzeilen {#example}

Das folgende Beispiel zeigt drei Protokollzeilen an:

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Kritischer Haftungsausschluss (Schreibweise und Typen) {#disclaimer}

Die Aufnahme- und Aggregations-Pipelines sind strikt bezüglich **Feldnamen und Datentypen**.

- Feldnamen müssen **exakt** übereinstimmen (Groß-/Kleinschreibung und Schreibweise).
- Datentypen sollten korrekt sein und zwar wie folgt:
   - **timestamp** muss eine Zeichenfolge im **ISO-8601**-Format sein. UNIX-ähnliche Zeitstempel funktionieren möglicherweise nicht.
   - **response_status** muss eine Ganzzahl sein.
   - **time_to_first_byte** muss eine Ganzzahl sein und Millisekunden verwenden.
   - Zeichenfolgen müssen gültige JSON-Zeichenfolgen sein.
- Falsch formatierte JSON-Inhalte oder fehlende/falsche Felder können dazu führen, dass Protokolle übersprungen werden oder nicht geparst werden können, was zu fehlenden Daten in den Berichten führt.

### Upload-Speicherort und Verarbeitungskadenz {#upload-location}

#### Pfadregel {#path-rule}

Laden Sie Protokolle unter dem entsprechenden Ordnerpfad im folgenden Format hoch: **`yyyy/mm/dd/`** (mit Schrägstrichen).

Ein Beispielprotokoll vom 1. Februar 2025 UTC: `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Verarbeitungsregel {#processing-rule}

- Protokolle, die an einem bestimmten **UTC-Tag** hochgeladen wurden, werden von den Pipelines **gegen Ende dieses UTC-Tages** verarbeitet (täglicher Durchlauf).
- Protokolle, die in **Ordner vergangener Tage** hochgeladen werden (Aufstockung), werden innerhalb von 24 Stunden **erkannt und verarbeitet**.

## Szenarien {#scenarios}

### Szenario 1: Protokolle in Splunk/Elasticsearch – Exportieren und Hochladen in S3 {#scenario-splunk}

**Ziel**: Abrufen von Protokollen aus vorhandenen Beobachtbarkeitsplattformen und Bereitstellen an den S3-Speicherort.

- Extrahieren Sie die erforderlichen Felder aus Splunk-/Elasticsearch-Ereignissen.
- Wandeln Sie jedes Ereignis in ein JSON-Objekt gemäß dem obigen Schema um (JSON-Zeilen).
- Laden Sie die resultierende(n) Datei(en) in den angegebenen S3-Bucket und den Pfad des **aktuellen UTC-Tages** hoch: `…/byocdn-other/yyyy/mm/dd/`
- Die Protokolle werden am Ende des UTC-Tages automatisch verarbeitet.

### Szenario 2: Lambda-/Azure-Funktion – Formatieren und Hochladen in S3 {#scenario-serverless}

**Ziel**: Verwenden von Server-losen Berechnungen zum Abrufen/Empfangen von CDN-Protokollen, Normalisieren von diesen und Bereitstellen von diesen an den S3-Speicherort.

- Die Funktion ruft Protokolle aus der Quelle der Kundschaft ab (Protokollspeicher, Warteschlange, Blob-Speicher usw.).
- Die Funktion ordnet Felder dem erwarteten Schema zu und gibt **JSON-Zeilen** aus.
- Die Funktion lädt die Ausgabe hoch in: `…/byocdn-other/yyyy/mm/dd/`
- Die Protokolle werden am Ende des UTC-Tages automatisch verarbeitet.

## Schnelle Checkliste {#checklist}

- **Ein JSON-Objekt pro Zeile** (JSON-Zeilen)
- **Schreibweise der Felder exakt** wie angegeben
- Korrekte Datentypen
- **time_to_first_byte** in Millisekunden (Ganzzahl)
- Hochladen in entsprechenden UTC-Ordner: **JJJJ/MM/TT/** unter **byocdn-other**
