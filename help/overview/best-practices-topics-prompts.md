---
title: Best Practices für Kategorien, Themen und Eingabeaufforderungen
description: Optimieren Sie LLM-Erkenntnisse, indem Sie Kategorien, Themen, Eingabeaufforderungen und Mitbewerber für ein maßgeschneidertes Markenmonitoring und eine strategische Inhaltsanalyse konfigurieren.
source-git-commit: 29e067086f9b6dd41c04b349c86ddc1c2baf8d2f
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---


# Best Practices für die Konfiguration von Kategorien, Themen, Eingabeaufforderungen und Mitbewerbern

In diesem Abschnitt werden Best Practices beschrieben, mit deren Hilfe Sie entscheiden können, wie Sie Kategorien, Themen, Eingabeaufforderungen und Mitbewerber einrichten möchten.

Dies ist ein entscheidender erster Schritt. Was Sie jetzt entscheiden, bestimmt, wie Informationen auf Ihren Geschäftskontext zugeschnitten werden. Alle Änderungen an Kategorien in der Zukunft setzen historische Daten zurück.

Im Dashboard [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md) legen Sie fest, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird. Siehe [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md) für Informationen zur Verwendung des Dashboards.

![Fenster „Kundenkonfiguration“](/help/assets/best-practices/customer-configuration-best-practices.png)

Im Dashboard [!UICONTROL Kundenkonfiguration] können Sie Kategorien anpassen (z. B. Geschäftseinheiten oder Produktlinien), Wettbewerber verfolgen und Aliase für Markenbezeichnungen hinzufügen, um alle Varianten Ihrer Marke über Eingabeaufforderungen hinweg zu erfassen. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Einblicke auf Ihren Geschäftskontext zuschneidet, was eine genaue Sichtbarkeit, Traffic und Opportunity-Analyse ermöglicht.

## Best Practices für Kategorien

Mit Kategorien können Sie Ihre Inhalte in strategischen Geschäftseinheiten oder logischen Gruppierungen organisieren. Sie sind der Bucket „Wohin er gehört“ und die oberste Organisationsebene für Ihre Inhalte.

Wenn Sie entscheiden, wie Kategorien eingerichtet werden, müssen Sie Ihre Ziele berücksichtigen und festlegen, wer Ihre Berichte bearbeiten muss.

>[!IMPORTANT]
>
> Stellen Sie sicher, dass Kategorien von Anfang an korrekt eingerichtet sind, da Änderungen an Kategorien historische Daten zurücksetzen. Das bedeutet, dass Sie bei einer Änderung dieser Daten historische Daten aus der Zeit vor der Änderung verlieren.

Im Folgenden finden Sie eine Übersicht über die möglichen Ansätze und den Zeitpunkt, zu dem Sie einen bestimmten Ansatz wählen:

| Ansatz | Beschreibung | Vorteil |
|---------|----------|---------|
| Strategische Geschäftseinheit (SGE) | Verwenden Sie diesen Ansatz, wenn Ihr Unternehmen nach Gewinn- und Verlustrechnung (z. B. Verbraucher, Unternehmen, Services) aufgeteilt ist. | Sie erhalten sauberes Reporting nach Geschäftsbereich und eine einfachere Rechenschaftspflicht. |
| Website-Verzeichnis der obersten Ebene (URL_DIR) | Verwenden Sie , wenn Ihre Website-Informationsarchitektur den Besitz (/products/, /support/, /docs/, /news/) widerspiegelt. | Sie können festlegen, wie Teams Inhalte veröffentlichen und verwalten. |
| Kategorie des Produkts (oder der Dienstleistung) | Verwenden Sie diese Option, wenn Sie einen Katalog verkaufen (SKUs/Services). | Sie erhalten Sortimentansichten, Lückenanalyse und Antworten dazu, welche Kategorie Inhalte benötigt. |

Wie Sie Kategorien einrichten, hängt von einer Frage ab: **Wer muss auf den Bericht reagieren?**

