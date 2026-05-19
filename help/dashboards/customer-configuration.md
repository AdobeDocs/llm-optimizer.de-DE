---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
feature: Customer Configuration
autotag-review: '2026-05-15T17:45:12.067Z'
TQID: 'https://experienceleague.adobe.com/qa7zk54n9G19-Azz9f6mn7V1kAGvnJSOJjpxbTBeHgc'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 2249
ht-degree: 100%

---


# Kundenkonfiguration {#customer-configuration}

Das Dashboard „Kundenkonfiguration“ ist ein leistungsstarkes Tool, das Erkenntnisse zur Sichtbarkeit Ihrer Marke in LLMs bietet. Durch das korrekte Einrichten von Kategorien, Themen und Prompts können Sie sicherstellen, dass Ihre Marke gut positioniert ist, um in LLM-generierten Antworten angezeigt zu werden. Durch diese Einrichtung wird sichergestellt, dass die Plattform die Erkenntnisse auf Ihren Unternehmenskontext zuschneidet, sodass Sichtbarkeit, Traffic und Möglichkeiten genau analysiert werden können.

Das Dashboard „Kundenkonfiguration“ (siehe unten) wird angewendet, wenn Ihre Organisation diese Navigation weiterhin verwendet.

![Dashboard „Kundenkonfiguration“](/help/dashboards/assets/customer-config.png)

Um zu konfigurieren, wie LLM Optimizer Ihre Markenpräsenz in verschiedenen Märkten und Wettbewerbslandschaften überwacht und analysiert, können Sie die folgenden Registerkarten verwenden:

