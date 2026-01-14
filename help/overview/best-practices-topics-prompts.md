---
title: Best Practices für Kategorien, Themen, Eingabeaufforderungen und andere
description: Optimieren Sie die LLM-Erkenntnisse, indem Sie Kategorien, Themen, Eingabeaufforderungen und andere Marken konfigurieren, einschließlich Mitbewerbern für ein maßgeschneidertes Markenmonitoring und eine strategische Inhaltsanalyse.
feature: Best Practices, Customer Configuration
source-git-commit: a4dd9b1aece2936fb95a2e831ec8b41946bc5f46
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 0%

---


# Best Practices zum Konfigurieren von Kategorien, Themen, Eingabeaufforderungen und anderen zu verfolgenden Themen

In diesem Abschnitt werden Best Practices beschrieben, mit deren Hilfe Sie entscheiden können, wie Sie Ihre Kategorien, Themen, Eingabeaufforderungen und andere Nachverfolgungsoptionen einrichten möchten. Darüber hinaus enthält es Informationen zur Industry Prompt Library, die Adobe mit umfangreichen Recherchen von Branchenexperten entwickelt hat.

Dies ist ein entscheidender erster Schritt. Was Sie jetzt entscheiden, bestimmt, wie Informationen auf Ihren Geschäftskontext zugeschnitten werden. Alle Änderungen an Kategorien in der Zukunft setzen historische Daten zurück.

Im Dashboard [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md) legen Sie fest, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird. Siehe [[!UICONTROL Kundenkonfiguration]](/help/dashboards/customer-configuration.md) für Informationen zur Verwendung des Dashboards.

![Fenster „Kundenkonfiguration“](/help/assets/best-practices/customer-configuration-best-practices.png)

Im Dashboard [!UICONTROL Kundenkonfiguration] können Sie Kategorien anpassen (z. B. Geschäftseinheiten oder Produktlinien), andere Marken verfolgen und Markenbezeichnungsaliase hinzufügen, um alle Varianten Ihrer Marke über Eingabeaufforderungen hinweg zu erfassen. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Einblicke auf Ihren Geschäftskontext zuschneidet, was eine genaue Sichtbarkeit, Traffic und Opportunity-Analyse ermöglicht.

## Bibliothek mit Eingabeaufforderungen für die Branche

Um Ihnen den Einstieg in Eingabeaufforderungen und Themen zu erleichtern, hat Adobe eine Industry Prompt Library erstellt, die durch umfangreiche Forschungsarbeiten mit Branchenexperten und Analysen des KI-Suchverhaltens von über 6.000 Kunden entwickelt wurde. Diese Bibliothek identifiziert die relevantesten Themen und Eingabeaufforderungen basierend auf branchenspezifischen Trends, validierten Geschäftszielen und realen Kundensuchmustern.

So verwenden Sie die Bibliothek mit Eingabeaufforderungen für die Branche:

1. Laden Sie die Bibliotheksdatei für die Eingabeaufforderung aus LLM Optimizer herunter, indem Sie zum Dashboard **Kundenkonfiguration** navigieren.
2. Überprüfen Sie die **Themen** und **Aufforderungen** für die Branche Ihrer Marke auf der entsprechenden Registerkarte und wählen Sie die relevantesten Optionen aus.
3. Lesen Sie **Spalte „Kunden-Journey-**&quot;, um die Eingabeaufforderungsoptionen im gesamten Kundenlebenszyklus anzuzeigen (z. B. Erkennung zur Konvertierung in die Aufbewahrung). Frühzeitige funnel-Eingabeaufforderungen haben hohe Priorität, erwägen aber auch Optionen für das spätere Stadium, um die Kundenbindung zu fördern, den Kunden-Support zu aktivieren usw.
4. Ändern Sie Themen oder Eingabeaufforderungen nach Bedarf, um Ihre Produktziele bestmöglich zu unterstützen, bevor Sie sie auf Adobe LLM Optimizer hochladen (fügen Sie beispielsweise Ihren Marken-/Produktnamen hinzu oder verwenden Sie markeninterne Terminologie). Eingabeaufforderungen können manuell zu LLMO hinzugefügt oder mithilfe der bereitgestellten *.csv*-Vorlage stapelweise hochgeladen werden.

>[!TIP]
>
> Verwenden Sie eine Kombination aus Domain-spezifischen Eingabeaufforderungen, die von LLM Optimizer während der Ersteinrichtung empfohlen werden, und der Industry Prompt Library, um Ihre Eingabeaufforderungsstrategie zu kuratieren.

### In: Prompt Library Research Foundation

Die Industry Prompt Library wurde im Rahmen einer umfassenden Forschungsinitiative entwickelt, die Folgendes kombiniert:

* **Customer Intelligence:** Analyse des Suchverhaltens und der Voreinstellungen von KI bei über 6.000 Kunden
* **Branchenkompetenz:** Perspektiven von Experten aus den Bereichen Auto, Finanzdienstleistungen, Gesundheitswesen, Telekommunikation und Reisen.
* **Datengesteuerte Einblicke:** Identifizierung von wirkungsvollen Themen und Abfragemustern, die die Kundeninteraktion und Konversion fördern.

Top-Themen, die von Kunden aus verschiedenen Branchen gesucht werden:

* **Auto:** Fehlerbehebung bei Autoproblemen, Vergleich von Fahrzeugen und Finanzierung/Leasing
* **Finanzdienstleistungen:** Erforschung von Finanzprodukten
* **Gesundheitswesen:** Nachschlagen von Symptomen oder Gesundheitsproblemen, Vergleichen von Behandlungsoptionen, Verstehen von Laborergebnissen oder medizinischen Begriffen
* **Telekommunikation:** Vergleichen von Plänen, Vertragsbedingungen und Werbeaktionen, Überprüfen von Dienstleistungen in der Umgebung
* **Reisen:** Vorbereitung auf eine Reise, Recherche und Buchung von Reisen

