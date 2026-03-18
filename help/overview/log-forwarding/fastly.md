---
title: Protokollweiterleitung - Fastly
description: Erfahren Sie, wie Sie CDN-Protokolle zur Erfassung von agenten Traffic-Daten in LLM Optimizer von Fastly an den S3-Bucket von Adobe weiterleiten.
feature: Agentic Traffic
source-git-commit: d1f98770b39f550c36d93ece9b89933c0e90f189
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 4%

---


# Protokollweiterleitung: Fastly {#log-forwarding-fastly}

Auf dieser Seite wird erläutert, wie Sie CDN-Protokolle zur Erfassung von Traffic-Daten von Fastly an den S3-Bucket von Adobe weiterleiten. Sie verwenden die LLM Optimizer CDN-Konfigurationsseite, um sich bei LLM Optimizer einzuarbeiten. Nachdem der Onboarding-Prozess abgeschlossen ist, führen Sie die auf dieser Seite angegebenen Schritte aus, um die Protokollweiterleitung in der Fastly-Web-Konsole zu konfigurieren.

## Schritt 1: Onboarding in LLM Optimizer {#step-1}

Auf der LLM Optimizer-Seite [https://llmo.now/](https://llmo.now/):

1. Navigieren Sie zu **Konfiguration**.

   ![Schaltfläche „Konfiguration“](/help/overview/assets/log-forwarding/common/config-button.png)

1. Klicken Sie auf die **CDN-Konfiguration**.

   ![Registerkarte CDN-Konfiguration](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Klicken Sie **Erste Schritte**.
1. Klicken Sie neben **KI-Traffic-Einblicke aktivieren** auf **Konfigurieren**.

   ![Konfigurieren](/help/overview/assets/log-forwarding/common/configure.png)
1. Wählen Sie **Fastly (BYOCDN)**.

   ![Fastly auswählen](/help/overview/assets/log-forwarding/fastly/fastly-select.png)
1. Klicken Sie **Onboard**.

## Schritt 2: Erstellen eines S3-Endpunkts in Fastly {#step-2}

So erstellen Sie einen S3-Endpunkt im **Fastly Control Panel**:

1. Gehen Sie im Fastly-Dashboard zu **CDN-Services** (nicht zu Compute-Services).
1. Klicken Sie im Bereich **Amazon Web Services S3** auf **Endpunkt erstellen**.
1. Füllen Sie die Felder **Erstellen eines Amazon S3** Endpunkts aus:

| Feld | Beschreibung |
| --- | --- |
| **Name** | Vom Menschen lesbarer Name für den Endpunkt. |
| **Platzierung** | Standard |
| **Protokollformat** | Verwenden Sie die Zeichenfolge für das Protokollformat, die im Abschnitt **Zeichenfolge für das Protokollformat** unten angezeigt wird. |
| **Zeitstempelformat** | `%Y-%m-%dT%H:%M:%S.000` |
| **Behältername** | Kopieren Sie den **Behälternamen** aus der LLM Optimizer-Konfigurationsseite. ![Bucket-Name](/help/overview/assets/log-forwarding/fastly/fastly-bucket-name.png) |
| **Domain** | Kopieren Sie **Domain-**) von der Seite LLM Optimizer-Konfiguration . ![Domain-Name](/help/overview/assets/log-forwarding/fastly/fastly-domain-name.png) |
| **Zugriffsmethode** | **Benutzeranmeldeinformationen** |
| **Benutzeranmeldeinformationen** | Kopieren Sie den **Zugriffsschlüssel** und den **Geheimschlüssel** von der LLM Optimizer-Konfigurationsseite. ![Zugriffsschlüssel](/help/overview/assets/log-forwarding/common/access-keys.png) |
| **Zeitraum** | `300` |

**Protokollformat-Zeichenfolge:**

```json
{ "timestamp": "%{strftime(\{"%Y-%m-%dT%H:%M:%S%z"\}, time.start)}V", "host": "%{if(req.http.Fastly-Orig-Host, req.http.Fastly-Orig-Host, req.http.Host)}V", "url": "%{json.escape(req.url)}V", "request_method": "%{json.escape(req.method)}V", "request_referer": "%{json.escape(req.http.referer)}V", "request_user_agent": "%{json.escape(req.http.User-Agent)}V", "response_status": %{resp.status}V, "response_content_type": "%{json.escape(resp.http.Content-Type)}V", "client_country_code": "%{client.geo.country_name}V", "time_to_first_byte": "%{time.to_first_byte}V" }
```

>[!WARNING]
>
>Passwort-Manager können das Feld **Geheimschlüssel** automatisch mit Ihrem Fastly-Passwort ausfüllen. Wenn die AWS-Integration fehlschlägt, geben Sie den geheimen Schlüssel manuell ein.

Klicken Sie nach Abschluss der oben genannten Schritte auf **Erweiterte Optionen** und legen Sie Folgendes fest:

| Feld | Beschreibung |
| --- | --- |
| **Pfad** | Kopieren Sie **Pfad** von der LLM Optimizer-Konfigurationsseite. ![Pfad](/help/overview/assets/log-forwarding/fastly/fastly-path.png) |
| **Protokollzeilenformat auswählen** | Leer |
| **Komprimierung** | Gzip |
| **Redundanzstufe** | Standard |
| **ACL** | Keine |
| **Server-seitige Verschlüsselung** | Keine |
| **Maximale Bytes** | 0 |

Nach dem Festlegen der erweiterten Optionen:

1. Klicken Sie **Erstellen**, um den Endpunkt zu erstellen.
1. Wählen Sie im Menü **Aktivieren** die Option **Bei Produktion aktivieren** aus, um die Bereitstellung durchzuführen.

>[!NOTE]
>
>Fastly streamt Protokolle kontinuierlich auf S3, die S3-Website und die API stellt Dateien erst nach Abschluss des Uploads zur Verfügung.

### Beispiel für einen Protokolleintrag {#example}

Nachfolgend finden Sie eine Beispiel-Formatzeichenfolge für das Senden von Daten an Amazon S3:

```json
{
  "timestamp": "2026-02-10T05:05:36+0000",
  "host": "example.com",
  "url": "/my/path",
  "request_method": "GET",
  "request_referer": "https://example.com/my/other/path",
  "request_user_agent": "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
  "response_status": 200,
  "response_content_type": "text/css; charset=utf-8",
  "client_country_code": "argentina",
  "time_to_first_byte": "0.138"
}
```
