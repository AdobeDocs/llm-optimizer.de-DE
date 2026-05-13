---
title: Google Analytics-Integration
description: Erfahren Sie, wie Sie Google Analytics 4 mit LLM Optimizer verbinden, um KI-gesteuerte Erkennung, Site-Interaktion und Geschäftsergebnisse im Referral Traffic-Dashboard zu messen.
feature: Referral Traffic
source-git-commit: 368b3c1ee79660ede0c4bf9824f299d2e801c8b2
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 1%

---


# Google Analytics-Integration

Die Google Analytics 4 (GA4)-Integration verbindet LLM Optimizer mit den GA4-Daten Ihres Unternehmens, sodass Sie messen können, wie sich die KI-gesteuerte Erkennung auf Plattformen wie ChatGPT, Gemini, Copilot, Claude und Perplexity in echte Website-Interaktion und Geschäftsergebnisse niederschlägt. Nachdem Sie eine GA4-Eigenschaft verbunden haben, ruft LLM Optimizer die Referral Traffic-, Interaktions- und Konversionsmetriken ab, die GA4 diesen Quellen zuordnet, und zeigt sie im Dashboard **Referral Traffic** auf der Registerkarte **Geschäftsauswirkungen** an.

>[!IMPORTANT]
>
>Die GA4-Integration ist im kostenpflichtigen LLM Optimizer-Angebot enthalten. Kunden, die die kostenlose Testversion verwenden, können GA4 erst dann verbinden, wenn sie ein kostenpflichtiges Upgrade erhalten haben.

## Vorbereitung {#before-you-begin}

Um die Verbindung abzuschließen, benötigen Sie Folgendes:

* Ein Google-Konto mit mindestens **Viewer**-Zugriff auf die GA4-Eigenschaft, die Sie verbinden möchten. Der Zugriff auf Eigenschaftsebene wird in Google Analytics unter **Admin > Zugriffsverwaltung für Eigenschaften** verwaltet.
* Berechtigung zur Konfigurationsverwaltung in LLM Optimizer (andernfalls wird die Schaltfläche Verbinden angezeigt, aber deaktiviert).
* Ein Browser, der Popups von der LLM Optimizer-Herkunft aus zulässt - der Google-Anmeldeschritt wird auf einer neuen Registerkarte geöffnet.

Sie **kein Google** Cloud-Projekt erstellen, ein Service-Konto generieren, einen JSON-Schlüssel hochladen oder eine Eigenschafts-ID eingeben. LLM Optimizer vermittelt die Verbindung über den standardmäßigen OAuth-Einverständnisbildschirm von Google.

## Verbinden von GA4 mit dem Referral Traffic-Dashboard {#connect}

Der Verbindungsfluss beginnt wie folgt vom [Referral Traffic](/help/dashboards/referral-traffic.md)-Dashboard:

1. Öffnen Sie **Referral Traffic** in LLM Optimizer.

1. Öffnen Sie die Registerkarte **Geschäftsauswirkungen**.

   ![Referral Traffic-Dashboard, Registerkarte „Geschäftsauswirkungen“](/help/dashboards/assets/ga4-integration-01-business-impact-tab.png)

1. Wählen Sie **Mit Analytics verbinden** aus. LLM Optimizer leitet Sie zu **Kundenkonfiguration > Analytics** weiter. Wählen Sie in der Auswahl des Analytics-Anbieters die Option **Google Analytics 4 verbinden** aus.

   ![Kundenkonfiguration, Registerkarte „Analytics“ mit ausgewählter GA4](/help/dashboards/assets/ga4-integration-02-analytics-ga4-picker.png)

1. Wählen Sie **Konto verbinden** aus. Eine neue Browser-Registerkarte wird geöffnet, auf der der Google-Anmeldebildschirm angezeigt wird.

   ![Google-Anmeldung für GA4-Verbindung](/help/dashboards/assets/ga4-integration-03-google-sign-in.png)

1. Melden Sie sich mit dem Google-Konto an, das Zugriff auf die GA4-Eigenschaft hat, mit der Sie eine Verbindung herstellen möchten. Genehmigen Sie die `See and download your Google Analytics data` Berechtigung (`analytics.readonly` Bereich), wenn Google Sie dazu auffordert.