* [Prompts](#prompts-brand)
* [Kategorien](#categories)
* [Andere Marken](#other-brands)
* [Markenaliasse](#brand-aliases)
* [CDN-Konfiguration](#agentic-cdn)
* [Google Search Console](#google-console)

Wenn Sie die [markenorientierte Oberfläche](/help/overview/quick-start.md#brand-centric-experience) verwenden, navigieren Sie zu **Markenverwaltung**, um Marken, Markenaliasse und Konkurrenz einzurichten und zu konfigurieren, um anhand des Trackings mit diesen Vergleiche zu ziehen. Die **Markenverwaltung** wird auch verwendet, um Integrationen wie Google Search Console, Adobe Analytics und CDN-Protokollweiterleitung zu konfigurieren, die sich auf mit Marken verknüpfte URLs beziehen. Klicken Sie dazu auf die entsprechenden Registerkarten: GSC, CDN usw.

![Markenverwaltung – App-Navigation (markenorientierte Oberfläche)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Markenverwaltung – Konfigurationsüberblick (markenorientierte Oberfläche)](/help/assets/brand-centric-experience/brands-management-configuration.png)

>[!IMPORTANT]
>
> Weitere Informationen zum Einrichten von Kategorien, Themen und Prompts finden Sie auf der Seite [Best Practices bei der Konfiguration von Kategorien, Themen und Prompts](/help/overview/best-practices-topics-prompts.md).

## Prompts {#prompts-brand}

In der Registerkarte **Prompts** können Sie Prompts überprüfen, verwalten und anpassen. Sie können eine CSV-Datei mit einer [Markenpräsenz-Analyse](/help/dashboards/brand-presence.md) hochladen, dann wird die Liste mit Prompts und Themen aus dieser Analyse gefüllt, oder eine von Adobe erstellte [Prompts-Bibliothek herunterladen](/help/overview/best-practices-topics-prompts.md). Je nach Bedarf können Sie Themen und die zugehörigen Prompts auch löschen, ändern und hinzufügen.

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

Für Kundschaften, die die [markenorientierten Oberfläche](/help/overview/quick-start.md#brand-centric-experience) verwenden, navigieren Sie zum Hinzufügen von Themen und Prompts zu **Prompts-Verwaltung**.

![Prompts-Verwaltung (markenorientierte Oberfläche)](/help/assets/brand-centric-experience/prompts-management.png)

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

Um einen Markenalias zu löschen, klicken Sie in der Liste der Aliasse auf das Symbol **Löschen**.

## CDN-Konfiguration {#cdn-configuration}

In dieser Registerkarte können Sie Ihre CDN-Streams konfigurieren, damit Adobe LLM Optimizer Ihre CDN-Daten analysieren kann. Diese Daten werden für Dashboards (z. B. „Agent-basierter Traffic“) verwendet und stellen Erkenntnisse zu Traffic-Mustern, Leistungsmetriken und Optimierungsmöglichkeiten bereit. Um Ihren CDN-Anbieter zu integrieren, klicken Sie auf **CDN integrieren**.

![CDN-Kundenkonfiguration](/help/overview/assets/cc-cdn.png)

Im Fenster **CDN-Anbieter integrieren**:

1. Wählen Sie Ihren CDN-Anbieter aus.
2. Klicken Sie auf **Integrieren**, um die Protokollweiterleitung zu aktivieren.

Wenn Sie **Sonstige** auswählen, müssen Sie sich an llmo-now@adobe.com wenden, um Hilfe zu erhalten.

## Google Search Console {#google-console}

Mit Adobe LLM Optimizer können Sie Ihr Google Search Console-Konto integrieren, um echte Suchabfragen direkt in der Benutzeroberfläche zu ermöglichen. Indem Sie echte Google Search Console-Abfragen ermöglichen, können Sie Prompt-Sets erstellen, die auf tatsächlichem Suchverhalten und zielgerichteten Erkennungsmustern basieren. Auf diese Weise können Sie Prompts basierend auf bewährten Anforderungen priorisieren und die LLM-Optimierungsmaßnahmen an der aktuellen Suchmethode der Benutzenden ausrichten. Darüber hinaus behalten Sie die volle Kontrolle, da Abfragen nie automatisch hinzugefügt werden und explizit ausgewählt werden müssen, bevor Sie zu aktiven Prompts werden.

### Funktionsweise {#how-it-works}

Der wichtigste zu berücksichtigende Aspekt bei der Integration von LLM Optimizer mit Google Search Console ist folgender: Anstatt manuell zu erraten, welche Kundschaften möglicherweise einen KI-Assistenten fragen, schauen wir uns an, wonach sie **bereits suchen** und wandeln diese echten Abfragen in natürliche, dialogorientierte Prompts um. Dieser Prozess der Umstellung von Suchabfragen auf KI-Prompts wird im folgenden Diagramm veranschaulicht.

![Prozessfluss](/help/dashboards/assets/diagram-flow.png)

Im Allgemeinen umfasst der Prozess fünf Schritte:

#### Schritt 1: Erfassen Ihrer echten Suchdaten {#gsc-one}

Der Prozess beginnt mit den Keywords, die Ihre Zielgruppe tatsächlich verwendet, um Ihre Website über Google zu finden. Dieser Rohdatensatz (oft Tausende von eindeutigen Abfragen) ist die Grundlage für alles, was folgt.

#### Schritt 2: Analysieren der Bedeutung und Filtern auf Sicherheit {#gsc-two}

Jede Abfrage wird auf ihre semantische Bedeutung analysiert (wonach die Person tatsächlich fragt) und mit einem Sicherheitsfilter geprüft, der unangemessene oder markenfremde Inhalte entfernt. Dadurch wird sichergestellt, dass nur angemessene, relevante Keywords weiterverwendet werden.

#### Schritt 3: Gruppieren nach Kategorien und Themen {#gsc-three}

Zugehörige Abfragen werden automatisch in **Kategorien** (allgemeine Geschäftsthemen) und **Themen** (fokussierte Unterthemen innerhalb jeder Kategorie) gruppiert. Das System priorisiert Kategorien, die bereits in Ihrem LLM Optimizer-Setup konfiguriert sind. Darüber hinaus können neue Kategorien angezeigt werden, die aus Ihren Suchdaten hervorgehen, aber noch nicht überwacht werden. Das folgende Diagramm zeigt ein Beispiel für Kategorien und Themen einer Möbelmarke:

![Möbelmarke](/help/dashboards/assets/diagram-example.png)

#### Schritt 4: Generieren von Prompts basierend auf echten Keywords {#gsc-four}

Für jedes Thema generiert das System Prompts, die der Art und Weise ähneln, wie echte Menschen mit KI-Assistenten kommunizieren. Jeder Prompt wird direkt von den tatsächlichen Suchbegriffen aus Google Search Console beeinflusst, wodurch die Keyword-Absicht in Fragen in natürlicher Sprache umgewandelt wird.

Dieser (auf Keywords basierende) Ansatz bedeutet:

* Prompts spiegeln eine reale Nachfrage wider, keine hypothetischen Fragen.
* Die Sprache spiegelt wider, wie Kundschaften Dinge tatsächlich formulieren.
* Die Abdeckung erstreckt sich über den gesamten Bereich dessen, wonach auf Ihrer Site gesucht wird.

Bei der Prompt-Generierung wird auch Ihr Markenprofil berücksichtigt, einschließlich Produkten, Konkurrenz, Branchenpositionierung und Zielgruppe, um sicherzustellen, dass Prompts kontextuell korrekt sind.

#### Schritt 5: Qualitätssicherung und Bereitstellung {#gsc-five}

Vor der Bereitstellung durchläuft jeder Prompt mehrere automatisierte Qualitätsprüfungen:

* Deduplizierung: Nahezu identische Prompts werden entfernt.
* Ausgleichen des Markenverhältnisses: Es wird für eine realistische Mischung gesorgt (~75 % ohne Branding, ~25 % mit Branding).
* Sprachliche Qualität: Künstlich klingende Formulierungen werden korrigiert, damit Prompts natürlich klingen.
* Konsistenzprüfungen: Daten werden validiert, Füllwörter werden entfernt und kurze Textlänge wird sichergestellt.

Darüber hinaus wird jeder Prompt mit der zugehörigen Kategorie, dem Thema, dem Absichtstyp und der Klassifizierung mit/ohne Branding versehen, damit LLM Optimizer mit dem Monitoring beginnen kann.

#### Prompt-Anatomie {#prompt-anatomy}

Nach Abschluss des obigen Prozesses weist jeder an LLM Optimizer gesendete Prompt die folgenden Attribute auf:

| Feld | Beschreibung |
|---------|----------|
| Text | Der Prompt, ähnlich wie eine Person ihn in einen KI-Assistenten eingeben würde. |
| Kategorie | Das diesem Prompt zugewiesene allgemeine Geschäftsthema. |
| Thema | Das konkrete Unterthema innerhalb der Kategorie. |
| Region | Der Zielmarkt (z. B. USA, Vereinigtes Königreich usw.). |
| Absicht | Die Benutzermentalität: informativ, vergleichend, transaktional, anweisend, planend oder delegiert. |
| Typ | Der Typ kann entweder Branding (erwähnt die Marke/Produkte) oder kein Branding (allgemeine Frage in Bezug auf eine Branche) aufweisen. |

### Informationen zur Verwendung {#how-to-use}

Gehen Sie wie folgt vor, um die Google Search Console-Abfragen in LLM Optimizer zu integrieren und zu verwenden.

#### Verbinden mit Google Search Console {#connect-console}

Bevor Sie diese Funktion verwenden können, müssen Sie Ihr Google Search Console-Konto mit LLM Optimizer integrieren.

1. Öffnen Sie das Dashboard **Kundenkonfiguration** (klassische Navigation) oder **Markenverwaltung** (markenorientierte Oberfläche) und navigieren Sie dann zur Google Search Console-Integration (GSC-Tag in der markenorientierten Oberfläche).
1. Navigieren Sie zur Registerkarte „Google Search Console“ und klicken Sie auf **Konto verbinden**.
   ![Google Search Console](/help/dashboards/assets/google-console.png)
1. Melden Sie sich mit einem Google-Konto an, das Zugriff auf die gewünschte Search Console-Eigenschaft hat.
   ![Google-Konto](/help/dashboards/assets/google-account.png)
1. Wählen Sie die Eigenschaft aus, die Sie verbinden möchten.
   ![Console-Eigenschaft](/help/dashboards/assets/console-property.png)
1. Nachdem die Verbindung hergestellt wurde, beginnt LLM Optimizer mit dem Abrufen relevanter Suchabfragen.
   ![Abrufen von Daten](/help/dashboards/assets/console-complete.png)

#### Überprüfen und Suchen von Abfragen {#search-query}

Nachdem Sie das Google Search Console-Konto in LLM Optimizer integriert haben, können Sie die Liste der Themen und Prompts überprüfen, die Sie aus der Suchkonsole beziehen, und die Prompts aus der Liste hinzufügen.

1. Überprüfen Sie auf der Registerkarte „Google Search Console“ die Liste der Themen und Prompts aus der Suchkonsole.
   ![Prompts-Liste](/help/dashboards/assets/prompts-list.png)
1. Klicken Sie auf das gewünschte Thema/die gewünschte Prompt-Kategorie, um die Liste zu erweitern.
1. Verwenden Sie die Schaltfläche **Hinzufügen**, um Prompts von der Liste hinzuzufügen. Sie können Prompts und Kategorien auch gesammelt hinzufügen, indem Sie **Alle hinzufügen** verwenden.
   ![Hinzufügen von Prompts](/help/dashboards/assets/add-prompts.png)
1. Wenn Sie mit der Auswahl zufrieden sind, klicken Sie in der Benachrichtigung auf **Speichern**.

#### Anzeigen hinzugefügter Abfragen in der Prompts-Liste {#prompts-list}

Nachdem eine Abfrage hinzugefügt wurde, wird sie auf der Registerkarte [Prompts](#prompts-brand) im Dashboard „Kundenkonfiguration“ (klassische Navigation) oder in der **Prompts-Verwaltung** (markenorientierte Oberfläche) angezeigt. Prompts aus Google Search Console werden mit einem Google Search Console-Symbol in der Spalte **Herkunft** gekennzeichnet. Dieses Symbol hilft bei der Unterscheidung zwischen Prompts, die auf dem tatsächlichen Suchverhalten der Benutzenden basieren, und Prompts, die manuell oder aus anderen Quellen hinzugefügt wurden.

### Häufig gestellte Fragen {#gsc-faq}

F: Wie oft werden Prompts im Dashboard „Google Search Console“ aktualisiert?

Prompts aus Google Search Console werden in der Regel einmal pro Monat aktualisiert. Bei jeder Aktualisierung werden die neuesten Suchabfragedaten aus Google Search Console abgerufen, die Generierungs-Pipeline wird erneut ausgeführt und das Prompt-Set wird aktualisiert. Dadurch wird sichergestellt, dass Ihre Prompts den aktuellen Such-Trends und saisonalen Veränderungen im Benutzerverhalten entsprechen.

F: Wie viele Prompts stammen normalerweise aus Google Search Console?

Die Anzahl hängt von der Größe Ihrer Bereitstellung und der Anzahl der verfolgten Kategorien ab. Beispiel:

| Kategorien | Themen insgesamt | Bereitgestellte Prompts |
|---------|----------|----------|
| 1–2 | 3–8 | ~65–180 |
| 4–5 | 12–20 | ~270–450 |
| 10 | 30–40 | ~675–900 |

Wir möchten Prompt-Sets bereitstellen, die die Qualitätsziele erfüllen, die während der Testphase und des Onboardings kommuniziert wurden: mindestens 20 Prompts pro Thema mit 3–4 Themen pro Kategorie und ein angemessenes Verhältnis zwischen Inhalten mit/ohne Branding.

F: Wie schnell nach Herstellen der Verbindung mit Google Search Console werden von Google Search Console bezogene Prompts angezeigt?

Prompts sind in der Regel **innerhalb weniger Stunden** nach Herstellen der Verbindung mit Google Search Console verfügbar. Die Pipeline ruft automatisch Ihre Suchdaten ab, führt die Generierungs- und Qualitätssicherungsschritte für sie durch und stellt LLM Optimizer das endgültige Prompt-Set bereit.

F: Wer kann eine Verbindung zu Google Search Console herstellen?

Alle mit Berechtigungen des Typs **Eigentümerin bzw. Eigentümer** oder **vollständigen Berechtigungen** für die Google Search Console-Eigenschaft können die Verbindung autorisieren. Dies sind die Berechtigungsstufen, die Lesezugriff auf Suchabfragedaten gewähren. Wenn Sie sich bezüglich Ihrer Berechtigungsstufe nicht sicher sind, können Sie sie unter **Einstellungen>Benutzende** und „Berechtigungen“ in Google Search Console überprüfen.

F: Kann ich Prompts als ignoriert oder übersprungen markieren, damit sie nicht in der Prompts-Liste von Google Search Console angezeigt werden?

Ja, Sie können jeden Prompt löschen, den Sie nicht überwachen möchten. Gelöschte Prompts werden aus Ihrer aktiven Prompts-Liste entfernt und im zukünftigen Reporting nicht mehr angezeigt. Wenn ein gelöschter Prompt bei einer nachfolgenden monatlichen Aktualisierung neu generiert wird, können Sie ihn erneut entfernen.

F: Wie schnell nach Hinzufügen von Prompts aus Google Search Console zu meiner Prompts-Liste werden Markenpräsenzdaten für diese Prompts angezeigt?

Markenpräsenzdaten für neu hinzugefügte Prompts werden bei der nächsten geplanten Datenaktualisierung angezeigt, die normalerweise zu Beginn jeder Woche ausgeführt wird. Je nachdem, wann Sie die Prompts hinzufügen, werden Ihnen innerhalb weniger Tage Ergebnisse angezeigt.
