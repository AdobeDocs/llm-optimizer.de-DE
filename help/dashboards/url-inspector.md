---
title: URL-Überwachung
description: Erfahren Sie, wie Sie mit der URL-Überwachung die Leistung bestimmter Seiten Ihrer Domain bei der KI-Suche analysieren können.
feature: URL Inspector
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: ht
source-wordcount: '687'
ht-degree: 100%

---


# URL-Überwachung

Mit der URL-Überwachung können Sie die Leistung bestimmter Seiten Ihrer Domain bei der KI-Suche analysieren. Sie kombiniert Sichtbarkeit, Agent-basierten Traffic und Referenzdaten auf URL-Ebene, um Ihnen einen granularen Überblick darüber zu geben, welche URLs zitiert werden und wie oft sie in Antworten enthalten sind.

![URL-Überwachung](/help/dashboards/assets/url-insp.png)

## Filter

Oben auf der Seite können Sie Filter anwenden, um Ihre Ansicht zu verfeinern. Die ausgewählten Filter wirken sich auf **alle** Abschnitte im Dashboard aus. Sie können Folgendes anpassen:

* **Datumsbereich** – Wählen Sie den Zeitrahmen für die angezeigten Daten aus. Zum Beispiel die letzten 4 Wochen. Sie können den Zeitraum auch mit der Option **Benutzerdefinierte Wochen** anpassen.
* **Kategorie** – Filtern Sie die angezeigten Ergebnisse nach Kategorien.
* **Plattform** – Wählen Sie die zu analysierende KI-Engine aus.
* **Seiteninhaltstyp** – Filtern Sie nach Inhaltstyp.
* **Region** – Filtern Sie die Ergebnisse nach Geografie. Bei Veröffentlichung werden noch nicht alle Regionen verfügbar sein.

Nachdem Sie den gewünschten Filter ausgewählt haben, klicken Sie auf **Filter anwenden**, um Ihre Auswahl auf das Dashboard anzuwenden.

## Überblickmetriken

Die URL-Überwachung bietet mehrere Überblickmetriken, mit denen Sie schnell die Leistung Ihrer Seiten bei der KI-Suchen beurteilen können. Die folgenden Metriken sind verfügbar:

* **Eindeutige Prompts mit eigenen Zitierungen** – Die Gesamtzahl eindeutiger KI-Prompts mit eigenen Zitierungen.
* **Eindeutige Prompts insgesamt** – Die Gesamtzahl eindeutiger KI-Prompts.
* **Eindeutige zitierte URLs** – Die Anzahl der zitierten eindeutigen eigenen URLs.
* **Gesamtzahl der Zitierungen** – Die Gesamtzahl der Zitierungen einer eigenen URL in KI-generierten Antworten.
* **Gesamtzahl der Agent-basierten Treffer** – Zeigt die Gesamtanzahl der Treffer durch AI Agents auf Ihrer Site an.
* **Referenztreffer von LLMs** – Die Gesamtzahl der Treffer, die aus KI-generierten Antworten auf Ihre URL geleitet wurden.

Für jede Überblickmetrik zeigen Trend-Indikatoren an, wie sich die Werte im Zeitverlauf verglichen mit dem vorherigen Zeitraum ändern.

## Ihre zitierten URLs

Die Ansicht „Ihre zitierten URLs“ listet alle URLs Ihrer Marke auf, die in KI-generierten Antworten zitiert wurden, einschließlich unterstützender Metriken. Beide Tabellen verfügen über ein Suchfeld für den schnellen Zugriff auf Themen. Mit der Schaltfläche **Spalten konfigurieren** können Sie anpassen, welche Metriken angezeigt werden. Außerdem können Sie mit der Option **Exportieren** die CSV-Datei der Tabelle herunterladen und die Erkenntnisse mit Ihrem Team teilen oder die Tabellen in das Reporting für Führungskräfte aufnehmen.

![Zitierte URLs](/help/dashboards/assets/cited-urls.png)

Die folgenden Metriken sind verfügbar:

* **URL** – Die analysierte URL.
* **Anzahl der Zitierungen** – Die Anzahl der Zitierungen der URL in KI-generierten Antworten.
* **Zitiert in Prompts** – Die Anzahl der eindeutigen KI-Prompts, in denen die URL zitiert wurde.
* **Kategorien** – Die Produktkategorien oder Themen, denen diese URL zugeordnet ist.
* **Regionen** – Die geografischen Regionen, in denen die URL zitiert wurde.
* **Agent-basierte Treffer** – Die Gesamtzahl der Treffer von AI Agents für die URL.
* **Referenztreffer** – Die Anzahl der Treffer, die von KI-generierten Antworten an die URLs weitergeleitet wurden.

## Um Zitierungen konkurrierende Trend-URLs

Die Ansicht mit den Trend-URLs, die um Zitierungen konkurrieren, zeigt externe URLs an, die derzeit in markenrelevanten Antworten zitiert werden, um zu messen, wer in Ihrem Feld die Zitierungen gewinnt. Die Datentabelle verfügt über ein Suchfeld für den schnellen Zugriff auf bestimmte URLs. Außerdem können Sie mit der Option **Exportieren** die CSV-Datei der Tabelle herunterladen und die Erkenntnisse mit Ihrem Team teilen oder die Tabellen in das Reporting für Führungskräfte aufnehmen.

![Um Zitierungen konkurrierende Trend-URLs](/help/dashboards/assets/trend-url.png)

Die folgenden Metriken sind verfügbar:

* **URL** – Die analysierte URL.
* **Inhaltstyp** – Der Typ des Inhalts (eigener, Social Media, verdienter, anderer).
* **Anzahl der Zitierungen** – Die Anzahl der Zitierungen der URL in KI-generierten Antworten.
* **Zitiert in Prompts** – Die Anzahl der eindeutigen KI-Prompts, in denen die URL zitiert wurde.
* **Kategorien** – Die Produktkategorien oder Themen, denen diese URL zugeordnet ist.
* **Regionen** – Die geografischen Regionen, in denen die URL zitiert wurde.

### Fenster „Details“

Sowohl in der Ansicht für zitierte URLs als auch in der Ansicht für Trend-URLs wird am Ende jeder Zeile die Schaltfläche **Details** angezeigt. Durch Klicken auf die Schaltfläche wird ein separates Fenster mit weiteren Details angezeigt. Das Fenster „Details“ zeigt an, wie oft die URL zitiert wird, <!--the sentiment of AI responses where it is mentioned,--> die Themen und Prompts, in denen sie enthalten ist, sowie Trends beim Agent-basierten und Referral Traffic im Zeitverlauf (für eigene URLs).

![Fenster „Details“](/help/dashboards/assets/details-url.png)