1. Google sendet Sie zurück zu LLM Optimizer, wo die GA4-Eigenschaften aufgeführt sind, auf die Ihr Konto zugreifen kann. Wählen Sie die Eigenschaft aus, die verbunden und gesendet werden soll.

1. Kehren Sie zur Registerkarte LLM Optimizer zurück. Die Registerkarte Analytics erkennt die abgeschlossene Verbindung automatisch und die GA4-Karte zeigt den Status **Verbunden** an.

### Nach dem Verbinden {#after-connect}

Nachdem GA4 mit LLM Optimizer verbunden ist, geschieht Folgendes:

* LLM Optimizer füllt die **letzten vier vollen Kalenderwochen** und die **aktuelle Kalenderwoche bis heute** auf.
* Nach der Aufstockung werden die Daten **täglich** mit einem Pull des **ganzen Vortags** aktualisiert.

>[!NOTE]
>
>Die Aufstockung kann einige Stunden dauern. Das Dashboard „Geschäftsauswirkungen“ wird immer stärker angezeigt, wenn Daten landen. Sie müssen nichts unternehmen, während die Aufstockung ausgeführt wird.

Wenn Sie die Verbindung wiederherstellen (z. B. um entweder das Google-Konto oder die GA4-Eigenschaft zu wechseln), wird nur die aktuelle Kalenderwoche erneut aufgestockt. Bereits geladene vorherige Wochen bleiben erhalten.

## Funktionsweise {#how-it-works}

### Verbindungsmodell

Die Integration verwendet den standardmäßigen, von Benutzenden delegierten OAuth 2.0-Fluss von Google. LLM Optimizer speichert ein Aktualisierungstoken, das sich auf Ihre ausgewählte GA4-Eigenschaft bezieht, und dieses Token ermöglicht LLM Optimizer, die GA4-Daten-API in Ihrem Namen aufzurufen (mit schreibgeschütztem Zugriff), bis Sie es von Ihrem Google-Konto widerrufen.

### So wird LLM-Traffic identifiziert

LLM Optimizer fragt GA4 nur für die Sitzungen an, die GA4 selbst einer LLM-Plattform zuordnet. Heute sind dies Sitzungen, deren `sessionSourceMedium` einem von `chatgpt`, `gemini.google.com`, `copilot.microsoft.com`, `claude` oder `perplexity` entspricht. Die Liste der unterstützten LLM-Quellen wird von Adobe verwaltet und kann im Laufe der Zeit erweitert werden.

### Aufgenommene Daten {#data-ingested}

Jeder tägliche Pull ruft einen aggregierten Bericht ab, der Folgendes enthält:

**Dimensionen**

| GA4-Dimension | Was es repräsentiert |
| --- | --- |
| `date` | Der Tag, an dem die Sitzung stattfand. |
| `landingPage` | Die erste Seite, die der Besucher auf Ihrer Site gesehen hat. |
| `countryId` | Das Land des Besuchers, wie durch die IP-Geolokalisierung von GA4 bestimmt. |
| `deviceCategory` | Mobil / Desktop / Tablet. |
| `sessionSourceMedium` | Die von GA4 zugewiesene LLM-Quelle/Medium. |

**Metriken**

| GA4-Metrik | Was es repräsentiert |
| --- | --- |
| `sessions` | Anzahl der Sitzungen im Bucket. |
| `screenPageViews` | Seitenansichten im Bucket. |
| `bounceRate` | Teil der Sitzungen, die zurückkamen. |
| `totalPurchasers` | Unterschiedliche Käufer (wenn E-Commerce in GA4 konfiguriert ist). |
| `transactions` | Transaktionsanzahl (wenn E-Commerce konfiguriert ist). |
| `purchaseRevenue` | Kaufumsatz (USD). |
| `totalRevenue` | Gesamteinnahmen (USD). |

### Verwendung dieser Daten durch LLM Optimizer

LLM Optimizer verwendet diese Daten, um die Leistung auf Seitenebene, die Aufschlüsselungen der Quelle, die Länder- und Geräteaufteilungen sowie die Zeittrends des Business Impact Dashboards auszufüllen. Es werden keine Daten zum Trainieren von Modellen oder zum Freigeben außerhalb Ihres Mandanten verwendet.