* Wenn Sie ein *Business Leader* sind, wählen Sie den **SBU**-Ansatz.
* Wenn Sie „Web */Inhalts-Inhaber“ sind* wählen Sie den **URL_DIR**-Ansatz.
* Wenn Sie ein *Merchandising-/Angebotsmanager* sind, wählen Sie den Ansatz **Produkt-/**).

>[!IMPORTANT]
>
> * Wählen Sie einen Ansatz und halten Sie sich daran.
> * Pro Konto/Marke kann nur **ein** Kategoriemodell verwendet werden. Mischen Sie **SBU** und **URL_DIR** nicht gleichzeitig.
>   <!--Can you mix Product/Service with these?-->

Zum Beispiel:

| Site-Typ | Kategorie | Beispiele für Topic Taxonomy |
|---------|----------|---------|
| Unternehmen mit mehreren Unternehmen | SBU | Kleine Absichten (Anleitung, Fehlerbehebung, Vergleich, Preise, Richtlinie) |
| Dokumentation/Support vor Ort | URL_DIR | Anleitung, Fehlerbehebung, Referenz, Versionshinweise |
| E-Commerce/Services-Katalog | Produkt/Service | Vergleich, Bewertungen, Preise/Verfügbarkeit, Anleitungen, Fehlerbehebung |

## Best Practices für Themen

Themen helfen Ihnen, die Benutzerinteressen zu verstehen, denn sie zeigen Ihnen, was die Benutzerinnen und Benutzer wollen. Sie ermöglichen es Ihnen, Eingabeaufforderungen mit ähnlicher Benutzerabsicht zu gruppieren. Stellen Sie es sich so vor, dass relevante Eingabeaufforderungen gebündelt werden.

>[!IMPORTANT]
>
>Themen sind in allen Kategorien **alle**, d. h. sie bleiben unabhängig von der Kategorie, der sie zugewiesen sind, konsistent. Sie stellen Gruppen von Fragen oder Eingabeaufforderungen dar, die einen gemeinsamen Zweck verfolgen.

Bei der Entscheidung über Themen sollten Sie eine kurze, flache Liste erstellen (maximal 6-12). Beispiel:

* Produkte/Services
* Anleitung (Einrichtung/Verwendung)
* Fehlerbehebung (Fehler/Probleme)
* Vergleich (X vs. Y; „am besten … für …„)
* Bewertungen
* Preise und Verfügbarkeit
* Richtlinie und Gewährleistung
* Support-Kontakt
* Firmen/Nachrichten (wenn Sie dies wirklich benötigen)

Beachten Sie beim Erstellen der Liste Folgendes:

* Kann ein Editor das Thema in 5 Sekunden nach der Eingabeaufforderung verstehen? Falls nicht, benennen/vereinfachen Sie um.
* Wird die Fehlerbehebung für verschiedene Themen einem anderen Team gehören? Wenn ja, haben Sie nützliche Themen ausgewählt.
  <!-- Last bullet point does not make sense. Clarification needed.-->

Einige zusätzliche hilfreiche Hinweise:

* Nutzen Sie Ihre geschäftlichen oder Site-Kenntnisse, um Themen zu definieren, die den strategischen Zielen Ihrer Marke entsprechen
* Berücksichtigen Sie bei bestimmten Themen den Vergleich Ihrer Marke mit Konkurrenten.

>[!IMPORTANT]
>
> * Behalten Sie Themen bei, die absichtsbasiert, nicht organisatorisch sind.
> * Fügen Sie keine Kategorien/Filter für Marke/Nicht-Marke/Geografie hinzu, da Sie auf der Registerkarte **[!UICONTROL Marken]** gezielt danach filtern können.
> * Themen sind über mehrere Kategorien verteilt. Sie können **verschiedene Themen** Kategorie haben.
> * Eine Eingabeaufforderung kann in mehreren Themen oder Kategorien vorhanden sein.

## Best Practices für Eingabeaufforderungen

Anhand von Eingabeaufforderungen werden die spezifischen Fragen oder Abfragen identifiziert, die Kunden stellen und die sich auf Ihr Unternehmen auswirken können. Dabei handelt es sich um die eigentlichen Fragen oder Abfragen, die Benutzende in LLMs eingeben.

Stellen Sie sicher, dass Eingabeaufforderungen regelmäßig überprüft und aktualisiert werden, um sicherzustellen, dass sie mit den Kundenanforderungen und Geschäftszielen übereinstimmen.

>[!TIP]
>
>* Sie können Tools wie die Adobe LLM Optimizer- und Google-Suchkonsole mit Regex-Filtern verwenden, um gängige Fragestrukturen zu identifizieren (z. B. „wie“, „was“, „wann“, „wo„) und herauszufinden, welche Aufforderungen die Personen für den Besuch Ihrer Site verwenden.
>* Um herauszufinden, welche Eingabeaufforderungen für Ihre Site/Marke relevant sind, können Sie Suchdaten auf der Site verwenden, FAQs auf Suchmaschinenergebnisseiten verwenden oder sogar LLM-Chatbots direkt fragen, welche Fragen Kunden zu Ihrer Marke stellen könnten.

## Best Practices für Mitbewerber

Mitbewerber ermöglichen es Ihnen, die Sichtbarkeit und Erwähnungen in den LLM-Antworten auf für Ihr Unternehmen wichtige Eingabeaufforderungen und Themen zu überwachen.

Auf [!UICONTROL **Registerkarte**] Wettbewerbs-Tracking“ können Sie Konkurrenten hinzufügen und ihre Sichtbarkeit für bestimmte Eingabeaufforderungen und Themen verfolgen.

Mit dem Wettbewerb-Tracking können Sie sehen, wie oft Wettbewerber neben Ihrer Marke in verschiedenen Regionen und Kategorien erwähnt werden, und ihre Sichtbarkeit mit Ihrer eigenen vergleichen.

>[!TIP]
>
>Überprüfen Sie regelmäßig die Erwähnungen und Zitate von Mitbewerbern, um Bereiche zu identifizieren, in denen sich Ihre Marke verbessern kann.

## Weitere Informationen

* [Dashboard für Kundenkonfigurationen](/help/dashboards/customer-configuration.md) konfigurieren Sie Ihre Kategorien, Themen, Eingabeaufforderungen und Konkurrenten.
* [Best Practices für LLM Optimizer](/help/tutorials/best-practices.md) beschreibt Best Practices für die LLM-Optimierung

