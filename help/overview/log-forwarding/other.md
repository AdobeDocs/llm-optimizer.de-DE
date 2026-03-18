---
title: Protokollweiterleitung - Sonstige (manueller Upload)
description: Erfahren Sie, wie Sie bei Verwendung eines nicht unterstützten CDN-Anbieters CDN-Protokolle manuell in den S3-Bucket von Adobe für die agentische Traffic-Datenerfassung in LLM Optimizer hochladen.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---


# Protokollweiterleitung: Sonstige (manueller Upload) {#log-forwarding-other}

Die **Andere BYOCDN**-Bereitstellungsmethode ist eine Sammeloption für Kunden, die CDN-Protokolle an LLM Optimizer bereitstellen möchten, wenn:

- **Manuelle Uploads** werden bevorzugt, z. B. exportieren operative Teams Protokolle und laden sie regelmäßig hoch.
- **Ad-hoc automatisierte Prozesse** werden verwendet - einmalige Skripte, geplante Exporte, Server-lose Aufträge.
- Der Kunde verwendet ein **CDN, das von** integrierten Integrationen für die Protokollweiterleitung nicht nativ unterstützt wird.

Diese Methode imitiert das Modell der „kontinuierlichen Weiterleitung“: Protokolle werden erstellt und an den erwarteten S3-Speicherort hochgeladen und schließlich automatisch von den Aufnahme-Pipelines verarbeitet.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf [LLM Optimizer](https://llmo.now/):

1. Navigieren Sie zu **Konfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie **Erste Schritte**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)

1. Wählen Sie **Sonstige** aus.

   ![Andere auswählen](/help/overview/assets/log-forwarding/other/other-select.png)

1. Klicken Sie **Onboard**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Schritt 2: Protokolle vorbereiten und hochladen {#step-2}

### Erforderliches Protokollformat (JSON-Zeilen) {#log-format}

Protokolle müssen als durch Zeilenumbruch getrennte JSON hochgeladen werden (**ein JSON-Objekt pro Zeile**). Jede Protokollzeile muss die folgenden Felder enthalten **genau wie unten angegeben**.

#### Schema für jedes Feld {#schema}

| Feld | Typ | Beschreibung | Beispiel |
|---|---|---|---|
| **timestamp** | Zeichenfolge | Der Zeitstempel der Anfrage im Format **ISO 8601**. | `"2025-02-01T23:00:05Z"` |
| **host** | Zeichenfolge | Die vom Client angeforderte Web-Domain. | `"www.example.com"` |
| **url** | Zeichenfolge | **path** und die **Abfrageparameter** sind erforderlich, während die Domain **not** enthalten sein sollte. | `"/home?utm_source=google"` |
| **request_method** | Zeichenfolge | Die HTTP-Anfragemethode, manchmal auch als HTTP-Verben bezeichnet. | `"GET"` |
| **request_user_agent** | Zeichenfolge | Der HTTP-User-Agent-Anfrage-Header. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **request_referer** | Zeichenfolge | Die Kopfzeile der HTTP-Referrer-Anfrage (kann leer sein). | `"https://chatgpt.com"` |
| **RESPONSE_STATUS** | Ganzzahl | Der HTTP-Antwort-Status-Code. | `200` |
| **response_content_type** | Zeichenfolge | Die Antwort-Kopfzeile für den HTTP-Inhaltstyp. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Ganzzahl | Die Zeit zwischen dem Erstellen einer Verbindung zum Server und dem Herunterladen des Inhalts einer Web-Seite in **Millisekunden**. Auf null setzen, wenn unbekannt oder nicht verfügbar. | `42` |

#### Beispiel für Protokollzeilen {#example}

Das folgende Beispiel zeigt drei Protokollzeilen:

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Kritischer Haftungsausschluss (Rechtschreibung und Typen) {#disclaimer}

Die Aufnahme- und Aggregations-Pipelines sind strikt auf **Feldnamen und Datentypen**.

- Feldnamen müssen mit &quot;**&quot; übereinstimmen** Groß- und Kleinschreibung).
- Datentypen sollten wie folgt korrekt sein:
   - **Zeitstempel** muss eine Zeichenfolge im **ISO 8601**-Format sein. UNIX-ähnliche Zeitstempel funktionieren möglicherweise nicht.
   - **RESPONSE_STATUS** muss eine Ganzzahl sein.
   - **time_to_first_byte** muss eine Ganzzahl sein und Millisekunden verwenden.
   - Zeichenfolgen müssen gültige JSON-Zeichenfolgen sein.
- Falsch formatiertes JSON oder fehlende/falsche Felder können dazu führen, dass Protokolle übersprungen werden oder nicht geparst werden können, was zu fehlenden Daten in den Berichten führt.

### Upload-Speicherort und Verarbeitungskadenz {#upload-location}

#### Pfadregel {#path-rule}

Laden Sie Protokolle unter dem entsprechenden Ordnerpfad im folgenden Format hoch: **`yyyy/mm/dd/`** (mit Schrägstrichen).

Ein Beispielprotokoll vom 1. Februar 2025 UTC: `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Verarbeitungsregel {#processing-rule}

- Protokolle, die an einem bestimmten **UTC-Tag** hochgeladen wurden, werden von den Pipelines verarbeitet **gegen Ende dieses UTC-Tages** (täglicher Durchlauf).
- Protokolle, die in **Ordner „vergangener Tage“ hochgeladen** (Aufstockung), werden **24** erkannt und verarbeitet.

## Szenarien {#scenarios}

### Szenario 1: Protokolle in Splunk/Elasticsearch — Exportieren und Hochladen in S3 {#scenario-splunk}

**Ziel**: Abrufen von Protokollen aus vorhandenen Beobachtbarkeitsplattformen und Bereitstellen an den S3-Speicherort.

- Extrahieren Sie die erforderlichen Felder aus Splunk-/Elastic-Suchereignissen.
- Wandeln Sie jedes Ereignis in ein JSON-Objekt gemäß dem obigen Schema um (JSON-Zeilen).
- Laden Sie die resultierende(n) Datei(en) in den angegebenen S3-Bucket und den Pfad **aktuellen UTC-**) hoch: `…/byocdn-other/yyyy/mm/dd/`
- Die Protokolle werden am Ende des UTC-Tages automatisch verarbeitet.

### Szenario 2: Lambda-/Azure-Funktion — Formatieren und Hochladen in S3 {#scenario-serverless}

**Ziel**: Verwenden Sie Server-lose Berechnungen, um CDN-Protokolle abzurufen/zu empfangen, sie zu normalisieren und an den S3-Speicherort bereitzustellen.

- Die Funktion ruft Protokolle aus der Quelle des Kunden ab (Protokollspeicher, Warteschlange, Blob-Speicher usw.).
- Die Funktion ordnet Felder dem erwarteten Schema zu und gibt **JSON-Zeilen** aus.
- Die Funktion lädt Ausgabe in: `…/byocdn-other/yyyy/mm/dd/` hoch
- Die Protokolle werden am Ende des UTC-Tages automatisch verarbeitet.

## Schnellprüfliste {#checklist}

- **Ein JSON-Objekt pro Zeile** (JSON-Zeilen)
- **Exakte Feldschreibweise** wie angegeben
- Korrigieren von Datentypen
- **time_to_first_byte** in Millisekunden (Ganzzahl)
- Laden Sie in den entsprechenden UTC-Ordner hoch: **jjjj/mm/tt/** unter **byocdn-other**
