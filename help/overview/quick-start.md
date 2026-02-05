---
title: Schnellstart
description: Erste Schritte mit Adobe LLM Optimizer - Integrieren Sie Ihre Marke, erschließen Sie Einblicke in die KI-Sichtbarkeit und erkunden Sie Dashboards, um die Suchleistung zu verbessern.
feature: Quickstart, Onboarding
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 1%

---


# Schnellstart

Um mit LLM Optimizer zu beginnen, müssen Sie den Onboarding-Prozess wie in den folgenden Schritten beschrieben abschließen. Nach Abschluss des Vorgangs haben Sie vollen Zugriff auf [LLM Optimizer-Dashboards](/help/dashboards/dashboards-overview.md) und andere Funktionen.

## Onboarding - Übersicht

Der Onboarding-Prozess beginnt mit dem Onboarding Ihrer Domain. Der Prozess unterscheidet sich, je nachdem, ob Sie AEM Cloud-Kunde sind oder nicht. Nach Abschluss des Vorgangs müssen Sie Informationen für die CDN-Protokollweiterleitung angeben und Kategorien, Themen und Eingabeaufforderungen schließlich anpassen. Im Folgenden werden die einzelnen Schritte des Prozesses zusammen mit hilfreichen Tipps beschrieben, wie Sie so bald wie möglich mit LLM Optimizer beginnen können.

### Zulassen des Zugriffs von Adobe LLM Optimizer auf öffentliche Seiten

Um präzise Inhalte und technische Empfehlungen bereitstellen zu können, benötigt Adobe LLM Optimizer Zugriff auf Ihre öffentlich zugänglichen Seiten. Dies wird durch eine sichere interne Crawler (Spacecat/1.0 User Agent) erreicht.

Konfigurationsanforderungen:

* Auf die Zulassungsliste setzen Fügen Sie den Spacecat/1.0-Benutzeragenten zur Datei &quot;&quot; in der Datei „robots.txt“ Ihrer Site oder zu den Regeln für die Verwaltung von Bot-Traffic hinzu
* Stellen Sie sicher, dass Seiten nicht auf Domain- oder CDN-Ebene blockiert werden. Blockierte Seiten können nicht indiziert werden, was bedeutet, dass Optimierungsaufgaben und -einblicke für sie nicht generiert werden können.

Wenn die Content-Sichtbarkeit im Dashboard unten angezeigt wird, stellen Sie sicher, dass die Crawler Zugriff auf Ihre Domains hat. Eingeschränkter Zugriff ist eine häufige Ursache für eine unvollständige Indizierung.

## Schritt 1: Onboarding Ihrer Domain

### Vor dem Kauf versuchen

Kunden von AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) haben die Möglichkeit, das Angebot &quot;**vor dem Kauf**&quot; zu verwenden. Es handelt sich um eine kostenlose Testversion von LLM Optimizer mit bis zu 200 kostenlosen Eingabeaufforderungen. Die Verwendung von mehr als 200 Eingabeaufforderungen erfordert eine separate Lizenzvereinbarung. Der Zugriff erfolgt „wie besehen“ und „wie verfügbar“ und kann von Adobe jederzeit geändert, eingeschränkt oder entfernt werden.

Es gibt einige Produktfunktionen, die in der kostenlosen Version nicht verfügbar sind:

* Testversion ist auf eine Domain beschränkt. Die von Ihnen angegebene Domain kann nach Abschluss der Einrichtung nicht mehr geändert werden.
* Unterstützung für die Bereitstellung von Optimierungen wird nicht verfügbar sein.

Im folgenden Abschnitt finden Sie Details zum Aktivieren der kostenlosen Testversion und zum Onboarding Ihrer Domain.

### AEM Cloud-Kunden

Wenn Sie AEM Cloud-Kunde sind, haben Sie die Möglichkeit, LLM Optimizer mithilfe der Produktankündigungskarte in [Experience Hub](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) auszuprobieren.

