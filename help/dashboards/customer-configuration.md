---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
feature: Customer Configuration
source-git-commit: 5d8b59ea4281c88bb42dc48096c07a3faaeb2e88
workflow-type: ht
source-wordcount: '836'
ht-degree: 100%

---


# Kundenkonfiguration {#customer-configuration}

Das Dashboard „Kundenkonfiguration“ ist ein leistungsstarkes Tool, das Erkenntnisse zur Sichtbarkeit Ihrer Marke in LLMs bietet. Durch das korrekte Einrichten von Kategorien, Themen und Prompts können Sie sicherstellen, dass Ihre Marke gut positioniert ist, um in LLM-generierten Antworten angezeigt zu werden. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Erkenntnisse auf Ihren Unternehmenskontext zuschneidet, sodass Sichtbarkeit, Traffic und Möglichkeiten genau analysiert werden können.

![Dashboard „Kundenkonfiguration“](/help/dashboards/assets/customer-config.png)

Um zu konfigurieren, wie LLM Optimizer Ihre Markenpräsenz in verschiedenen Märkten und Wettbewerbslandschaften überwacht und analysiert, können Sie die folgenden Registerkarten verwenden:

* [Prompts](#prompts-brand)
* [Kategorien](#categories)
* [Andere Marken](#other-brands)
* [Markenaliasse](#brand-aliases)
* [CDN-Konfiguration](#agentic-cdn)

>[!IMPORTANT]
>
> Weitere Informationen zum Einrichten von Kategorien, Themen und Prompts finden Sie auf der Seite [Best Practices bei der Konfiguration von Kategorien, Themen und Prompts](/help/overview/best-practices-topics-prompts.md).

## Prompts {#prompts-brand}

In dieser Registerkarte können Sie Prompts prüfen, verwalten und anpassen. Sie können eine CSV-Datei mit einer [Markenpräsenz-Analyse](/help/dashboards/brand-presence.md) hochladen, dann wird die Liste mit Prompts und Themen aus dieser Analyse gefüllt, oder eine von Adobe erstellte [Prompts-Bibliothek herunterladen](/help/overview/best-practices-topics-prompts.md). Je nach Bedarf können Sie Themen und die zugehörigen Prompts auch löschen, ändern und hinzufügen.

Um eine CSV-Datei mit Datenerkenntnissen zu importieren, müssen Sie zunächst eine Datei aus dem Dashboard „Markenpräsenz“ exportieren. Im Abschnitt [Datenerkenntnisse](/help/dashboards/brand-presence.md#data-insights) erfahren Sie, wie Sie dies tun. Wenn die Datei vorliegt:

1. Klicken Sie im Dashboard auf **CSV hochladen**.
2. Fügen Sie die Datei im Fenster „Datenerkenntnisse importieren“ per Drag-and-Drop hinzu oder wählen Sie sie manuell aus.
3. Klicken Sie auf **Daten hochladen**.

Sie können auch eine neue CSV-Datei erstellen, indem Sie die Vorlage aus dem Fenster **Datenerkenntnisse importieren** herunterladen. Wenn Sie die Vorlage haben, öffnen Sie sie und geben Sie Ihre Themen zusammen mit den zugehörigen Prompts, Kategorien und Regionen jeweils in einer neuen Zeile ein.

Informationen zum Herunterladen und Verwenden der von Adobe erstellten Branchen-Prompt-Bibliothek finden Sie im Abschnitt zur Branchen-Prompt-Bibliothek [auf dieser Seite](/help/overview/best-practices-topics-prompts.md).

Darüber hinaus können Sie der Liste auch unabhängig von einer CSV-Datei oder Prompt-Bibliothek Themen/Prompts hinzufügen. Gehen Sie dazu im Dashboard wie folgt vor:

1. Klicken Sie auf die Schaltfläche **Thema hinzufügen**.
2. Wählen Sie im Fenster der neuen Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Geben Sie den Themennamen ein.
4. Fügen Sie den Prompt-Text hinzu.
5. Wählen Sie die Region aus.
6. Klicken Sie auf **Prompt hinzufügen**. Das Thema wird nun mit dem Prompt in der Liste angezeigt.

>[!NOTE]
>Neu hinzugefügte Prompts werden erst dann in der Markenpräsenz angezeigt, wenn die Verarbeitung abgeschlossen ist.

Sie können in der Liste auf jedes Thema klicken, um die zugehörigen Prompts anzuzeigen. Um das Thema und die zugehörigen Prompts zu löschen, klicken Sie in der Liste auf das Symbol „Löschen“.

## Kategorien {#categories}

In der Registerkarte „Kategorien“ können Sie Geschäftskategorien oder Produktlinien definieren, die Sie nachverfolgen möchten, und sie mit bestimmten Regionen verknüpfen. Die Registerkarte „Kategorien“ wirkt sich auf nahezu alle anderen Anpassungen auf dieser Seite aus, da die Kategorien für die anderen Anpassungen (Tracking von anderen, Aliasse usw.) im Feld „Kategorie“ angezeigt werden. So fügen Sie eine neue Kategorie hinzu:

1. Klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Fügen Sie im Fenster der neuen Konfiguration den **Kategorienamen** hinzu.
3. Passen Sie die **zugeordnete Region** an, in der die Kategorie überwacht wird.
4. Klicken Sie auf **Speichern**. Die neue Kategorie wird in der Kategorieliste angezeigt.

Beim Hinzufügen neuer Kategorien werden nicht automatisch Themen und Prompts generiert. Diese müssen Sie manuell über die Registerkarte [Datenerkenntnisse](#data-insights) hinzufügen.

Um eine Kategorie zu löschen, klicken Sie in der Kategorieliste auf das Symbol „Löschen“. Seien Sie vorsichtig, da das **Löschen einer Kategorie auch die zugehörigen Elemente löscht**, z. B. die Markenaliasse, die mit dieser Kategorie verknüpft sind.

## Andere Marken {#others-tracking}

Mit dieser Registerkarte können Sie verfolgen, wie andere Marken in verschiedenen Kategorien und Regionen im Verhältnis zu Ihrer Marke erwähnt werden. Überwachen Sie deren Präsenz und Leistung in Ihren Marktsegmenten. So passen Sie das Tracking an:

1. Klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Wählen Sie im Fenster der neuen Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Fügen Sie den Namen der anderen Marke hinzu.
4. Passen Sie bei Bedarf den Alias und die Domains der anderen Marke an.
5. Klicken Sie auf **Speichern**.

Um einen Eintrag aus der Liste zu löschen, klicken Sie auf das Symbol „Löschen“.

## Markenaliasse {#brand-aliases}

Mit Markenaliassen können Sie alternative Namen und Varianten Ihrer Marke konfigurieren, die über verschiedene Kategorien und Regionen hinweg nachverfolgt werden sollen. Dadurch wird ein umfassendes Monitoring aller Markenerwähnungen gewährleistet. So fügen Sie einen Markenalias hinzu:

1. Klicken Sie auf die Schaltfläche **Hinzufügen**.
2. Wählen Sie im Fenster der neuen Konfiguration die Option **Kategorie** aus. Zuvor erstellte Kategorien werden hier angezeigt.
3. Wählen Sie die **Region** aus, in der der Alias überwacht werden soll.
4. Fügen Sie den Markenalias hinzu.
5. Klicken Sie auf **Speichern**. Der Markenalias wird in der Liste angezeigt.

Um einen Markenalias zu löschen, klicken Sie in der Liste der Aliasse auf das Symbol „Löschen“.

## CDN-Konfiguration {#cdn-configuration}

In dieser Registerkarte können Sie Ihre CDN-Streams konfigurieren, damit Adobe LLM Optimizer Ihre CDN-Daten analysieren kann. Diese Daten werden für Dashboards (z. B. „Agent-basierter Traffic“) verwendet und stellen Erkenntnisse zu Traffic-Mustern, Leistungsmetriken und Optimierungsmöglichkeiten bereit. Um Ihren CDN-Anbieter zu integrieren, klicken Sie auf **CDN integrieren**.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Im Fenster **CDN-Anbieter integrieren**:

1. Wählen Sie Ihren CDN-Anbieter aus.
2. Klicken Sie auf **Integrieren**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an llmo-now@adobe.com wenden, um Hilfe zu erhalten.
