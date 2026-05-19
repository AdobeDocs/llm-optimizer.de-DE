---
title: Best Practices für Kategorien, Themen, Prompts und andere Marken
description: Optimieren Sie die LLM-Erkenntnisse, indem Sie Kategorien, Themen, Prompts und andere Marken einschließlich der Wettbewerber konfigurieren, um eine maßgeschneiderte Markenüberwachung und eine strategische Inhaltsanalyse zu realisieren.
feature: Best Practices, Customer Configuration
autotag-review: '2026-05-15T17:36:13.598Z'
TQID: 'https://experienceleague.adobe.com/aZCxLQbfeDDtqD3hBGuD-JuCZoMuGiqQrs0gaqxt4-4'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: c898dfb2-0885-42fb-b2af-b2d756752646
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f8667931-f646-4dd3-af2a-b9d0cb8098ad
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1530
ht-degree: 100%

---

# Best Practices bei der Konfiguration nachzuverfolgender Kategorien, Themen, Prompts und anderer Marken

In diesem Abschnitt finden Sie Best Practices bei der Entscheidung, wie Sie Ihre Kategorien, Themen, Prompts und anderen Marken zur Nachverfolgung einrichten. Darüber hinaus enthält er Informationen zur Brachen-Prompt-Bibliothek, die Adobe mit umfangreichen Recherchen gemeinsam mit Branchenfachleuten entwickelt hat.

Dies ist ein entscheidender erster Schritt. Ihre Entscheidungen zu diesem Zeitpunkt bestimmen, wie Informationen für Ihren Unternehmenskontext zugeschnitten werden. Alle späteren Änderungen an Kategorien führen zum Zurücksetzen historischer Daten.

Im Dashboard [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md) legen Sie fest, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird. Weitere Informationen zur Verwendung des Dashboards finden Sie unter [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md).

![Fenster „Kundenkonfiguration“](/help/assets/best-practices/customer-configuration-best-practices.png)

Im Dashboard [!UICONTROL Kundenkonfiguration] können Sie Kategorien anpassen (z. B. Geschäftseinheiten oder Produktlinien), andere Marken verfolgen und Aliasse für Markenerwähnungen hinzufügen, um alle Varianten Ihrer Marke über alle Prompts hinweg zu erfassen. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Erkenntnisse auf Ihren Unternehmenskontext zuschneidet, sodass Sichtbarkeit, Traffic und Möglichkeiten genau analysiert werden können.

## Markenorientierte Oberfläche

Standardmäßig beginnen neue Nutzende in einer fokussierten, markenorientierten Oberfläche mit einer Onboarding-gesteuerten Einrichtung. In dieser neuen Benutzeroberfläche beginnt jede Organisation mit einer aktiven Marke und zusätzlichen vorgeschlagenen Marken, aus denen ausgewählt werden kann. Bestehende LLM Optimizer-Nutzende steigen schrittweise auf diese markenorientierte Oberfläche um.

Wenn Sie die markenorientierte Oberfläche nutzen, definieren Sie unter **Markenverwaltung**, wie Ihre Marke überwacht und analysiert wird.

![Markenverwaltung – App-Navigation (markenorientierte Oberfläche)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Markenverwaltung – Konfigurationsüberblick](/help/assets/brand-centric-experience/brands-management-configuration.png)

Um Themen und Prompts für eine bestimmte Marke einzurichten, verwenden Sie **Prompt-Verwaltung**.

![Prompt-Verwaltung](/help/assets/brand-centric-experience/prompts-management.png)

## Branchen-Prompt-Bibliothek

Um Ihnen den Einstieg in Prompts und Themen zu erleichtern, hat Adobe eine Branchen-Prompt-Bibliothek erstellt, die durch umfangreiche Recherchen mit Branchenfachleuten und Analysen des Verhaltens von über 6.000 Kundinnen und Kunden bei der KI-Suche entwickelt wurde. Diese Bibliothek identifiziert die relevantesten Themen und Prompts basierend auf branchenspezifischen Trends, validierten Geschäftszielen und echten Kundensuchmustern.

So verwenden Sie die Branchen-Prompt-Bibliothek:

1. Navigieren Sie zum Dashboard **Kundenkonfiguration**.
1. Wählen Sie **Prompt-Bibliothek herunterladen** aus, um die Bibliotheksdatei von LLM Optimizer herunterzuladen.
   ![Download der Branchen-Prompt-Bibliothek](/help/assets/best-practices/customer-configuration-prompts-library.png)
1. Prüfen Sie auf der entsprechenden Registerkarte die vorgeschlagenen **Themen** und **Prompts** für die Branche Ihrer Marke und wählen Sie die für Sie relevantesten Optionen aus.
1. Prüfen Sie die Spalte **Phase der Customer Journey**, um die Prompt-Optionen im gesamten Kundenzyklus anzuzeigen (z. B. von der Entdeckung über die Konversion bis zur Bindung). Prompts in frühen Phasen bzw. im oberen Teil des Trichters haben hohe Priorität. Erwägen Sie aber auch Optionen für spätere Phasen, um die Kundenbindung zu fördern, Kunden-Support zu ermöglichen usw.
1. Passen Sie Themen oder Prompts bestmöglich für Ihre Produktziele an, bevor Sie sie in Adobe LLM Optimizer hochladen (fügen Sie beispielsweise Ihren Marken-/Produktnamen hinzu oder verwenden Sie markenkonforme Terminologie). Prompts können manuell oder per Massen-Upload unter Verwendung der bereitgestellten *CSV*-Vorlage zu LLM Optimizer hinzugefügt werden.

>[!TIP]
>
> Verwenden Sie eine Kombination aus Domain-spezifischen Prompts, die von LLM Optimizer während der Ersteinrichtung empfohlen werden, und Prompts aus der Branchen-Prompt-Bibliothek, um Ihre Prompt-Strategie zu erstellen.

### Recherchefundament der Prompt-Bibliothek

Die Branchen-Prompt-Bibliothek wurde im Rahmen einer umfassenden Recherche-Initiative entwickelt, in der Folgendes kombiniert wurde:

* **Customer Intelligence:** Analyse des Verhaltens und der Präferenzen von über 6.000 Kundinnen und Kunden in KI-Suchen.
* **Branchenkompetenz:** Perspektiven von Fachleuten aus den Bereichen Automobil, Finanzdienstleistungen, Gesundheitswesen, Telekommunikation und Reisen.
* **Datengestützte Erkenntnisse:** Identifizierung von wirkungsvollen Themen und Abfragemustern, die die Kundeninteraktion und Konversion fördern.

Top-Themen, die von Kundschaft aus verschiedenen Branchen gesucht werden:

* **Automobil:** Fehlerbehebung bei Fahrzeugproblemen, Fahrzeugvergleiche und Finanzierung/Leasing.
* **Finanzdienstleistungen:** Recherchen zu Finanzprodukten.
* **Gesundheitswesen:** Recherchieren von Symptomen oder Gesundheitsproblemen, Vergleichen von Behandlungsoptionen, Verständnis von Laborergebnissen oder medizinischen Begriffen.
* **Telekommunikation:** Vergleichen von Tarifen, Vertragsbedingungen und Werbeaktionen, Prüfen von Service-Optionen in der Umgebung
* **Reisen:** Vorbereitung auf eine Reise, Recherche und Buchung von Reisen

Kunden-Trends in Bezug auf das Verhalten bei KI-Suchen und Prompts in LLM-Tools:

* Kundinnen und Kunden stellen bei der Verwendung von Tools für LLM-Suchen lieber Fragen, statt Keywords zu verwenden.
* Sie nutzen LLM-Such-Tools hauptsächlich für die Recherche und Entdeckung in der Frühphase der Customer Journey.
* Kundinnen und Kunden neigen dazu, in ihren Prompts einen bestimmten Marken- oder Produktnamen anzugeben.

## Best Practices für Kategorien

Mit Kategorien können Sie Ihre Inhalte in strategischen Geschäftseinheiten oder logischen Gruppierungen organisieren. Sie sind die „Schublade“, in die Ihre Inhalte gehören, und bilden die oberste Organisationsebene.

Bei der Entscheidung, wie Sie die Kategorien einrichten, müssen Sie berücksichtigen, was Ihre Ziele sind und wer mit Ihrem Reporting arbeiten muss.

>[!IMPORTANT]
>
> Stellen Sie sicher, dass Kategorien von Anfang an korrekt eingerichtet sind, da Änderungen an Kategorien historische Daten zurücksetzen. Das bedeutet, dass Sie bei jeder Änderung einer Kategorie alle historischen Daten aus der Zeit vor der Änderung verlieren.