>[!NOTE]
>Neu hinzugefügte Eingabeaufforderungen werden erst dann im [Markenpräsenz-Dashboard angezeigt](/help/dashboards/brand-presence.md) wenn die Verarbeitung abgeschlossen ist. AEM Cloud-Kunden können die kostenlose Testversion von LLM Optimizer verwenden. Die Verwendung von mehr als 200 Eingabeaufforderungen erfordert eine separate Lizenzvereinbarung. Der Zugriff erfolgt „wie besehen“ und „wie verfügbar“ und kann von Adobe jederzeit geändert, eingeschränkt oder entfernt werden. Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie weitere Informationen benötigen.

![LLM Optimizer-Testversion](/help/overview/assets/llm-trial.png)

Nachdem Sie auf die Schaltfläche **LLM Optimizer ausprobieren** geklickt haben, werden Sie zu [https://llmo.now&rbrace; &#x200B;](https://llmo.now). Anschließend müssen Sie sich über IMS anmelden. Nach der Anmeldung starten Sie den Onboarding-Prozess, indem Sie eine Domain und den Markennamen angeben.

![LLM Optimizer-Domain](/help/overview/assets/domain.png)

>[!NOTE]
>Die bereitgestellte Domain wird von allen in Ihrem Unternehmen verwendet und kann nicht geändert werden.

Während der Onboarding-Phase wird eine kleine Reihe von Kategorien, Themen und Eingabeaufforderungen generiert. Markenpräsenz-Analysen zu diesen Eingabeaufforderungen stehen kurz nach dem Onboarding Ihrer Site zur Verfügung.

<!--![Brand Presence Analysis](/help/overview/assets/bp-analysis.png)-->

Darüber hinaus müssen Sie für die Traffic[Analyse auch &#x200B;](#step-4)CDN-Protokollweiterleitung“ konfigurieren. LLM Optimizer erfordert Markenpräsenz-Daten und Erkenntnisse von Agenten und Referral Traffic, um Chancen zu identifizieren und präskriptive Empfehlungen zu geben, um die KI-Sichtbarkeit zu verbessern.

### Nicht-AEM Cloud-Kunden

Sobald der Geschäftsvertrag abgeschlossen ist, erhalten Sie eine Einführung in die Domain, die Sie in LLM Optimizer integrieren möchten. Sobald dieses Onboarding abgeschlossen ist, können Sie sich über [https://llmo.now](https://llmo.now) bei LLM Optimizer anmelden.

### Schritt 2: Kategorien, Themen und Eingabeaufforderungen anpassen

Nach dem Onboarding der Site können Sie die Markenpräsenz-Analyse auf der Grundlage der kleinen Eingabeaufforderungen anzeigen, die während der Onboarding-Phase automatisch generiert wurden. Ab nun können Sie die Kategorien, Themen und Eingabeaufforderungen für Ihre Marke anpassen. Diese Konfiguration wird im Dashboard [Kundenkonfiguration“ &#x200B;](/help/dashboards/customer-configuration.md).

![Kundenkonfigurations-Dashboard](/help/overview/assets/prompt-creation.png)

Von diesem Dashboard aus haben Sie folgende Möglichkeiten:

* Fügen Sie **neue Kategorien** hinzu, die Ihren geschäftlichen Prioritäten entsprechen. Kategorien können breite Inhaltsbereiche sein, die für Ihre Domain relevant sind.
* Geben Sie **benutzerdefinierte Themen** oder Unterthemen ein, die verfolgt werden sollen. Bei Themen kann es sich um spezifische Themen handeln, die mit umfangreichen, nicht markenspezifischen Keywords in Verbindung gebracht werden, die mit Ihrer Domain verknüpft sind.
* Erstellen **Eingabeaufforderungen** um die Sichtbarkeit in bestimmten Abfragen zu überwachen. Eingabeaufforderungen sind Abfragen (mit oder ohne Marke), die eine allgemeine Sichtbarkeit bieten. Je nach den von Ihnen angegebenen Kategorien und Themen wird nur eine begrenzte Anzahl von Eingabeaufforderungen automatisch generiert.
* Definieren Sie **Aliase**, um sicherzustellen, dass alle Erwähnungen einer Marke erfasst und berücksichtigt werden.
* Definieren Sie **andere Aliase**, um andere Marken genau zu verfolgen.

>[!NOTE]
>Die von Ihnen angeforderten Eingabeaufforderungen sind nicht öffentlich verfügbar, da sie von den LLMs nicht offen gelegt werden.

>[!NOTE]
>
> Weitere Informationen zum Einrichten von Kategorien, Themen und Eingabeaufforderungen finden Sie auf der Seite [Best Practices zum Konfigurieren von Kategorien, Themen und &#x200B;](/help/overview/best-practices-topics-prompts.md)&quot;.

### Schritt 3: Markenpräsenz Insights

Nachdem Ihre Domain integriert wurde, erhalten Sie erste Einblicke in der Markenpräsenz-Ansicht, basierend auf den Eingabeaufforderungen, die beim Onboarding automatisch generiert wurden. Nachdem Sie Ihre eigenen Kategorien, Themen und Eingabeaufforderungen angepasst haben, erstellt LLM Optimizer automatisch einen Trigger der Markenpräsenz-Analyse anhand der von Ihnen angegebenen Eingabeaufforderungen, und die Ergebnisse sind innerhalb von 24 Stunden verfügbar.

### Schritt 4: Bereitstellen von Informationen für die CDN-Protokollweiterleitung {#step-4}

Um Agent-Traffic und Referral Traffic-Einblicke zu entsperren, müssen Sie Informationen für die CDN-Protokollweiterleitung angeben. Sie kann über das Dashboard [Kundenkonfiguration“ hinzugefügt werden](/help/dashboards/customer-configuration.md#cdn-configuration) indem Sie zur Registerkarte **CDN-Konfiguration** navigieren und auf **Integriertes CDN** klicken.

![Kundenkonfigurations-CDN](/help/overview/assets/cc-cdn.png)

Wenn zuvor kein CDN-Anbieter hinzugefügt wurde (wie oben beschrieben), werden Sie alternativ dazu aufgefordert, beim erstmaligen Zugriff auf die Dashboards Agent und Referral Traffic eine CDN-Protokollweiterleitung hinzuzufügen. Weitere Informationen finden Sie unter:

* [Agent-basierter Traffic](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Referenz-Traffic](/help/dashboards/referral-traffic.md#setup#setup)

### Schritt 5: Dashboards erkunden und Maßnahmen ergreifen

Nachdem Sie Informationen für die CDN-Protokollweiterleitung angegeben haben, können Sie:

* Zeigen Sie das [Markenpräsenz](/help/dashboards/brand-presence.md)-Dashboard an, zeigen Sie Ihre Sichtbarkeitsbewertung an und verfolgen Sie Ihre Leistung in Bezug auf andere Marken.
* Erkunden Sie die [Agent](/help/dashboards/agentic-traffic.md)- und [Referral Traffic](/help/dashboards/referral-traffic.md)-Dashboards, wenn CDN-Protokollweiterleitung konfiguriert wurde.
* Verwenden Sie [Opportunities](/help/dashboards/opportunities.md) um Inhalte und technische Verbesserungen zu identifizieren.
* Exportieren Sie Daten und arbeiten Sie mit Ihrem Team zusammen oder laden Sie Ihren Kollegen zur Verwendung des Produkts ein.

Um die Funktionen von LLM Optimizer vollständig zu verstehen, sollten Sie schließlich alle verfügbaren [Dashboards“ &#x200B;](/help/dashboards/dashboards-overview.md).
