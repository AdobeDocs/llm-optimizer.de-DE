---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
source-git-commit: a699f8f3c50f77d07f29cd354fd1ef8e6eed8ff9
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 1%

---


# Kundenkonfiguration {#customer-configuration}

Das Dashboard für Kundenkonfigurationen ist ein leistungsstarkes Tool, das Einblicke in die Sichtbarkeit Ihrer Marke in LLMs bietet. Durch das korrekte Einrichten von Kategorien, Themen, Eingabeaufforderungen und Konkurrenten können Sie sicherstellen, dass Ihre Marke gut positioniert ist, um in LLM-generierten Antworten angezeigt zu werden. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Einblicke auf Ihren Geschäftskontext zuschneidet, was eine genaue Sichtbarkeit, Traffic und Opportunity-Analyse ermöglicht.

![Kundenkonfigurations-Dashboard](/help/dashboards/assets/customer-config.png)

Um zu konfigurieren, wie LLM Optimizer Ihre Markenpräsenz auf verschiedenen Märkten und in verschiedenen Wettbewerbslandschaften überwacht und analysiert, haben Sie Zugriff auf die folgenden Registerkarten:

* [Kategorien](#categories)
* [Mitbewerber-Tracking](#competitor-tracking)
* [Markenalias](#brand-aliases)
* [Data Insights](#data-insights)
* [CDN-Konfiguration](#agentic-cdn)

>[!IMPORTANT]
>
> Weitere Informationen zum Einrichten von Kategorien, Themen, Eingabeaufforderungen und Wettbewerbern finden Sie auf der Seite [Best Practices zum Konfigurieren von Kategorien, Themen, Eingabeaufforderungen und Wettbewerbern](/help/overview/best-practices-topics-prompts.md) .

## Kategorien {#categories}

Auf der Registerkarte Kategorien können Sie Geschäftskategorien oder Produktlinien definieren, die Sie verfolgen möchten, und sie mit bestimmten Regionen verknüpfen. Insgesamt bezieht sich die Registerkarte Kategorien auf fast jede andere Anpassung auf dieser Seite, da Kategorien im Feld Kategorie für die anderen Anpassungen angezeigt werden (Konkurrenten-Tracking, Aliase usw.). Hinzufügen einer neuen Kategorie:

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

Um eine CSV-Datei mit Datenerkenntnissen zu importieren, müssen Sie zunächst eine Datei aus dem Dashboard „Markenpräsenz“ exportieren. Weitere Informationen dazu finden [ im ](/help/dashboards/brand-presence.md#data-insights) „Dateneinblicke“. Sobald Sie die Datei haben:

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

## CDN-Konfiguration {#cdn-configuration}

Auf dieser Registerkarte können Sie Ihre CDN-Streams konfigurieren, damit Adobe LLM Optimizer Ihre CDN-Daten analysieren kann. Diese Daten werden für Dashboards (wie den Agentenverkehr) verwendet, die Einblicke in Traffic-Muster, Leistungsmetriken und Optimierungsmöglichkeiten bieten. Um Ihren CDN-Provider zu integrieren, klicken Sie auf **Onboarding CDN**.

![Kundenkonfigurations-CDN](/help/overview/assets/cc-cdn.png)

Im Fenster **Onboarding CDN Provider**:

1. Wählen Sie Ihren CDN-Provider aus (z. B. Akamai, Adobe-Managed Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare oder andere).
2. Klicken Sie **Onboard**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an Adobe wenden, um Hilfe zu erhalten.
