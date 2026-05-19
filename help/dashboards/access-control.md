---
title: Zugangssteuerung
description: Erfahren Sie, wie sich produktzugewiesene und Organisationsbenutzende in Adobe LLM Optimizer unterscheiden, was schreibgeschützten Benutzenden in der Benutzeroberfläche angezeigt wird und wie Admins Zugriff in Adobe Admin Console zuweisen.
feature: Customer Configuration
autotag-review: '2026-05-15T17:26:43.837Z'
TQID: 'https://experienceleague.adobe.com/hJpQQpuHBRMdKT5oKA9z0Y8H3d3p6To-n2hWKrXgZsQ'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: b704f6a0-b2fb-4df0-9177-9753751004f5
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 618
ht-degree: 100%

---


# Zugangssteuerung

Adobe LLM Optimizer unterstützt eine einfache Zugriffssteuerung basierend auf Benutzerpersonas. Diese Funktion steht nur **zahlenden Kundschaften** zur Verfügung und wird auf Anfrage aktiviert. Sie ist nicht für Kundschaften mit der Testversion verfügbar.

>[!IMPORTANT]
>
>Um Zugriff auf diese Funktion zu erhalten, sollten sich zahlende Kundschaften an ihren Adobe-Konto-Support wenden.

## Produktzugewiesene Benutzende {#product-assigned-users}

Wenn Sie dem Produkt zugewiesen sind, verfügen Sie zusätzlich zu den folgenden Berechtigungen über dieselben Funktionen wie standardmäßige Organisationsbenutzende:

* Schreibzugriff in [Kundenkonfiguration](/help/dashboards/customer-configuration.md) für Prompts, Kategorien, Themen und zugehörige Einstellungen.
* Bereitstellen von Optimierungen mit [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md) und Verwalten von Vorschlägen.
* Verwalten von Google Search Console-Konfigurationen.
* Verwalten und Optimize at Edge- und CDN-Konfigurationen.
* Durchführen von Onboarding einer neuen Site.

## Organisationsbenutzende {#organizational-users}

Organisationsbenutzende sind Standardbenutzende, die dem Produkt **nicht** zugewiesen sind. Wenn Sie eine Organisationsbenutzerin bzw. ein Organisationsbenutzer sind, verfügen Sie über **schreibgeschützten** Zugriff auf die [LLM Optimizer-Dashboards](/help/dashboards/dashboards-overview.md) und zugehörige Ansichten. Folgende Einschränkungen gelten.

### Kundenkonfiguration {#customer-configuration-restrictions}

* **Das Hochladen von Prompts** ist deaktiviert.
* Die Verwaltung und Bearbeitung von Prompts, Kategorien, Themen und Regionen ist deaktiviert.

  ![Kundenkonfigurationseinschränkungen für schreibgeschützte Benutzende](/help/dashboards/assets/access-control-customer-configuration.png)

### CDN-Konfiguration (Kundenkonfiguration) {#cdn-configuration-restrictions}

* **Das Onboarding von CDNs** ist deaktiviert (schreibgeschützte Benutzende können keinen CDN-Anbieter hinzufügen).
* **Das Löschen von CDNs** ist deaktiviert (schreibgeschützte Benutzende können eine vorhandene CDN-Konfiguration nicht entfernen).
* Die Schaltfläche **Senden** im Dialogfeld „CDN integrieren“ ist deaktiviert (schreibgeschützte Benutzende können die CDN-Einrichtung nicht abschließen).

  ![CDN-Konfigurationseinschränkungen für schreibgeschützte Benutzende](/help/dashboards/assets/access-control-cdn-configuration.png)

### Markenpräsenz – Datenerkenntnisse {#brand-presence-restrictions}

* Die Schaltfläche **Löschen** neben den Themen ist ausgeblendet (schreibgeschützte Benutzende können keine Themen aus dem Tracking entfernen).
* Die Schreibfläche **Löschen** neben den Prompts ist ausgeblendet (schreibgeschützte Benutzende können keine Prompts aus dem Tracking entfernen).

  ![Ausgeblendete Markenpräsenzaktionen für schreibgeschützte Benutzende](/help/dashboards/assets/access-control-brand-presence.png)

