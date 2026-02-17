---
title: Schnellstart
description: 'Starten Sie mit Adobe LLM Optimizer: Integrieren Sie Ihre Marke, gewinnen Sie KI-Erkenntnisse zur Sichtbarkeit und erkunden Sie Dashboards zur Verbesserung der Suchleistung.'
feature: Quickstart, Onboarding
source-git-commit: ae37ef578f279eae6ea51fd8aed5c6b91c8e1088
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 93%

---


# Schnellstart

Um mit LLM Optimizer zu beginnen, müssen Sie den Onboarding-Prozess wie in den folgenden Schritten beschrieben abschließen. Nach Abschluss des Verfahrens haben Sie vollen Zugriff auf [LLM Optimizer-Dashboards](/help/dashboards/dashboards-overview.md) und andere Funktionen.

## Onboarding – Überblick

Das Onboarding-Verfahren beginnt mit dem Onboarding Ihrer Domain. Das Verfahren unterscheidet sich abhängig davon, ob Sie Kundin oder Kunde von AEM Cloud sind oder nicht. Nach Abschluss des Verfahrens müssen Sie Informationen für die CDN-Protokollweiterleitung angeben und schließlich Kategorien, Themen und Prompts anpassen. Im Folgenden werden die einzelnen Schritte des Verfahrens zusammen mit hilfreichen Tipps beschrieben, wie Sie so bald wie möglich mit LLM Optimizer beginnen können.

### Erlauben des Zugriffs auf öffentliche Seiten durch Adobe LLM Optimizer

Um präzise Inhalte und technische Empfehlungen bereitstellen zu können, benötigt Adobe LLM Optimizer Zugriff auf Ihre öffentlich zugänglichen Seiten. Dies wird durch einen sicheren internen Crawler (Benutzer-Agent „Spacecat/1.0“) erreicht.

Konfigurationsanforderungen:

* Fügen Sie der Zulassungsliste in der Datei robots.txt Ihrer Site oder den Regeln für die Verwaltung von Bot-Traffic den Benutzer-Agent „Spacecat/1.0“ hinzu.
* Stellen Sie sicher, dass Seiten nicht auf Domain- oder CDN-Ebene blockiert werden. Blockierte Seiten können nicht indiziert werden. Daher können keine Optimierungsaufgaben und -erkenntnisse für sie generiert werden.

Wenn im Dashboard eine geringe Inhaltssichtbarkeit angezeigt wird, stellen Sie sicher, dass der Crawler Zugriff auf Ihre Domains hat. Eingeschränkter Zugriff ist eine häufige Ursache für eine unvollständige Indizierung.

## Schritt 1: Onboarding Ihrer Domain

### Vor dem Kauf testen

Kunden von AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) haben die Möglichkeit, das Angebot &quot;**vor dem Kauf**&quot; zu verwenden. Dies ist eine kostenlose Testversion von LLM Optimizer mit bis zu 200 kostenlosen Prompts. Wenn Sie mehr als 200 Prompts nutzen möchten, benötigen Sie einen separaten Lizenzvertrag. Der Zugriff wird „wie besehen“ und „wie verfügbar“ bereitgestellt und kann von Adobe jederzeit geändert, eingeschränkt oder entfernt werden.

Einige Produktfunktionen sind in der kostenlosen Version nicht verfügbar:

* Die Testversion ist auf eine Domain beschränkt. Sie können die angegebene Domain nach Abschluss der Einrichtung nicht mehr ändern.
* Die Möglichkeit, Optimierungen bereitzustellen, ist im Early Access-Modus verfügbar. Weitere Informationen finden Sie unter [Optimieren bei Edge - Häufig gestellte &#x200B;](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge#frequently-asked-questions).

Im folgenden Abschnitt finden Sie Details zum Aktivieren der kostenlosen Testversion und zum Onboarding Ihrer Domain.

### Kundinnen und Kunden von AEM Cloud

Wenn Sie AEM Cloud-Kundin oder -Kunde sind, haben Sie die Möglichkeit, LLM Optimizer über die Produktankündigungskarte in [Experience Hub](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) auszuprobieren.

>[!NOTE]
>Neu hinzugefügte Prompts werden im [Dashboard „Markenpräsenz“](/help/dashboards/brand-presence.md) erst angezeigt, wenn die Verarbeitung abgeschlossen ist. AEM Cloud-Kundinnen und -Kunden können die kostenlose Testversion von LLM Optimizer verwenden. Wenn Sie mehr als 200 Prompts nutzen möchten, benötigen Sie einen separaten Lizenzvertrag. Der Zugriff wird „wie besehen“ und „wie verfügbar“ bereitgestellt und kann von Adobe jederzeit geändert, eingeschränkt oder entfernt werden. Bitte wenden Sie sich für weitere Informationen an Ihre Kundenbetreuung.

![LLM Optimizer-Testversion](/help/overview/assets/llm-trial.png)

Wenn Sie auf die Schaltfläche **LLM Optimizer ausprobieren** klicken, werden Sie zu [https://llmo.now](https://llmo.now) weitergeleitet. Anschließend müssen Sie sich über IMS anmelden. Nach der Anmeldung starten Sie das Onboarding-Verfahren, indem Sie eine Domain und den Markennamen angeben.

![LLM Optimizer-Domain](/help/overview/assets/domain.png)

>[!NOTE]
>Die von Ihnen angegebene Domain wird von allen Mitarbeitenden Ihres Unternehmens verwendet und kann nicht geändert werden.

Während der Onboarding-Phase wird eine kleine Gruppe von Kategorien, Themen und Prompts generiert. Markenpräsenz-Analysen zu diesen Prompts stehen kurz nach dem Onboarding Ihrer Site zur Verfügung.

<!--![Brand Presence Analysis](/help/overview/assets/bp-analysis.png)-->

Außerdem müssen Sie die [CDN-Protokollweiterleitung](#step-4) für die Traffic-Analyse konfigurieren. LLM Optimizer benötigt Markenpräsenz-Daten und Erkenntnisse von Agent-basiertem und Referral Traffic, um Möglichkeiten zu identifizieren und präskriptive Empfehlungen zur Verbesserung der KI-Sichtbarkeit zu geben.

### Nicht-AEM Cloud-Kundinnen und -Kunden

Sobald der Unternehmensvertrag abgeschlossen ist, erfolgt Ihr Onboarding mit der Domain, die Sie in LLM Optimizer integrieren möchten. Sobald dieses Onboarding abgeschlossen ist, können Sie sich über [https://llmo.now](https://llmo.now) bei LLM Optimizer anmelden.

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

Um Erkenntnisse zu Agent-basiertem Traffic und Referral Traffic zu gewinnen, müssen Sie Informationen für die CDN-Protokollweiterleitung angeben. Diese können Sie im [Dashboard „Kundenkonfiguration“](/help/dashboards/customer-configuration.md#cdn-configuration) hinzufügen, indem Sie zur Registerkarte **CDN-Konfiguration** navigieren und auf **CDN integrieren** klicken.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Wenn zuvor kein CDN-Anbieter hinzugefügt wurde (wie oben beschrieben), werden Sie alternativ dazu aufgefordert, beim erstmaligen Zugriff auf die Dashboards für Agent-basierten und Referral Traffic eine CDN-Protokollweiterleitung hinzuzufügen. Weitere Informationen finden Sie unter:

* [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Referral Traffic](/help/dashboards/referral-traffic.md#setup#setup)

## Schritt 5: Erkunden der Dashboards und Einleiten von Maßnahmen

Nachdem Sie Informationen für die CDN-Protokollweiterleitung angegeben haben, können Sie:

* Das Dashboard [Markenpräsenz](/help/dashboards/brand-presence.md) anzeigen, Ihre Sichtbarkeitsbewertung anzeigen und Ihre Leistung im Vergleich mit anderen Marken nachverfolgen.
* Die Dashboards [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md) und [Referral Traffic](/help/dashboards/referral-traffic.md) erkunden, wenn die CDN-Protokollweiterleitung konfiguriert wurde.
* [Möglichkeiten](/help/dashboards/opportunities.md) nutzen, um Verbesserungen für Inhalte und technische Aspekte zu identifizieren.
* Daten exportieren und mit Ihrem Team zusammenarbeiten oder Ihre Kolleginnen und Kollegen zur Verwendung des Produkts einladen.

Um die Funktionen von LLM Optimizer vollständig zu verstehen, sollten Sie sich alle verfügbaren [Dashboards](/help/dashboards/dashboards-overview.md) genau ansehen.