Im Folgenden finden Sie einen Überblick über die möglichen Ansätze und in welchen Fällen Sie einen bestimmten Ansatz wählen sollten:

| Ansatz | Beschreibung | Vorteil |
|---------|----------|---------|
| Strategische Geschäftseinheit (SBU) | Verwenden Sie diesen Ansatz, wenn Ihr Unternehmen nach Gewinn- und Verlustrechnung (z. B. Verbrauchende, Unternehmen, Services) unterteilt ist. | Sie erhalten sauberes Reporting nach Geschäftsbereich und eine einfachere Aufteilung von Verantwortlichkeiten. |
| Website-Verzeichnis der obersten Ebene (URL_DIR) | Verwenden Sie diesen Ansatz, wenn die Datenarchitektur Ihrer Website die Eigentümerschaft widerspiegelt (/products/, /support/, /docs/, /news/). | Sie können stets nachvollziehen, wie Teams Inhalte veröffentlichen und verwalten. |
| Produkt-Kategorie (oder Service-Kategorie) | Verwenden Sie diese Option, wenn Sie aus einem Katalog verkaufen (SKUs/Services). | Sie erhalten Sortimentansichten, Lückenanalysen und Antworten auf die Frage, welche Kategorie Inhalte benötigt. |

Wie Sie Kategorien einrichten, hängt von einer Frage ab: **Wer muss mit dem Bericht arbeiten?**

* Wenn Sie in der *Geschäftsführung* arbeiten, wählen Sie den **SBU**-Ansatz.
* Wenn Sie *Web-/Inhalts-Eigentümerin/-Eigentümer* sind, wählen Sie den **URL_DIR**-Ansatz.
* Wenn Sie im *Merchandising-/Angebots-Management* arbeiten, wählen Sie den Ansatz **Produkt-/Service-Kategorie**.

