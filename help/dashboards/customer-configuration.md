---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
feature: Customer Configuration
source-git-commit: 3fab5f21311a741e51e7a31cd3a26de79fcbff95
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 40%

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
* [Google Search Console](#google-console)

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

Um einen Markenalias zu löschen, klicken Sie in der **auf das Symbol** Löschen“.

## CDN-Konfiguration {#cdn-configuration}

In dieser Registerkarte können Sie Ihre CDN-Streams konfigurieren, damit Adobe LLM Optimizer Ihre CDN-Daten analysieren kann. Diese Daten werden für Dashboards (z. B. „Agent-basierter Traffic“) verwendet und stellen Erkenntnisse zu Traffic-Mustern, Leistungsmetriken und Optimierungsmöglichkeiten bereit. Um Ihren CDN-Anbieter zu integrieren, klicken Sie auf **CDN integrieren**.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Im Fenster **CDN-Anbieter integrieren**:

1. Wählen Sie Ihren CDN-Anbieter aus.
2. Klicken Sie auf **Integrieren**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an llmo-now@adobe.com wenden, um Hilfe zu erhalten.

## Google Search Console {#google-console}

Mit Adobe LLM Optimizer können Sie Ihr Google Search Console-Konto integrieren, um echte Suchabfragen direkt in die Benutzeroberfläche zu bringen. Indem Sie echte Abfragen der Google-Suchkonsole anzeigen, können Sie Aufforderungssätze erstellen, die auf dem tatsächlichen Suchverhalten und zielgerichteten Erkennungsmustern basieren. Auf diese Weise können Sie Eingabeaufforderungen basierend auf bewährten Anforderungen priorisieren und die LLM-Optimierung an der aktuellen Suchmethode der Benutzer ausrichten. Darüber hinaus behalten Sie die volle Kontrolle, da Abfragen nie automatisch hinzugefügt werden und explizit ausgewählt werden müssen, bevor Sie zu aktiven Eingabeaufforderungen werden.

### Funktionsweise {#how-it-works}

An die Integration zwischen LLM Optimizer und Google Search Console sollte vor allem Folgendes erinnert werden: Anstatt manuell zu erraten, welche Kunden möglicherweise einen KI-Assistenten fragen, schauen wir uns an, wonach sie **bereits suchen** und wandeln diese echten Abfragen in natürliche, dialogorientierte Eingabeaufforderungen um. Dieser Prozess der Umstellung von Suchabfragen auf KI-Eingabeaufforderungen wird im folgenden Diagramm veranschaulicht.

![Prozessfluss](/help/dashboards/assets/diagram-flow.png)

Im Allgemeinen umfasst der Prozess fünf Schritte:

#### Schritt 1: Erfassen Sie Ihre echten Suchdaten {#gsc-one}

Der Prozess beginnt mit den Keywords, die Ihre Zielgruppe tatsächlich verwendet, wenn sie Ihre Website über Google findet. Dieser Rohdatensatz (oft Tausende eindeutiger Abfragen) ist die Grundlage für alles, was folgt.

#### Schritt 2 — Bedeutung und Filter auf Sicherheit analysieren {#gsc-two}

Jede Abfrage wird auf ihre semantische Bedeutung (worum der Benutzer wirklich bittet) analysiert und durch einen Sicherheitsfilter gefiltert, der unangemessene oder markenfremde Inhalte entfernt. Dadurch wird sichergestellt, dass nur saubere, relevante Keywords weiterentwickelt werden.

#### Schritt 3 — Nach Kategorien und Themen gruppieren {#gsc-three}

Zugehörige Abfragen werden automatisch in **Kategorien** (allgemeine Geschäftsthemen) und **Themen** (fokussierte Unterthemen innerhalb jeder Kategorie) gruppiert. Das System priorisiert Kategorien, die bereits in Ihrem LLM Optimizer-Setup konfiguriert sind. Darüber hinaus können neue Kategorien angezeigt werden, die aus Ihren Suchdaten hervorgehen, aber noch nicht überwacht werden. Das folgende Diagramm zeigt ein Beispiel für Kategorien und Themen einer Möbelmarke:

![Möbelmarke](/help/dashboards/assets/diagram-example.png)

#### Schritt 4 - Eingabeaufforderungen generieren, die auf echten Keywords basieren {#gsc-four}

Für jedes Thema generiert das System Eingabeaufforderungen, die der Art und Weise ähneln, wie echte Menschen mit KI-Assistenten sprechen. Jede Eingabeaufforderung wird direkt von den tatsächlichen Suchbegriffen aus Ihrer Google-Suchkonsole beeinflusst, wodurch die Keyword-Absicht in natürliche Gesprächsfragen umgewandelt wird.

Dieser (auf Keywords basierende) Ansatz bedeutet:

* Eingabeaufforderungen spiegeln eine reale Nachfrage wider, keine hypothetischen Fragen.
* Die Sprache spiegelt wider, wie Kunden Dinge tatsächlich formulieren.
* Die Abdeckung erstreckt sich über den gesamten Bereich dessen, wonach auf Ihrer Site gesucht wird.

Bei der Eingabeaufforderungsgenerierung wird auch Ihr Markenprofil berücksichtigt, einschließlich Produkten, Mitbewerbern, Branchenpositionierung und Zielgruppe, um sicherzustellen, dass Eingabeaufforderungen kontextuell korrekt sind.

#### Schritt 5: Qualitätssicherung und Lieferung {#gsc-five}

Vor dem Versand durchläuft jede Eingabeaufforderung mehrere automatisierte Qualitätsprüfungen:

* Deduplizierung - nahezu identische Eingabeaufforderungen werden entfernt.
* Ausgleich des Markenverhältnisses - sorgt für einen realistischen Mix (~75 % ohne Markenbezeichnung, ~25 % Markenbezeichnung).
* Sprachqualität - nimmt robotische Formulierungen weg und gibt so natürliche Klänge wieder.
* Konsistenzprüfungen - Validiert Füllsätze, entfernt sie und sorgt für eine knappe Länge.

Darüber hinaus wird jede Eingabeaufforderung mit der zugehörigen Kategorie, dem Thema, dem Absichtstyp und der gebrandeten/nicht gebrandeten Klassifizierung versehen, damit LLM Optimizer mit der Überwachung beginnen kann.

#### Eingabeaufforderungsanatomie {#prompt-anatomy}

Nach Abschluss des obigen Prozesses hat jede an LLM Optimizer gesendete Eingabeaufforderung die folgenden Attribute:

| Feld | Beschreibung |
|---------|----------|
| Text | Die Eingabeaufforderung, ähnlich wie ein Benutzer sie in einen KI-Assistenten eingeben würde |
| Kategorie | Das dieser Eingabeaufforderung zugewiesene allgemeine Geschäftsthema. |
| Thema | Das spezifische Unterthema innerhalb der Kategorie. |
| Region | Zielmarkt (z. B. USA, Vereinigtes Königreich usw.) |
| Absicht | Die Benutzermentalität: informativ, vergleichend, transaktional, lehrerisch, planend oder delegiert. |
| Typ | Der Typ kann entweder mit einem Branding versehen sein (erwähnt die Marke/Produkte) oder ohne Branding (allgemeine Frage der Branche). |

### Informationen zur Verwendung {#how-to-use}

Gehen Sie wie folgt vor, um die Abfragen der Google-Suchkonsole in LLM Optimizer zu integrieren und zu verwenden.

#### Verbinden der Google-Suchkonsole {#connect-console}

Bevor Sie diese Funktion verwenden können, müssen Sie Ihr Google Search Console-Konto mit LLM Optimizer integrieren.

1. Öffnen Sie das Dashboard Kundenkonfiguration .
1. Navigieren Sie zur Registerkarte Google-Suchkonsole und klicken Sie auf **Konto verbinden**.
   ![Google-Suchkonsole](/help/dashboards/assets/google-console.png)
1. Melden Sie sich mit einem Google-Konto an, das Zugriff auf die gewünschte Search Console-Eigenschaft hat.
   ![Google-Konto](/help/dashboards/assets/google-account.png)
1. Wählen Sie die Eigenschaft aus, die Sie verbinden möchten.
   ![Konsoleneigenschaft](/help/dashboards/assets/console-property.png)
1. Nachdem die Verbindung hergestellt wurde, beginnt LLM Optimizer mit dem Abrufen relevanter Suchabfragen.
   ![Daten werden abgerufen](/help/dashboards/assets/console-complete.png)

#### Überprüfen und Suchen von Abfragen {#search-query}

Nachdem Sie das Google Search Console-Konto in LLM Optimizer integriert haben, können Sie die Liste der Themen und Eingabeaufforderungen überprüfen, die Sie aus der Suchkonsole beziehen, und die Eingabeaufforderungen aus der Liste hinzufügen.

1. Überprüfen Sie auf der Registerkarte Google-Suchkonsole die Liste der Themen und Eingabeaufforderungen aus der Suchkonsole.
   ![Liste mit Eingabeaufforderungen](/help/dashboards/assets/prompts-list.png)
1. Klicken Sie auf das gewünschte Thema/die gewünschte Aufforderungskategorie, um die Liste zu erweitern.
1. Verwenden Sie die **Hinzufügen**, um Eingabeaufforderungen aus der Liste hinzuzufügen. Sie können Aufforderungen und Kategorien auch stapelweise hinzufügen, indem Sie **Alle hinzufügen** verwenden.
   ![Eingabeaufforderungen hinzufügen](/help/dashboards/assets/add-prompts.png)
1. Wenn Sie mit der Auswahl zufrieden sind, klicken Sie auf **Speichern** in der Benachrichtigung.

#### Anzeigen hinzugefügter Abfragen in der Liste „Eingabeaufforderungen“ {#prompts-list}

Nachdem eine Abfrage hinzugefügt wurde, wird sie auf der Registerkarte [Eingabeaufforderungen](#prompts-brand) im Dashboard Kundenkonfiguration angezeigt. Eingabeaufforderungen aus der Google-Suchkonsole werden mit einem Google-Suchkonsolensymbol in der Spalte **Herkunft** gekennzeichnet. Mit dem Symbol können Sie zwischen Eingabeaufforderungen, die auf dem tatsächlichen Suchverhalten der Benutzenden basieren, und Eingabeaufforderungen unterscheiden, die manuell oder aus anderen Quellen hinzugefügt wurden.

### Häufig gestellte Fragen {#gsc-faq}

F: Wie oft werden Eingabeaufforderungen im Dashboard der Google-Suchkonsole aktualisiert?

Eingabeaufforderungen aus der Google-Suchkonsole werden in der Regel einmal pro Monat aktualisiert. Bei jeder Aktualisierung werden die neuesten Suchabfragedaten aus Ihrer Google Search Console abgerufen, die Generierungs-Pipeline wird erneut ausgeführt und der Eingabeaufforderungssatz wird aktualisiert. Dadurch wird sichergestellt, dass Ihre Eingabeaufforderungen mit aktuellen Suchtrends und saisonalen Veränderungen im Benutzerverhalten übereinstimmen.

F.: Wie viele Eingabeaufforderungen stammen normalerweise aus der Google-Suchkonsole?

Die Anzahl hängt von der Größe Ihrer Bereitstellung und der Anzahl der verfolgten Kategorien ab. Beispiel:

| Kategorien | Themen insgesamt | Eingabeaufforderungen zugestellt |
|---------|----------|----------|
| 1-2 | 3-8 | ~65-180 |
| 4-5 | 12-20 | ~270-450 |
| 10 | 30-40 | ~675-900 |

Wir sind bestrebt, Prompt-Sets zu liefern, die die Qualitätsziele erfüllen, die während der Testphase und des Onboarding kommuniziert wurden: mindestens 20 Eingabeaufforderungen pro Thema mit 3-4 Themen pro Kategorie und ein gesundes Verhältnis zwischen Marke und Nicht-Marke.

F: Wie bald werden Eingabeaufforderungen angezeigt, die von der Google-Suchkonsole bezogen wurden, nachdem ich eine Verbindung zur Google-Suchkonsole hergestellt habe?

Eingabeaufforderungen sind in der Regel (**Stunden) verfügbar** nachdem die Google-Suchkonsolenverbindung hergestellt wurde. Die Pipeline ruft automatisch Ihre Suchdaten ab, verarbeitet sie durch die Generierungs- und Qualitätssicherungsschritte und liefert die endgültige Eingabeaufforderung an LLM Optimizer.

F: Wer kann eine Verbindung zur Google-Suchkonsole herstellen?

Jeder Benutzer **Inhaber** oder **Vollständige Berechtigung** auf der Google Search Console -Eigenschaft kann die Verbindung autorisieren. Dies sind die Berechtigungsebenen, die Lesezugriff auf Suchabfragedaten gewähren. Wenn Sie sich bezüglich Ihrer Berechtigungsstufe nicht sicher sind, können Sie sie unter **Einstellungen>Benutzer** und Berechtigungen in Ihrer Google-Suchkonsole überprüfen.

F.: Kann ich Eingabeaufforderungen als ignoriert oder übersprungen markieren, damit sie nicht in der Eingabeaufforderungsliste der Google-Suchkonsole angezeigt werden?

Ja, Sie können jede Eingabeaufforderung löschen, die Sie nicht überwachen möchten. Gelöschte Eingabeaufforderungen werden aus Ihrer aktiven Eingabeaufforderungsliste entfernt und werden in zukünftigen Berichten nicht mehr angezeigt. Wenn eine gelöschte Eingabeaufforderung bei einer nachfolgenden monatlichen Aktualisierung neu generiert wird, können Sie sie erneut entfernen.

F.: Sobald ich Eingabeaufforderungen aus der Google-Suchkonsole zu meiner Eingabeaufforderungsliste hinzugefügt habe, wie schnell werden die Markenpräsenz-Daten für diese Eingabeaufforderungen angezeigt?

Markenpräsenz-Daten für neu hinzugefügte Eingabeaufforderungen werden bei der nächsten geplanten Datenaktualisierung angezeigt, die normalerweise zu Beginn jeder Woche ausgeführt wird. Je nachdem, wann Sie die Eingabeaufforderungen hinzufügen, können Sie innerhalb weniger Tage Ergebnisse sehen.
