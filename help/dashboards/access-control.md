---
title: Zugangssteuerung
description: Erfahren Sie, wie sich produktzugewiesene und organisatorische Benutzende in Adobe LLM Optimizer unterscheiden, was schreibgeschützte Benutzende in der Benutzeroberfläche sehen und wie Admins Zugriff in Adobe Admin Console zuweisen.
feature: Customer Configuration
source-git-commit: 3b792a8ca7efd4b6d6764d2e83f9b0c103a56558
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 4%

---


# Zugangssteuerung

Adobe LLM Optimizer unterstützt eine einfache Zugriffssteuerung basierend auf Benutzerrollen. Diese Funktion steht nur **zahlenden Kunden zur** und wird auf Anfrage aktiviert. Es ist nicht für Testkunden verfügbar.

>[!IMPORTANT]
>
>Um Zugriff auf diese Funktion zu erhalten, sollten sich zahlende Kunden an ihren Adobe Account Manager wenden.

## Produktzugewiesene Benutzer {#product-assigned-users}

Wenn Sie dem Produkt zugewiesen sind, verfügen Sie zusätzlich zu den folgenden Berechtigungen über dieselben Funktionen wie ein standardmäßiger organisatorischer Benutzer:

* Schreibzugriff in [Kundenkonfiguration](/help/dashboards/customer-configuration.md) für Eingabeaufforderungen, Kategorien, Themen und zugehörige Einstellungen.
* Optimierungen [Optimieren bei Edge](/help/dashboards/optimize-at-edge/overview.md) bereitstellen und Vorschläge verwalten.
* Google Search Console-Konfigurationen verwalten.
* Verwalten und Optimieren von Edge- und CDN-Konfigurationen.
* Onboarding einer neuen Site.

## Organisatorische Benutzer {#organizational-users}

Organisationsbenutzer sind Standardbenutzer, die dem Produkt **nicht** zugewiesen sind. Wenn Sie ein Benutzer in einem Unternehmen sind, haben Sie **schreibgeschützten** Zugriff auf die [LLM Optimizer-Dashboards](/help/dashboards/dashboards-overview.md) und die zugehörigen Ansichten. Folgende Einschränkungen gelten.

### Kundenkonfiguration {#customer-configuration-restrictions}

* **Upload-Eingabeaufforderungen** ist deaktiviert.
* Die Verwaltung und Bearbeitung von Eingabeaufforderungen, Kategorien, Themen und Regionen ist deaktiviert.

  ![Kundenkonfigurationsbeschränkungen für schreibgeschützte Benutzer](/help/dashboards/assets/access-control-customer-configuration.png)

### CDN-Konfiguration (Kundenkonfiguration) {#cdn-configuration-restrictions}

* **Integriertes CDN** ist deaktiviert (schreibgeschützte Benutzer können keinen CDN-Anbieter hinzufügen).
* **CDN löschen** ist deaktiviert (Benutzer, die nur lesen können, können eine vorhandene CDN-Konfiguration nicht entfernen).
* Die Schaltfläche **Senden** im integrierten CDN-Dialogfeld ist deaktiviert (schreibgeschützte Benutzer können die CDN-Einrichtung nicht abschließen).

  ![CDN-Konfigurationsbeschränkungen für schreibgeschützte Benutzer](/help/dashboards/assets/access-control-cdn-configuration.png)

### Markenpräsenz - Dateneinblicke {#brand-presence-restrictions}

* Die **Löschen**-Schaltflächen neben den Themen sind ausgeblendet (schreibgeschützte Benutzer können keine Themen aus dem Tracking entfernen).
* Die **Löschen** neben den Eingabeaufforderungen sind ausgeblendet (schreibgeschützte Benutzer können Eingabeaufforderungen aus dem Tracking nicht entfernen).

  ![Markenpräsenz-Aktionen für schreibgeschützte Benutzer ausgeblendet](/help/dashboards/assets/access-control-brand-presence.png)

### Agent-Traffic-Gelegenheiten (Chancen auf Fehlerseite) {#agentic-opportunities}

Für Opportunities wie 404-, 403- und 503-Fehlerseiten:

* **Optimierung bereitstellen** ist ausgeblendet.
* Ein informativer Warnhinweis erklärt, dass Bereitstellungszugriff erforderlich ist.

  ![Optimierungsbereitstellung in den Traffic-Möglichkeiten von Agenten ausgeblendet](/help/dashboards/assets/access-control-agentic-deploy.png)

### Andere Opportunity-Seiten {#other-opportunities}

Schreibgeschütztes Verhalten gilt auch für Opportunity-Typen, z. B.:

* Inhaltsverzeichnis
* Zusammenfassung
* Lesbarkeit
* Prerender
* Überschriften
* Häufig gestellte Fragen
* Fehlende strukturierte Daten
* Allgemeine Patch-Opportunity

Für diese Seiten:

* **Bereitstellungsoptimierung** wird ausgeblendet, wenn der Benutzer keinen Bereitstellungszugriff hat.
* Ein Inline-Warnhinweis erklärt, dass Bereitstellungszugriff erforderlich ist. Die Meldung ähnelt: *Bereitstellungszugriff erforderlich - Sie sind nicht berechtigt, Optimierungen bereitzustellen oder Vorschläge zu verwalten. Wenden Sie sich an Ihren Administrator, um Zugriff anzufordern.*
* Die fixierbare untere Leiste mit Bereitstellungsaktionen ist ausgeblendet.

  ![Inline-Warnhinweis, wenn der Bereitstellungszugriff erforderlich ist](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Optimieren Sie die bei Edge ausgeblendeten Bereitstellungsaktionen für schreibgeschützte Benutzer](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Konfiguration der Google Search Console-Eingabeaufforderung {#gsc-restrictions}

* Aktionen „Verwalten“ und „Verbinden“ sind deaktiviert oder ausgeblendet.
* Die Spalte Aktionen , die zum Hinzufügen von Eingabeaufforderungen verwendet wird, ist ausgeblendet.

  ![Konfigurationseinschränkungen der Google-Suchkonsole](/help/dashboards/assets/access-control-gsc.png)

### Onboarding einer neuen Site {#onboarding-restrictions}

* Das Onboarding einer neuen Site ist für Benutzende ohne Zugriffssteuerung deaktiviert.

  ![Onboarding einer neuen Site deaktiviert](/help/dashboards/assets/access-control-onboarding.png)

## Produkt einem Benutzer oder einer Gruppe zuweisen {#assign-product}

Ein **Systemadministrator** für Ihr Unternehmen kann die [Adobe Admin Console](https://adminconsole.adobe.com/) verwenden, um Adobe LLM Optimizer einem Benutzer oder einer Gruppe zuzuweisen.

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit einem Konto an, das über Administratorrechte für Ihr Unternehmen verfügt.
1. Weisen Sie das Adobe LLM Optimizer-Produktprofil (oder die entsprechende Produktberechtigung Ihres Unternehmens) dem Benutzer oder der Gruppe zu, der bzw. die produktzugewiesene Funktionen erhalten soll.

Ausführliche Anweisungen finden Sie unter [Verwalten von Produkten in der ](https://helpx.adobe.com/enterprise/using/manage-products.html) und [Verwalten von Benutzergruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html).

>[!NOTE]
>
>Die Fluss-Bildschirme in der Adobe Admin Console können sich zwischen den Versionen ändern. Wenn die oben genannten Optionen nicht mit Ihrer Konsole übereinstimmen, verwenden Sie die produktinternen Hilfelinks in Adobe Admin Console oder wenden Sie sich an Ihr Adobe-Accountteam.
