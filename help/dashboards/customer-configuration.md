---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
source-git-commit: 653a6be856412faac8783fa9dc7b759a7c6e1f68
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 1%

---


# Kundenkonfiguration

In der Kundenkonfiguration legen Sie fest, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird. Sie können Kategorien (z. B. Geschäftsbereiche oder Produktlinien) anpassen, Mitbewerber verfolgen und Aliase für Markenbezeichnungen hinzufügen, um alle Varianten Ihrer Marke über Eingabeaufforderungen hinweg zu erfassen. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Einblicke auf Ihren Geschäftskontext zuschneidet, was eine genaue Sichtbarkeit, Traffic und Opportunity-Analyse ermöglicht.

![Kundenkonfigurations-Dashboard](/help/dashboards/assets/customer-config.png)


## Best Practices zum Konfigurieren von Kategorien, Themen und Eingabeaufforderungen

In diesem Abschnitt werden Best Practices beschrieben, mit deren Hilfe Sie entscheiden können, wie Sie Kategorien, Themen, Eingabeaufforderungen und Mitbewerber einrichten möchten.

Dies ist ein entscheidender erster Schritt. Was Sie jetzt entscheiden, bestimmt, wie Informationen auf Ihren Geschäftskontext zugeschnitten werden. Alle Änderungen an Kategorien in der Zukunft setzen historische Daten zurück.

### Best Practices für Kategorien

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

Zum Beispiel:

| Site-Typ | Kategorie | Beispiele für Topic Taxonomy |
|---------|----------|---------|
| Unternehmen mit mehreren Unternehmen | SBU | Small Intent Set (Anleitung, Fehlerbehebung, Vergleich, Preise, Richtlinie) |
| Dokumentation/Support vor Ort | URL_DIR | Anleitung, Fehlerbehebung, Referenz, Versionshinweise |
| E-Commerce/Services-Katalog | Produkt/Service | Vergleich, Bewertungen, Preise/Verfügbarkeit, Anleitungen, Fehlerbehebung |

### Best Practices für Themen

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
* Firmen / Nachrichten (wenn Sie sie wirklich brauchen)

Beachten Sie beim Erstellen der Liste Folgendes:

* Kann ein Editor das Thema in 5 Sekunden nach der Eingabeaufforderung verstehen? Falls nicht, benennen/vereinfachen Sie um.
* Wird die Fehlerbehebung für verschiedene Themen einem anderen Team gehören? Wenn ja, haben Sie nützliche Themen ausgewählt.

Einige zusätzliche hilfreiche Hinweise:

* Nutzen Sie Ihre geschäftlichen oder Site-Kenntnisse, um Themen zu definieren, die den strategischen Zielen Ihrer Marke entsprechen
* Berücksichtigen Sie bei bestimmten Themen den Vergleich Ihrer Marke mit Konkurrenten.

>[!IMPORTANT]
>
> * Behalten Sie Themen bei, die absichtsbasiert, nicht organisatorisch sind.
> * Fügen Sie keine Kategorien/Filter für Marke/Nicht-Marke/Geografie hinzu, da Sie auf der Registerkarte **Marken** gezielt danach filtern können.
> * Themen sind über mehrere Kategorien verteilt. Sie können **verschiedene Themen** Kategorie haben.
> * Eine Eingabeaufforderung kann in mehreren Themen oder Kategorien vorhanden sein.

### Best Practices für Eingabeaufforderungen

Anhand von Eingabeaufforderungen werden die spezifischen Fragen oder Abfragen identifiziert, die Kunden stellen und die sich auf Ihr Unternehmen auswirken können. Dabei handelt es sich um die eigentlichen Fragen oder Abfragen, die Benutzende in LLMs eingeben.

Stellen Sie sicher, dass Eingabeaufforderungen regelmäßig überprüft und aktualisiert werden, um sicherzustellen, dass sie mit den Kundenanforderungen und Geschäftszielen übereinstimmen.

