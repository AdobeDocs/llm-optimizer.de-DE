---
title: Schnellstart
description: Erfahren Sie, wie Sie Ihren Markennamen und Ihre Domain integrieren, Ihre Testversion von Experience Hub oder Experience Cloud aktivieren und die Einrichtung für Adobe LLM Optimizer abschließen.
feature: Quickstart, Onboarding
source-git-commit: dcbeb1c61dd9dcefd83908f65f8303d36c0fb78e
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 47%

---


# Schnellstart

Um mit LLM Optimizer zu beginnen, müssen Sie den Onboarding-Prozess abschließen. Nach dem Onboarding können Sie Kategorien, Themen und Eingabeaufforderungen anpassen und die Protokollweiterleitung konfigurieren, um genauere Einblicke und vollen Zugriff auf die [LLM Optimizer-Dashboards](/help/dashboards/dashboards-overview.md) und andere Funktionen zu erhalten.

## Onboarding – Überblick

Der Onboarding-Prozess beginnt mit dem Onboarding Ihrer Domain und Ihres Markennamens. Jeder Teil der Onboarding-Journey wird unten beschrieben, zusammen mit hilfreichen Tipps, wie Sie so bald wie möglich mit LLM Optimizer beginnen können.

### Erlauben des Zugriffs auf öffentliche Seiten durch Adobe LLM Optimizer

Um präzise Inhalte und technische Empfehlungen bereitstellen zu können, benötigt Adobe LLM Optimizer Zugriff auf Ihre öffentlich zugänglichen Seiten. Dies wird durch einen sicheren internen Crawler (Benutzer-Agent „Spacecat/1.0“) erreicht.

Konfigurationsanforderungen:

* Fügen Sie den Spacecat/1.0-Benutzeragenten zur Datei &quot;&quot; in der Datei „robots.txt“ Ihrer Site oder zu den Regeln für die Verwaltung von Bot-Traffic hinzu.
* Stellen Sie sicher, dass Seiten weder auf Domain- noch auf CDN-Ebene blockiert werden. Blockierte Seiten können nicht indiziert werden. Daher können keine Optimierungsaufgaben und -erkenntnisse für sie generiert werden.

Wenn im Dashboard eine geringe Inhaltssichtbarkeit angezeigt wird, stellen Sie sicher, dass der Crawler Zugriff auf Ihre Domains hat. Eingeschränkter Zugriff ist eine häufige Ursache für eine unvollständige Indizierung.

## Schritt 1: Integrieren Sie Ihren Markennamen und Ihre Domain {#step-1-onboard-your-domain}

Um mit LLM Optimizer zu beginnen, aktivieren Sie zunächst Ihre Testversion (falls zutreffend) und integrieren Sie Ihren Markennamen und Ihre Domain.

### Testversion aktivieren

Der Aktivierungsfluss unterscheidet sich je nach Adobe-Produkt.

#### AEM Cloud-Kunden

Um Ihre Testversion zu aktivieren, haben Sie als AEM Cloud-Kunde folgende Möglichkeiten:

* Navigieren Sie zu [Experience Hub](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) und aktivieren Sie LLM Optimizer mithilfe der Karte „Produktankündigung“. Nachdem Sie &quot;**LLM Optimizer ausprobieren** ausgewählt haben, werden Sie zu [https://llmo.now} ](https://llmo.now). Melden Sie sich über IMS an und geben Sie dann eine Domain und einen Markennamen ein, um den Onboarding-Prozess zu starten.
* Oder gehen Sie direkt zu [https://llmo.now](https://llmo.now) und melden Sie sich an.

![LLM Optimizer-Testversion](/help/overview/assets/llm-trial.png)

#### Adobe Analytics-Kunden

Wenn Sie Adobe Analytics-Kunde sind, wird auf der Experience Cloud-Startseite ein Banner angezeigt.

![Experience Cloud-Startseite mit dem Banner &quot;Adobe LLM Optimizer-Testversion starten“](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Sie können Ihre Testversion auf eine der folgenden Arten aktivieren:

* Wählen **im Banner die Option** Adobe LLM Optimizer-Testversion starten“ aus.
* Gehen Sie direkt zu [https://llmo.now](https://llmo.now) und melden Sie sich an.

Sobald die Testversion aktiv ist, fahren Sie mit dem Onboarding Ihres Markennamens und Ihrer Domain fort.

>[!NOTE]
>
> * **Kostenlose Testversion:** Kunden von AEM Cloud und Adobe Analytics können die kostenlose Testversion von LLM Optimizer verwenden.
> * **Kunden, die die Testversion am oder nach dem 1. April 2026 aktivieren** können bis zu 100 Eingabeaufforderungen und eine Domain verwenden und Optimierungen für bis zu 10 URLs für einen einzelnen Opportunity-Typ bereitstellen.
> * **Kunden, die die Testversion vor dem 1. April 2026 aktiviert**, haben unter ihren bestehenden Bedingungen weiterhin Zugriff auf bis zu 200 Eingabeaufforderungen.
>
>Die Verwendung über die enthaltenen Beschränkungen hinaus erfordert eine separate Lizenzvereinbarung. Der Zugriff erfolgt „wie besehen“ und „wie verfügbar“ und kann jederzeit geändert, eingeschränkt oder entfernt werden. Weitere Informationen erhalten Sie von Ihrem Kundenbetreuer.

#### Integrieren Sie Ihren Markennamen und Ihre Domain

Integrieren Sie Ihren Markennamen und Ihre Domain, um mit der Verwendung von LLM Optimizer zu beginnen.

1. Geben Sie Ihren Markennamen und die zugehörige Domain ein.

   * Dies sollte die Hauptdomäne sein, in der Sie Inhalte analysieren und optimieren möchten.

1. Vollständiges Onboarding.

   * Nach der Übermittlung beginnt LLM Optimizer mit der Analyse Ihrer Domain und der Erstellung von Einblicken.

![LLM Optimizer-Domain](/help/overview/assets/domain.png)

>[!NOTE]
>Neu hinzugefügte Prompts werden im [Dashboard „Markenpräsenz“](/help/dashboards/brand-presence.md) erst angezeigt, wenn die Verarbeitung abgeschlossen ist.

>[!NOTE]
>Die von Ihnen angegebene Domain wird von allen Mitarbeitenden Ihres Unternehmens verwendet und kann nicht geändert werden.

Während der Onboarding-Phase wird eine kleine Gruppe von Kategorien, Themen und Prompts generiert. Markenpräsenz-Analysen zu diesen Prompts stehen kurz nach dem Onboarding Ihrer Site zur Verfügung.

Die Möglichkeit, Optimierungen im Randbereich bereitzustellen, ist ebenfalls verfügbar. Weitere Informationen finden Sie unter [Optimieren bei Edge - Häufig gestellte Fragen](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Konfigurieren Sie außerdem [CDN-Protokollweiterleitung](#step-4) für die Traffic-Analyse. LLM Optimizer erfordert Markenpräsenz-Daten und Erkenntnisse von Agent und Referral Traffic, um Chancen zu identifizieren und präskriptive Empfehlungen zur Steigerung der KI-Sichtbarkeit zu geben.

### Nicht-AEM Cloud-Kunden

Nachdem Ihr Unternehmen den Geschäftsvertrag abgeschlossen hat, werden Sie mit der von Ihrem Unternehmen ausgewählten Domain in LLM Optimizer aufgenommen. Wenn das Onboarding abgeschlossen ist, melden Sie sich unter [https://llmo.now](https://llmo.now) an.

## Schritt 2: Anpassen der Kategorien, Themen und Prompts

Nach dem Onboarding der Site können Sie die Markenpräsenz-Analyse auf Basis der kleinen Gruppe von Prompts anzeigen, die während der Onboarding-Phase automatisch generiert wurden. Ab diesem Zeitpunkt können Sie die Kategorien, Themen und Prompts für Ihre Marke anpassen. Diese Konfiguration wird im [Dashboard „Kundenkonfiguration“](/help/dashboards/customer-configuration.md) erstellt.

![Dashboard „Kundenkonfiguration“](/help/overview/assets/prompt-creation.png)

In diesem Dashboard haben Sie folgende Möglichkeiten:

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

## Schritt 3: Markenpräsenz-Erkenntnisse

Nachdem Ihre Domain integriert wurde, erhalten Sie in der Ansicht „Markenpräsenz“ erste Erkenntnisse basierend auf den beim Onboarding automatisch generierten Prompts Sobald Sie Ihre eigenen Kategorien, Themen und Prompts angepasst haben, löst LLM Optimizer automatisch die Markenpräsenz-Analyse anhand der von Ihnen angegebenen Prompts aus. Die Ergebnisse sind innerhalb von 24 Stunden verfügbar.

## Schritt 4: Bereitstellen von Informationen für die CDN-Protokollweiterleitung {#step-4}

Um Agenten-Traffic und Referral Traffic-Einblicke zu entsperren, fügen Sie CDN-Protokollweiterleitungsinformationen vom [Kundenkonfigurations-Dashboard) ](/help/dashboards/customer-configuration.md#cdn-configuration). Öffnen Sie die **CDN-Konfiguration** und wählen Sie **Integriertes CDN** aus.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Wenn zuvor kein CDN-Anbieter hinzugefügt wurde (wie oben beschrieben), werden Sie alternativ dazu aufgefordert, beim erstmaligen Zugriff auf die Dashboards für Agent-basierten und Referral Traffic eine CDN-Protokollweiterleitung hinzuzufügen. Weitere Informationen finden Sie unter:

* [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Referral Traffic](/help/dashboards/referral-traffic.md#setup)

>[!NOTE]
>Weitere Informationen zur Protokollweiterleitung bei Verwendung eines vom Kunden verwalteten CDN (BYOCDN) finden Sie unter [Übersicht über die Protokollweiterleitung von BYOCDN](/help/overview/log-forwarding/log-forwarding-overview.md)

## Schritt 5: Erkunden der Dashboards und Einleiten von Maßnahmen

Nachdem Sie Informationen für die CDN-Protokollweiterleitung angegeben haben, können Sie:

* Das Dashboard [Markenpräsenz](/help/dashboards/brand-presence.md) anzeigen, Ihre Sichtbarkeitsbewertung anzeigen und Ihre Leistung im Vergleich mit anderen Marken nachverfolgen.
* Erkunden Sie die [Agent](/help/dashboards/agentic-traffic.md)- und [Referral Traffic](/help/dashboards/referral-traffic.md)-Dashboards, wenn die CDN-Protokollweiterleitung konfiguriert wurde.
* [Möglichkeiten](/help/dashboards/opportunities.md) nutzen, um Verbesserungen für Inhalte und technische Aspekte zu identifizieren.
* Daten exportieren und mit Ihrem Team zusammenarbeiten oder Ihre Kolleginnen und Kollegen zur Verwendung des Produkts einladen.

Um die Funktionen von LLM Optimizer vollständig zu verstehen, sollten Sie sich alle verfügbaren [Dashboards](/help/dashboards/dashboards-overview.md) genau ansehen.
