---
title: Schnellstart
description: Erfahren Sie, wie Sie das Onboarding für Ihren Markennamen und Ihre Domain durchführen, Ihre Testversion von Experience Hub oder Experience Cloud aktivieren und die Einrichtung für Adobe LLM Optimizer abschließen.
feature: Quickstart, Onboarding
autotag-review: '2026-05-15T17:56:15.005Z'
TQID: 'https://experienceleague.adobe.com/ShjpvskyOoHqz88gorfhqbIdP5SWT9FJ9SfmjBgEm8E'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: b70f186a-2ef9-43ce-b452-25fa1d91bcda
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1472
ht-degree: 96%

---


# Schnellstart

Um mit LLM Optimizer zu beginnen, schließen Sie den Onboarding-Prozess ab. Passen Sie dann Kategorien, Themen und Prompts an, konfigurieren Sie die CDN-Protokollweiterleitung und öffnen Sie die [Dashboards](/help/dashboards/dashboards-overview.md), um umfassendere Erkenntnisse zu erhalten.

<!--Where steps differ by layout, use **Customer Configuration (classic experience)** or **Brands Management** / **Prompts Management**, whichever matches your current interface.-->

## Markenorientierte Oberfläche {#brand-centric-experience}

Standardmäßig beginnen neue Nutzende in einer fokussierten, markenorientierten Oberfläche mit einer Onboarding-gesteuerten Einrichtung. In dieser neuen Benutzeroberfläche beginnt jede Organisation mit einer aktiven Marke und zusätzlichen vorgeschlagenen Marken, aus denen ausgewählt werden kann. Bestehende LLM Optimizer-Nutzende steigen schrittweise auf diese markenorientierte Oberfläche um.

## Onboarding – Überblick

Der Onboarding-Prozess beginnt mit dem Onboarding Ihrer Domain und Ihres Markennamens. Im Folgenden werden die einzelnen Schritte des Onboarding-Prozesses beschrieben zusammen mit hilfreichen Tipps dazu, wie Sie so schnell wie möglich mit der Arbeit mit LLM Optimizer beginnen können.

### Erlauben des Zugriffs auf öffentliche Seiten durch Adobe LLM Optimizer

Um präzise Inhalte und technische Empfehlungen bereitstellen zu können, benötigt Adobe LLM Optimizer Zugriff auf Ihre öffentlich zugänglichen Seiten. Dies wird durch einen sicheren internen Crawler (Benutzer-Agent „Spacecat/1.0“) erreicht.

Konfigurationsanforderungen:

* Fügen Sie der Zulassungsliste in der Datei „robots.txt“ Ihrer Site oder den Regeln für die Verwaltung von Bot-Traffic den Benutzer-Agent „Spacecat/1.0“ hinzu.
* Stellen Sie sicher, dass Seiten nicht auf Domain- oder CDN-Ebene blockiert werden. Blockierte Seiten können nicht indiziert werden. Daher können keine Optimierungsaufgaben und -erkenntnisse für sie generiert werden.

Wenn im Dashboard eine geringe Inhaltssichtbarkeit angezeigt wird, stellen Sie sicher, dass der Crawler Zugriff auf Ihre Domains hat. Eingeschränkter Zugriff ist eine häufige Ursache für eine unvollständige Indizierung.

## Schritt 1: Durchführen des Onboardings für Ihren Markennamen und Ihre Domain {#step-1-onboard-your-domain}

Um mit LLM Optimizer zu beginnen, aktivieren Sie zunächst Ihre Testversion (falls zutreffend) und führen Sie das Onboarding für Ihren Markennamen und Ihre Domain durch.

### Aktivieren der Testversion

Der Aktivierungsfluss unterscheidet sich je nach Adobe-Produkt.

#### AEM Cloud-Kundschaften

Um Ihre Testversion zu aktivieren, haben Sie als AEM Cloud-Kundschaft folgende Möglichkeiten:

* Navigieren Sie zu [Experience Hub](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) und aktivieren Sie LLM Optimizer mithilfe der Karte „Produktankündigung“. Nachdem Sie **LLM Optimizer ausprobieren** ausgewählt haben, werden Sie zu [https://llmo.now](https://llmo.now) weitergeleitet. Melden Sie sich über IMS an und geben Sie dann eine Domain und einen Markennamen ein, um den Onboarding-Prozess zu starten.
* Oder navigieren Sie direkt zu [https://llmo.now](https://llmo.now) und melden Sie sich an.

![LLM Optimizer-Testversion](/help/overview/assets/llm-trial.png)

#### Adobe Analytics und Adobe Customer Journey Analytics

Kunden von Adobe Analytics und Adobe Customer Journey Analytics sehen ein Banner auf der Startseite von Experience Cloud.

![Experience Cloud-Startseite mit dem Banner „Adobe LLM Optimizer-Testversion starten“](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Sie können Ihre Testversion auf eine der folgenden Arten aktivieren:

* Wählen Sie im Banner **Adobe LLM Optimizer-Testversion starten** aus.
* Navigieren Sie direkt zu [https://llmo.now](https://llmo.now) und melden Sie sich an.

Sobald die Testversion aktiv ist, fahren Sie mit dem Onboarding Ihres Markennamens und Ihrer Domain fort.

>[!NOTE]
>
> * **Kostenlose Testversion:** Kunden von AEM Cloud und Adobe Analytics/Customer Journey Analytics können die kostenlose Testversion von LLM Optimizer verwenden.
> * **Kundschaften, die die Testversion am oder nach dem 1. April 2026 aktivieren**, können bis zu 100 Prompts und eine Domain verwenden und Optimierungen für bis zu 10 URLs für einen einzelnen Möglichkeitstyp bereitstellen.
> * **Kundschaften, die die Testversion vor dem 1. April 2026 aktivierten**, haben gemäß der bestehenden Bedingungen weiterhin Zugriff auf bis zu 200 Prompts.
>
>Die Verwendung über die enthaltenen Limits hinaus erfordert eine separate Lizenzvereinbarung. Der Zugriff wird „wie besehen“ und „wie verfügbar“ bereitgestellt und kann von Adobe jederzeit geändert, eingeschränkt oder entfernt werden. Weitere Informationen erhalten Sie von Ihrem Konto-Support.

#### Durchführen des Onboardings für Ihren Markennamen und Ihre Domain

Führen Sie das Onboarding für Ihren Markennamen und Ihre Domain durch, um mit der Verwendung von LLM Optimizer zu beginnen.

1. Geben Sie Ihren Markennamen und die zugehörige Domain ein.

   * Dies sollte die Haupt-Domain sein, in der Sie Inhalte analysieren und optimieren möchten.

1. Schließen Sie das Onboarding ab.

   * Nach der Übermittlung beginnt LLM Optimizer mit der Analyse Ihrer Domain und der Generierung von Erkenntnissen.

![LLM Optimizer-Domain](/help/overview/assets/domain.png)

>[!NOTE]
>Neu hinzugefügte Prompts werden im [Dashboard „Markenpräsenz“](/help/dashboards/brand-presence.md) erst angezeigt, wenn die Verarbeitung abgeschlossen ist.

>[!NOTE]
>Die von Ihnen angegebene Domain wird von allen Mitarbeitenden Ihres Unternehmens verwendet und kann nicht geändert werden.

Während der Onboarding-Phase wird eine kleine Gruppe von Kategorien, Themen und Prompts generiert. Markenpräsenz-Analysen zu diesen Prompts stehen kurz nach dem Onboarding Ihrer Site zur Verfügung.

Die Möglichkeit, Optimierungen auf Edge-Architektur bereitzustellen, ist ebenfalls verfügbar. Weitere Informationen finden Sie unter [Optimieren auf Edge-Architektur – Häufig gestellte Fragen](https://experienceleague.adobe.com/de/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Konfigurieren Sie außerdem die [CDN-Protokollweiterleitung](#step-4) für die Traffic-Analyse. LLM Optimizer benötigt Markenpräsenzdaten und Erkenntnisse von Agent-basiertem und Referral Traffic, um Möglichkeiten zu identifizieren und präskriptive Empfehlungen zur Verbesserung der KI-Sichtbarkeit zu geben.

### Nicht-AEM Cloud-Kundschaften

Nachdem Ihr Unternehmen der Geschäftsvereinbarung zugestimmt hat, wird das Onboarding in LLM Optimizer mit der von Ihrer Organisation ausgewählten Domain durchgeführt. Wenn das Onboarding abgeschlossen ist, melden Sie sich unter [https://llmo.now](https://llmo.now) an.

## Schritt 2: Anpassen der Kategorien, Themen und Prompts {#step-2-customize-categories-topics-and-prompts}

Nach dem Onboarding der Site können Sie die Markenpräsenz-Analyse auf Basis der kleinen Gruppe von Prompts anzeigen, die während der Onboarding-Phase automatisch generiert wurden. Ab diesem Zeitpunkt können Sie Kategorien, Themen und Prompts für Ihre Marke anpassen.

### Kundenkonfiguration (klassische Navigation)

Wenn Sie die klassische Navigation (nicht die markenorientierte Oberfläche) verwenden, können Sie Kategorien, Themen und Prompts für Ihre Marke über das Dashboard [Kundenkonfiguration](/help/dashboards/customer-configuration.md) anpassen.

![Dashboard „Kundenkonfiguration“](/help/overview/assets/prompt-creation.png)

Im Dashboard „Kundenkonfiguration“ haben Sie folgende Möglichkeiten:

* Hinzufügen **neuer Kategorien**, die zu Ihren geschäftlichen Prioritäten passen. Kategorien können breite Inhaltsbereiche sein, die für Ihre Domain relevant sind.
* Eingeben **benutzerdefinierter Themen** oder Unterthemen, die nachverfolgt werden sollen. Bei Themen kann es sich um spezifische Bereiche mit Bezug zu umfangreichen, nicht markenspezifischen Keywords handeln, die mit Ihrer Domain verknüpft sind.
* Erstellen **eigener Prompts**, um die Sichtbarkeit in bestimmten Abfragen zu überwachen. Prompts sind Abfragen (mit oder ohne Bezug zur Marke), die eine allgemeine Sichtbarkeit bieten. Nur eine begrenzte Anzahl von Prompts wird automatisch basierend auf den von Ihnen angegebenen Kategorien und Themen generiert.
* Definieren von **Aliassen** für Erwähnungen, um sicherzustellen, dass alle Erwähnungen einer Marke erfasst und berücksichtigt werden.
* Definieren **anderer Aliasse**, um andere Marken genau nachzuverfolgen.

>[!NOTE]
>Der genaue Wortlaut der von Ihnen genutzten Prompts für LLMs ist nicht öffentlich verfügbar, da die Prompts von den LLMs nicht offengelegt werden.

>[!NOTE]
>
> Weitere Informationen zum Einrichten von Kategorien, Themen und Prompts finden Sie auf der Seite [Best Practices bei der Konfiguration von Kategorien, Themen und Prompts](/help/overview/best-practices-topics-prompts.md).

### Kategorien, Themen und Prompts der markenorientierten Oberfläche

Für Kundschaften, die die markenorientierten Oberfläche verwenden, können Sie Kategorien, Themen und Prompts wie folgt hinzufügen:

* **Kategorien**: Navigieren Sie zu **Markenverwaltung** und klicken Sie auf **Kategorien**. Kategorien werden auf globaler Ebene definiert und gelten für alle Marken in der Markenverwaltung.

  ![Markenverwaltung mit Kategorien in der Navigation](/help/assets/brand-centric-experience/llmo-app-shell.png)

* **Themen und Prompts**: Navigieren Sie zu **Prompt-Verwaltung**, um Themen und Prompts zu erstellen, einschließlich Prompts für eine bestimmte Marke.

  ![Prompt-Verwaltung](/help/assets/brand-centric-experience/prompts-management.png)

## Schritt 3: Markenpräsenz-Erkenntnisse

Nachdem Ihre Domain integriert wurde, erhalten Sie in der Ansicht „Markenpräsenz“ erste Erkenntnisse basierend auf den beim Onboarding automatisch generierten Prompts Sobald Sie Ihre eigenen Kategorien, Themen und Prompts angepasst haben, löst LLM Optimizer automatisch die Markenpräsenz-Analyse anhand der von Ihnen angegebenen Prompts aus. Die Ergebnisse sind innerhalb von 24 Stunden verfügbar.

>[!NOTE]
>
> Für Kundschaften, die die markenorientierten Oberfläche verwenden, können Sie zu **Markenpräsenz** navigieren und mithilfe des Dropdown-Menüs „Marke“ eine Marke auswählen, für die die Markenpräsenz angezeigt werden soll. Mit diesem Erlebnis können Sie auch die Markensichtbarkeit auf einer Ebene für **alle Marken** anzeigen.

## Schritt 4: Bereitstellen von Informationen für die CDN-Protokollweiterleitung {#step-4}

Um Erkenntnisse zu Agent-basiertem Traffic und Referral Traffic zu erhalten, registrieren Sie die CDN-Protokollweiterleitung, damit LLM Optimizer Ihre Zugriffsprotokolle lesen kann.

### Kundenkonfiguration (klassische Navigation)

Wenn Sie die klassische Navigation verwenden, können Sie Informationen zur CDN-Protokollweiterleitung über das Dashboard [Kundenkonfiguration](/help/dashboards/customer-configuration.md#cdn-configuration) hinzufügen. Öffnen Sie die Registerkarte **CDN-Konfiguration** und wählen Sie **CDN integrieren** aus.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Wenn zuvor kein CDN-Anbieter hinzugefügt wurde (wie oben beschrieben), werden Sie alternativ dazu aufgefordert, beim erstmaligen Zugriff auf die Dashboards für Agent-basierten und Referral Traffic eine CDN-Protokollweiterleitung hinzuzufügen. Weitere Informationen finden Sie unter:

* [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Referral Traffic](/help/dashboards/referral-traffic.md#setup)

>[!NOTE]
>Einzelheiten zur Protokollweiterleitung bei Verwendung eines kundenseitig verwalteten CDN (BYOCDN) finden Sie unter [BYOCDN-Protokollweiterleitung – Überblick](/help/overview/log-forwarding/log-forwarding-overview.md)

### CDN-Protokollweiterleitung für markenorientierte Oberfläche

Für Kundschaften, die die markenorientierten Oberfläche verwenden, können Sie Informationen zur CDN-Protokollweiterleitung von **Markenverwaltung** wie folgt hinzufügen: Öffnen Sie **Markenverwaltung** und klicken Sie auf das Label **CDN**.

![Markenverwaltung – CDN-Protokollweiterleitung](/help/assets/brand-centric-experience/brands-management-cdn.png)

## Schritt 5: Erkunden der Dashboards und Einleiten von Maßnahmen

Nachdem Sie Informationen für die CDN-Protokollweiterleitung angegeben haben, können Sie:

* Das Dashboard [Markenpräsenz](/help/dashboards/brand-presence.md) anzeigen, Ihre Sichtbarkeitsbewertung anzeigen und Ihre Leistung im Vergleich mit anderen Marken nachverfolgen.
* Zeigen Sie die Dashboards [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md) und [Referral Traffic](/help/dashboards/referral-traffic.md) an, nachdem die CDN-Protokollweiterleitung konfiguriert wurde.
* [Möglichkeiten](/help/dashboards/opportunities-overview.md) nutzen, um Verbesserungen für Inhalte und technische Aspekte zu identifizieren.
* Daten exportieren und mit Ihrem Team zusammenarbeiten oder Ihre Kolleginnen und Kollegen zur Verwendung des Produkts einladen.

>[!NOTE]
> Rufen Sie in der markenorientierten Oberfläche die gewünschte Ansicht über den Navigationsbereich auf der linken Seite auf.

Um die Funktionen von LLM Optimizer vollständig zu verstehen, sollten Sie sich alle verfügbaren [Dashboards](/help/dashboards/dashboards-overview.md) genau ansehen.