>[!TIP]
>
>* Sie können Tools wie die LLM Optimizer- und die Google-Suchkonsole mit Regex-Filtern verwenden, um allgemeine Fragenstrukturen zu identifizieren (z. B. „wie“, „was“, „wann“, „wo„).
>* Um herauszufinden, welche Eingabeaufforderungen für Ihre Site/Marke relevant sind, können Sie Suchdaten auf der Site verwenden, FAQs auf Suchmaschinenergebnisseiten verwenden oder sogar LLM-Chatbots direkt fragen, welche Fragen Kunden zu Ihrer Marke stellen könnten.

### Best Practices für Mitbewerber

Mitbewerber ermöglichen es Ihnen, die Sichtbarkeit und Erwähnungen in den LLM-Antworten auf für Ihr Unternehmen wichtige Eingabeaufforderungen und Themen zu überwachen.

Auf [!UICONTROL **Registerkarte**] Wettbewerbs-Tracking“ können Sie Konkurrenten hinzufügen und ihre Sichtbarkeit für bestimmte Eingabeaufforderungen und Themen verfolgen.

Mit dem Wettbewerb-Tracking können Sie sehen, wie oft Wettbewerber neben Ihrer Marke in verschiedenen Regionen und Kategorien erwähnt werden, und ihre Sichtbarkeit mit Ihrer eigenen vergleichen.

>[!TIP]
>
>Überprüfen Sie regelmäßig die Erwähnungen und Zitate von Mitbewerbern, um Bereiche zu identifizieren, in denen sich Ihre Marke verbessern kann.

## Kundenkonfigurations-Dashboard

Das Dashboard für Kundenkonfigurationen ist ein leistungsstarkes Tool, das Einblicke in die Sichtbarkeit Ihrer Marke in LLMs bietet. Durch das korrekte Einrichten von Kategorien, Themen, Eingabeaufforderungen und Konkurrenten können Sie sicherstellen, dass Ihre Marke gut positioniert ist, um in LLM-generierten Antworten angezeigt zu werden. Das regelmäßige Überprüfen von Einblicken wie Stimmanteil, Sichtbarkeit von Inhalten und Chancen hilft Ihnen, Ihre Strategie anzupassen und der Konkurrenz einen Schritt voraus zu sein.

Um zu konfigurieren, wie LLM Optimizer Ihre Markenpräsenz auf verschiedenen Märkten und in verschiedenen Wettbewerbslandschaften überwacht und analysiert, haben Sie Zugriff auf die folgenden Registerkarten:

* [Kategorien](#categories)
* [Mitbewerber-Tracking](#competitor-tracking)
* [Markenalias](#brand-aliases)
* [Data Insights](#data-insights)
* [Agent-CDN](#agentic-cdn)

## Kategorien {#categories}

Auf der Registerkarte Kategorien können Sie Geschäftskategorien oder Produktlinien definieren, die Sie verfolgen möchten, und sie mit bestimmten Regionen verknüpfen. Insgesamt bezieht sich die Registerkarte Kategorien auf jede andere Anpassung auf dieser Seite, da Kategorien im Feld Kategorie für die anderen Anpassungen angezeigt werden (Wettbewerber-Tracking, Aliase usw.). Hinzufügen einer neuen Kategorie:

1. Klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Fügen Sie im Fenster für die neue Konfiguration den **Kategorienamen“**.
3. Passen Sie die **zugeordnete Region** an, in der die Kategorie überwacht wird.
4. Klicken Sie **Speichern** und die neue Kategorie wird in der Kategorieliste angezeigt.

Durch das Hinzufügen neuer Kategorien werden nicht automatisch Themen und Eingabeaufforderungen generiert. Diese müssen manuell über die Registerkarte [Dateneinblicke](#data-insights) hinzugefügt werden.

Um eine Kategorie zu löschen, klicken Sie in der Kategorieliste auf das Löschsymbol. Vorsicht ist geboten, da **beim Löschen einer Kategorie auch die zugehörigen Elemente gelöscht werden** z. B. Wettbewerber, die Sie möglicherweise eingerichtet haben, oder Markenaliase, die mit dieser bestimmten Kategorie verknüpft sind.

## Mitbewerber-Tracking {#competitor-tracking}

Mithilfe des Wettbewerbs-Trackings können Sie verfolgen, wie Ihre Konkurrenten in Bezug auf Ihre Marke in verschiedenen Kategorien und Regionen erwähnt werden. Überwachen Sie deren Präsenz und Leistung in Ihren Marktsegmenten. So passen Sie das Mitbewerber-Tracking an:

1. Um einen neuen Mitbewerber hinzuzufügen, klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Wählen Sie im Fenster für die neue Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Fügen Sie den Namen des Mitbewerbers hinzu.
4. Passen Sie bei Bedarf den Konkurrenzalias und die Domains an.
5. Klicken Sie **Speichern** und der neue Mitbewerber wird auf der Liste der Mitbewerber angezeigt.

Um einen Mitbewerber zu löschen, klicken Sie auf das Löschsymbol in der Liste der Mitbewerber.

## Markenalias {#brand-aliases}

Mithilfe von Markenaliasen können Sie alternative Namen und Varianten Ihrer Marke konfigurieren, die über verschiedene Kategorien und Regionen hinweg verfolgt werden sollen. Dadurch wird eine umfassende Überwachung aller Markenbezeichnungen gewährleistet. So fügen Sie einen Markenalias hinzu:

1. Klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Wählen Sie im Fenster für die neue Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Wählen Sie **Region**, in der der Alias überwacht wird.
4. Fügen Sie den Markenalias hinzu.
5. Klicken Sie **Speichern** und der Markenalias wird in der Liste angezeigt.

Um einen Markenalias zu löschen, klicken Sie in der Alias-Liste auf das Symbol Löschen .

## Data Insights {#data-insights}

Auf dieser Registerkarte können Sie Eingabeaufforderungen überprüfen, verwalten und anpassen. Sie können eine CSV-Datei [Dateneinblicke zur Markenpräsenz](/help/dashboards/brand-presence.md#data-insights) hochladen und die Liste mit Eingabeaufforderungen und Themen aus dieser Analyse füllen. Bei Bedarf können Sie auch Themen und die zugehörigen Aufforderungen löschen, ändern und hinzufügen.

Um eine CSV-Datei mit Datenerkenntnissen zu importieren, müssen Sie zunächst eine Datei aus dem Dashboard „Markenpräsenz“ exportieren. Weitere Informationen dazu finden [&#x200B; im &#x200B;](/help/dashboards/brand-presence.md#data-insights) „Dateneinblicke“. Sobald Sie die Datei haben:

1. Klicken Sie im Dashboard auf **CSV hochladen**.
2. Ziehen Sie im Fenster Dateneinblicke importieren per Drag-and-Drop oder wählen Sie die Datei manuell aus.
3. Klicken Sie **Daten hochladen**.

Sie können auch eine neue CSV-Datei erstellen, indem Sie die Vorlage aus dem Fenster **Dateneinblicke importieren** herunterladen. Sobald Sie die Vorlage haben, öffnen Sie sie und geben Sie Ihre Themen zusammen mit den zugehörigen Eingabeaufforderungen, Kategorien und Regionen in einer neuen Zeile ein.

Darüber hinaus können Sie der Liste auch Themen/Eingabeaufforderungen unabhängig von einer CSV-Datei hinzufügen. Gehen Sie dazu im Dashboard wie folgt vor:

1. Klicken Sie auf **Schaltfläche „Thema**&quot;.
2. Wählen Sie im Fenster für die neue Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Geben Sie den Themennamen ein.
4. Fügen Sie den Eingabeaufforderungstext hinzu.
5. Auswählen der Region.
6. Klicken Sie **Eingabeaufforderung hinzufügen** und das Thema mit der Eingabeaufforderung wird in der Liste angezeigt.

>[!NOTE]
>Neu hinzugefügte Eingabeaufforderungen werden erst dann in der Markenpräsenz angezeigt, wenn die Verarbeitung abgeschlossen ist.

In der Liste können Sie auf jedes Thema klicken, und die zugehörigen Eingabeaufforderungen werden angezeigt. Um das Thema und die zugehörigen Eingabeaufforderungen zu löschen, klicken Sie auf das Löschsymbol in der Liste.

## Agent-CDN {#agentic-cdn}

Nicht verfügbar (wird sie zur Veröffentlichung verfügbar sein?).