Kundentrends bei KI-Suche und Promptverhalten in LLM-Tools:

* Kunden stellen bei der Verwendung von LLM-Suchwerkzeugen lieber Fragen als verwenden Keywords.
* Sie nutzen hauptsächlich LLM-Suchwerkzeuge für die Forschung und Entdeckung in der Frühphase.
* Kunden neigen dazu, in ihren Eingabeaufforderungen einen bestimmten Marken- oder Produktnamen anzugeben.

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

![Hinzufügen von Kategorien in LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Wählen Sie einen Ansatz und halten Sie sich daran.
> * Pro Konto/Marke kann nur **ein** Kategoriemodell verwendet werden. Mischen Sie **SBU** und **URL_DIR** nicht gleichzeitig.
<!--Can you mix Product/Service with these?-->

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

![Hinzufügen von Themen in LLM Optimizer](/help/assets/best-practices/add-topic.png)

Beachten Sie beim Erstellen der Liste Folgendes:

* Kann ein Editor das Thema in 5 Sekunden nach der Eingabeaufforderung verstehen? Falls nicht, benennen/vereinfachen Sie um.
* Wird die Fehlerbehebung für verschiedene Themen einem anderen Team gehören? Wenn ja, haben Sie nützliche Themen ausgewählt.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Einige zusätzliche hilfreiche Hinweise:

* Nutzen Sie Ihre geschäftlichen oder Site-Kenntnisse, um Themen zu definieren, die den strategischen Zielen Ihrer Marke entsprechen
* Beachten Sie, wie Ihre Marke im Vergleich zu anderen Marken innerhalb bestimmter Themen abschneidet.

>[!IMPORTANT]
>
> * Behalten Sie Themen bei, die absichtsbasiert, nicht organisatorisch sind.
> * Fügen Sie keine Kategorien/Filter für Marke/Nicht-Marke/Geografie hinzu, da Sie auf der Registerkarte **[!UICONTROL Marken]** gezielt danach filtern können.
> * Die Themen sind über mehrere Kategorien verteilt. Es **nicht möglich** eindeutige Themen für jede Kategorie zu definieren.
> * Eine einzelne Eingabeaufforderung **kann** in mehreren Themen oder Kategorien vorhanden sein.

## Best Practices für Eingabeaufforderungen

Anhand von Eingabeaufforderungen werden die spezifischen Fragen oder Abfragen identifiziert, die Kunden stellen und die sich auf Ihr Unternehmen auswirken können. Dabei handelt es sich um die eigentlichen Fragen oder Abfragen, die Benutzende in LLMs eingeben.

Stellen Sie sicher, dass Eingabeaufforderungen regelmäßig überprüft und aktualisiert werden, um sicherzustellen, dass sie mit den Kundenanforderungen und Geschäftszielen übereinstimmen.

Best Practices für Eingabeaufforderungen:

* Gruppieren Sie ähnliche Eingabeaufforderungen basierend auf den Fragen der Benutzer.
* Konzentrieren Sie sich auf die Eingabeaufforderungen, die für Ihre Kunden am wichtigsten sind.
* Überprüfen Sie, ob Ihre Marke gute Chancen hat, bei bestimmten Eingabeaufforderungen erwähnt zu werden.

>[!TIP]
>
>* Sie können Tools wie die Adobe LLM Optimizer- und die Google-Suchkonsole mit Regex-Filtern verwenden, um gängige Fragestrukturen zu identifizieren (z. B. „wie“, „was“, „wann“, „wo„) und herauszufinden, welche Aufforderungen die Personen für den Besuch Ihrer Site verwenden.
>* Um herauszufinden, welche Eingabeaufforderungen für Ihre Site/Marke relevant sind, können Sie Suchdaten auf der Site verwenden, FAQs auf Suchmaschinenergebnisseiten verwenden oder sogar LLM-Chatbots direkt fragen, welche Fragen Kunden zu Ihrer Marke stellen könnten.

## Best Practices für die Verfolgung anderer Marken

Mit „Andere nachverfolgen“ können Sie die Sichtbarkeit und Erwähnungen in LLM-Antworten auf für Ihr Unternehmen wichtige Eingabeaufforderungen und Themen überwachen.

Auf der Registerkarte [!UICONTROL **Andere Tracking**] können Sie weitere hinzufügen, einschließlich Wettbewerbern, um ihre Sichtbarkeit für bestimmte Eingabeaufforderungen und Themen zu verfolgen.

Bei der Nachverfolgung durch andere Benutzer können Sie sehen, wie oft andere Marken neben Ihrer Marke in verschiedenen Regionen und Kategorien erwähnt werden, und ihre Sichtbarkeit mit der Ihrer eigenen vergleichen.

>[!TIP]
>
>Überprüfen Sie regelmäßig die Erwähnungen und Zitate von Mitbewerbern oder anderen Anbietern, um Bereiche zu identifizieren, in denen sich Ihre Marke verbessern kann.

## Weitere Informationen

* [Dashboard für Kundenkonfiguration](/help/dashboards/customer-configuration.md) konfigurieren Sie Kategorien, Themen, Eingabeaufforderungen und anderes Tracking.
* [Best Practices für LLM Optimizer](/help/tutorials/best-practices.md) beschreibt Best Practices für die LLM-Optimierung