![Hinzufügen von Kategorien in LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Wählen Sie einen Ansatz und halten Sie sich daran.
> * Pro Konto/Marke kann nur **ein** Kategoriemodell verwendet werden. Verwenden Sie **SBU** und **URL_DIR** nicht gleichzeitig.
<!--Can you mix Product/Service with these?-->

Zum Beispiel:

| Site-Typ | Kategorie | Beispiele für Thementaxonomien |
|---------|----------|---------|
| Großunternehmen mit mehreren Unternehmensbereichen | SBU | Kleine Anzahl von Absichten (Anleitungen, Fehlerbehebung, Vergleiche, Preisgestaltung, Richtlinien) |
| Site mit hohem Dokumentations-/Support-Bedarf | URL_DIR | Anleitungen, Fehlerbehebung, Referenz, Versionshinweise |
| E-Commerce-/Services-Katalog | Produkt/Service | Vergleiche, Bewertungen, Preisgestaltung/Verfügbarkeit, Anleitungen, Fehlerbehebung |

## Best Practices für Themen

Themen helfen Ihnen, die Benutzerabsichten zu verstehen, denn sie zeigen Ihnen, was die Benutzerinnen und Benutzer wollen. Sie ermöglichen es Ihnen, Prompts mit ähnlicher Benutzerabsicht zu gruppieren. Stellen Sie es sich so vor, dass relevante Prompts gebündelt werden.

>[!IMPORTANT]
>
>Themen sind in **allen** Kategorien universell, d. h. sie bleiben unabhängig von der Kategorie konsistent, der sie zugewiesen sind. Sie stellen Gruppen von Fragen oder Prompts dar, die eine gemeinsame Absicht verfolgen.

Bei der Entscheidung über Themen sollten Sie eine kurze, eindimensionale Liste erstellen (maximal 6–12 Themen). Beispiel:

* Produkte/Services
* Anleitungen (Einrichtung/Verwendung)
* Fehlerbehebung (Fehler/Probleme)
* Vergleiche (X vs. Y; „bestes … für …“)
* Rezensionen und Bewertungen
* Preisgestaltung und Verfügbarkeit
* Richtlinien und Gewährleistung
* Support-Kontakt
* Unternehmen/Neuigkeiten (wenn Sie dies wirklich benötigen)

![Hinzufügen von Themen in LLM Optimizer](/help/assets/best-practices/add-topic.png)

Beachten Sie beim Erstellen der Liste Folgendes:

* Können Bearbeitende das Thema anhand des Prompts innerhalb von 5 Sekunden verstehen? Falls nicht, benennen Sie ihn um/vereinfachen Sie ihn.
* Sind für die Fehlerbehebung für verschiedene Themen unterschiedliche Teams zuständig? Falls ja, haben Sie nützliche Themen ausgewählt.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Zusätzliche hilfreiche Hinweise:

* Nutzen Sie Ihre Kenntnisse über das Unternehmen oder die Site, um Themen zu definieren, die auf die strategischen Ziele Ihrer Marke abgestimmt sind.
* Bedenken Sie, wie Ihre Marke bei bestimmten Themen im Vergleich zu anderen Marken abschneidet.

>[!IMPORTANT]
>
> * Gestalten Sie die Themen absichtsbasiert, nicht organisatorisch.
> * Fügen Sie keine Kategorien/Filter für Marke/Nicht-Marke/Geografie hinzu, da Sie auf der Registerkarte **[!UICONTROL Marken]** gezielt danach filtern können.
> * Themen gelten über mehrere Kategorien hinweg. Es ist **nicht möglich**, für jede Kategorie individuelle Themen zu definieren.
> * Ein einzelner Prompt **kann** in mehreren Themen oder Kategorien vorhanden sein.

## Best Practices für Prompts

Anhand von Prompts werden die spezifischen Fragen oder Abfragen identifiziert, die von Kundinnen und Kunden gestellt werden. Dies kann Auswirkungen auf Ihre Geschäfte haben. Sie sind die eigentlichen Fragen oder Abfragen, die Benutzende in LLMs eingeben.

Prüfen und aktualisieren Sie Prompts regelmäßig, damit sichergestellt ist, dass sie mit den Kundenanforderungen und Geschäftszielen übereinstimmen.

Best Practices für Prompts:

* Gruppieren Sie ähnliche Prompts basierend auf den Fragen der Benutzenden.
* Konzentrieren Sie sich auf die Prompts, die für Ihre Kundinnen und Kunden am wichtigsten sind.
* Prüfen Sie, ob Ihre Marke gute Chancen hat, bei bestimmten Prompts erwähnt zu werden.

>[!TIP]
>
>* Sie können Tools wie Adobe LLM Optimizer und Google Search Console mit Regex-Filtern verwenden, um gängige Fragemuster zu identifizieren (z. B. „wie“, „was“, „wann“, „wo“) und herauszufinden, welche Prompts die Personen für den Besuch Ihrer Site verwenden.
>* Um herauszufinden, welche Prompts für Ihre Site/Marke relevant sind, können Sie Site-Suchdaten oder häufig gestellte Fragen in Ergebnisseiten von Suchmaschinen verwenden oder sogar LLM-Chatbots direkt fragen, welche Fragen Kundinnen und Kunden zu Ihrer Marke stellen könnten.

## Best Practices für die Nachverfolgung anderer Marken

Wenn Sie andere Marken nachverfolgen, können Sie die Sichtbarkeit und Erwähnungen in LLM-Antworten für Prompts und Themen überwachen, die für Ihr Unternehmen wichtig sind.

Auf der Registerkarte [!UICONTROL **Tracking von anderen**] können Sie andere Marken einschließlich Wettbewerbern hinzufügen, um deren Sichtbarkeit für bestimmte Prompts und Themen nachzuverfolgen.

Beim Tracking von anderen können Sie sehen, wie oft andere Marken neben Ihrer Marke in verschiedenen Regionen und Kategorien erwähnt werden, und deren Sichtbarkeit mit der Ihrer eigenen vergleichen.

>[!TIP]
>
>Überprüfen Sie regelmäßig die Erwähnungen und Zitierungen von Wettbewerbern oder anderen Marken, um Bereiche zu identifizieren, in denen sich Ihre Marke verbessern kann.

## Weitere Informationen

* Im [Dashboard „Kundenkonfiguration“](/help/dashboards/customer-configuration.md) konfigurieren Sie Kategorien, Themen, Prompts und Tracking von anderen.
* [Best Practices für LLM Optimizer](/help/tutorials/best-practices.md) beschreibt die Best Practices für die LLM-Optimierung.