### Möglichkeiten im Zusammenhang mit Agent-basiertem Traffic (Fehlerseitenmöglichkeiten) {#agentic-opportunities}

Für Möglichkeiten wie beispielsweise 404-, 403- und 503-Fehlerseiten:

* **Die Bereitstellungsoptimierung** ist ausgeblendet.
* Ein informativer Warnhinweis erklärt, dass ein Bereitstellungszugriff erforderlich ist.

  ![Ausgeblendete Bereitstellungsoptimierung für Möglichkeiten im Zusammenhang mit Agent-basiertem Traffic](/help/dashboards/assets/access-control-agentic-deploy.png)

### Weitere Möglichkeitsseiten {#other-opportunities}

Das schreibgeschützte Verhalten gilt auch für Möglichkeitstypen wie:

* Inhaltsverzeichnis
* Zusammenfassung
* Lesbarkeit
* Prerender
* Überschriften
* Häufig gestellte Fragen
* Fehlende strukturierte Daten
* Generische Patch-Möglichkeit

Für diese Seiten:

* **Die Bereitstellungsoptimierung** ist ausgeblendet, wenn Benutzende keinen Bereitstellungszugriff haben.
* Ein Inline-Warnhinweis erklärt, dass ein Bereitstellungszugriff erforderlich ist. Die Meldung lautet in etwa: *Bereitstellungszugriff erforderlich – Sie haben keine Berechtigung, Optimierungen bereitzustellen oder Vorschläge zu verwalten. Wenden Sie sich an Ihre bzw. Ihren Admin, um Zugriff anzufordern.*
* Die fixierte untere Leiste mit den Bereitstellungsaktionen ist ausgeblendet.

  ![Inline-Warnhinweis, wenn Bereitstellungszugriff erforderlich ist](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Bereitstellungsaktionen für „Optimize at Edge“ für schreibgeschützte Benutzende ausgeblendet](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Prompt-Konfiguration für Google Search Console {#gsc-restrictions}

* Die Aktionen „Verwalten“ und „Verbinden“ sind deaktiviert oder ausgeblendet.
* Die zum Hinzufügen von Prompts verwendete Aktionsspalte ist ausgeblendet.

  ![Konfigurationseinschränkungen für Google Search Console](/help/dashboards/assets/access-control-gsc.png)

### Durchführen von Onboarding einer neuen Site {#onboarding-restrictions}

* Das Onboarding einer neuen Site ist für Benutzende ohne Zugriffssteuerung deaktiviert.

  ![Durchführen von Onboarding einer neuen Site deaktiviert](/help/dashboards/assets/access-control-onboarding.png)

## Zuweisen des Produkts an Benutzende oder eine Gruppe {#assign-product}

Eine bzw. ein **Systemadmin** Ihrer Organisation kann die [Adobe Admin Console](https://adminconsole.adobe.com/) verwenden, um Adobe LLM Optimizer einzelnen Benutzenden oder einer Gruppe zuzuweisen.

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit einem Konto an, das über administrative Rechte für Ihre Organisation verfügt.
1. Weisen Sie das Adobe LLM Optimizer-Produktprofil (oder die entsprechende Produktberechtigung Ihrer Organisation) einzelnen Benutzenden oder der Gruppe zu, die produktzugewiesene Funktionen erhalten sollen.

Ausführliche Anweisungen finden Sie unter [Verwalten von Produkten in der Admin Console](https://helpx.adobe.com/de/enterprise/using/manage-products.html) und [Verwalten von Benutzergruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html).

>[!NOTE]
>
>Die Bildschirmabläufe in der Adobe Admin Console können sich von Version zu Version ändern. Wenn die oben genannten Optionen nicht mit Ihrer Konsole übereinstimmen, verwenden Sie die produktinternen Hilfelinks in Adobe Admin Console oder wenden Sie sich an Ihr Adobe-Accountteam.