### Was nicht aufgenommen wird

Keine Benutzerkennungen (Google-Client-ID, IP-Adresse, Geräte-ID), keine Zeilen auf Sitzungsebene, keine Zeilen auf Ereignisebene, keine benutzerdefinierten Dimensionen oder Metriken, die über die oben aufgeführten hinausgehen, und keine GA4-Zielgruppen- oder Segmentdefinitionen.

## Häufig gestellte Fragen {#faq}

F.: Ist die GA4-Integration während der Testphase verfügbar?

Nein. Die Integration ist nur für Kunden von Paid LLM Optimizer verfügbar.

F.: Muss ich ein Google Cloud-Projekt oder -Service-Konto erstellen?

Nein. Bei der Verbindung handelt es sich um eine standardmäßige Google-Anmeldung. LLM Optimizer verwaltet den Google OAuth-Client von Adobe aus. Sie benötigen lediglich ein Google-Konto mit Viewer-Zugriff auf die GA4-Eigenschaft.

F: Welche Daten werden erfasst oder gespeichert?

LLM Optimizer arbeitet mit aggregierten Metriken aus der von Ihrem Unternehmen autorisierten GA4-Daten-API und nicht mit Rohdaten auf Ereignisebene.

F: Wie werden Daten aufgenommen?

Ihr Unternehmen autorisiert LLM Optimizer, die GA4-Daten-API für die ausgewählte Eigenschaft abzufragen. An LLM-Quellen angepasste Referral Traffic werden über diese API genutzt.

F: Wie oft werden die Daten aktualisiert?

Daten werden aktualisiert **täglich** (voller Vortag nach Abschluss der Aufstockung).

F.: Werden in LLM Optimizer Rohdaten auf Ereignisebene gespeichert?

Nein. Nur **aggregierte** Metriken werden zum Verständnis von Traffic-Mustern und -Trends verwendet.

F.: Werden vollständige URLs, Abfragezeichenfolgen oder Seiteninhalte gespeichert?

Landingpage-Pfade werden als Teil des Standardberichts aufgenommen. Abfragezeichenfolgen und Seiteninhalte werden für diese Integration nicht aufgenommen.

F.: Werden Benutzerkennungen (Google Client-ID, IP-Adresse, Geräte-ID) gespeichert?

Nein.

F: Wie lange werden Daten aufbewahrt?

Derzeit werden Daten unbegrenzt gespeichert.

F.: Werden Daten während der Übertragung und im Ruhezustand verschlüsselt?

Derzeit werden Daten während der Übertragung verschlüsselt, nicht im Ruhezustand. Dies kann sich in zukünftigen Updates ändern.

F.: Werden historische Daten aufgestockt?

Ja. Nach einer erfolgreichen Einrichtung werden die letzten vier vollen Kalenderwochen und die aktuelle Kalenderwoche aufgestockt. Siehe auch [Nach dem Verbinden](#after-connect).

F.: Kann ich die Verbindung trennen oder den Zugriff widerrufen?

Ja — jederzeit. Sie können entweder die Verbindung zu einem anderen Konto oder einer anderen Eigenschaft von der GA4-Karte in LLM Optimizer wiederherstellen oder LLM Optimizer Zugriff vollständig von Ihrem Google-Konto unter [https://myaccount.google.com/permissions](https://myaccount.google.com/permissions) widerrufen. Durch Widerrufen des Zugriffs werden neue Daten-Pull-Vorgänge gestoppt. Zuvor aufgenommene aggregierte Daten verbleiben in LLM Optimizer.

F: Meine GA4-Eigenschaft ist verbunden, aber die Geschäftsauswirkungen sind leer - warum?

LLM Optimizer ruft nur Sitzungen ab, die GA4 selbst einer unterstützten LLM-Quelle/einem unterstützten Medium zuordnet (heute: ChatGPT, Gemini, Copilot, Claude, Perplexity). Wenn Ihre GA4-Eigenschaft noch keine Verweissitzungen aus einer dieser Quellen im angezeigten Zeitfenster aufgezeichnet hat, ist das Dashboard leer, auch wenn die Verbindung in Ordnung ist.
