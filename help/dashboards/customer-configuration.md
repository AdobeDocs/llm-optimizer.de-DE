---
title: Kundenkonfiguration
description: Verwenden Sie die Kundenkonfiguration, um festzulegen, wie Ihre Marke innerhalb der LLM Optimizer-Plattform überwacht und analysiert wird.
feature: Customer Configuration
autotag-review: '2026-07-15T17:48:20.742Z'
TQID: 'https://experienceleague.adobe.com/BvaFF-pMzojy1TNZvCQQRbcT5c5AQ75OqjclmDi14Z0'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c898dfb2-0885-42fb-b2af-b2d756752646id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 72cc645997dbd5ae0442fefad73fe6a4e7ffe050
workflow-type: tm+mt
source-wordcount: 3923
ht-degree: 56%

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
* [Eingabeaufforderungen basierend auf Zitatversuchen und Referral Traffic](#prompt-suggestions)

Wenn Sie die [markenorientierte Oberfläche](/help/overview/quick-start.md#brand-centric-experience) verwenden, navigieren Sie zu **Markenverwaltung**, um Marken, Markenaliasse und Konkurrenz einzurichten und zu konfigurieren, um anhand des Trackings mit diesen Vergleiche zu ziehen. Die **Markenverwaltung** wird auch verwendet, um Integrationen wie Google Search Console, Adobe Analytics und CDN-Protokollweiterleitung zu konfigurieren, die sich auf mit Marken verknüpfte URLs beziehen. Klicken Sie dazu auf die entsprechenden Registerkarten: GSC, CDN usw.

![Markenverwaltung - App-Navigation (Markenzentriertes Erlebnis)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Markenverwaltung - Konfigurationsübersicht (Markenzentriertes Erlebnis)](/help/assets/brand-centric-experience/brands-management-configuration.png)

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
1. Verwenden Sie die **Hinzufügen**, um Eingabeaufforderungen aus der Liste hinzuzufügen. Sie können Aufforderungen und Kategorien auch stapelweise hinzufügen, indem Sie **Alle hinzufügen** verwenden.
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

## Eingabeaufforderungen basierend auf Zitatversuchen und Referral Traffic {#prompt-suggestions}

Anstatt zu erraten, welche Eingabeaufforderungen wichtig sind **beginnen Sie** mit dem, auf was KI-Agenten und -Benutzer bereits auf Ihrer Site zugreifen oder auf was sie verwiesen werden.

Adobe LLM Optimizer analysiert Ihre CDN-Daten, um festzustellen, auf welche Seiten KI-Agenten bereits konsistent zugreifen (Zitierversuche) und Benutzer darauf verweisen (LLM-Referral Traffic). Danach werden automatisch Eingabeaufforderungsvorschläge basierend auf Lücken in der aktuellen Eingabeaufforderungsabdeckung generiert. Anstatt zu erraten, welche URLs priorisiert werden sollten und welche Aufforderungen zur Erstellung angezeigt werden, beginnt der Workflow mit echten Traffic-Signalen: Seiten, die Agenten bereits erreichen, und dann die Art der Benutzeraufforderungen definieren, die diese Seiten beantworten sollten.

Wenn eine Seite bereits konsistent von KI-Agenten aufgerufen wird, lautet die Frage nicht, wie Agenten über die Seite informiert werden, sondern welche Fragen der Seiteninhalt beantworten könnte. Ohne Eingabeaufforderungen, die für diese Seiten konfiguriert sind, haben Sie keine Einsicht in die Darstellung Ihrer Marke in KI-Antworten zu Themen, die am wichtigsten sind. Eingabeaufforderungsvorschläge von Agent Traffic schließen diese Lücke, damit Sie das Markensichtbarkeit für die Seiten verfolgen und verbessern können, auf denen Agenten bereits am aktivsten sind.

>[!NOTE]
>
> Im [markenorientierten Erlebnis](/help/overview/quick-start.md#brand-centric-experience) werden im Abschnitt **Eingabeaufforderungsverwaltung** Eingabeaufforderungsvorschläge angezeigt.

### Funktionsweise {#prompt-suggestions-how-it-works}

Der Workflow Vorschläge auffordern wird in vier Schritten ausgeführt, wodurch CDN-Traffic-Signale in konfigurationsbereite Eingabeaufforderungsvorschläge umgewandelt werden. Jeder Schritt baut auf dem vorherigen auf: von Seiten aus, auf denen die KI-Agentenaktivität bereits erwiesen ist, um zu verstehen, worum es bei diesen Seiten geht, zu überprüfen, was bereits abgedeckt ist, und um Eingabeaufforderungen zu generieren, die spezifisch, fundiert und zur Veröffentlichung bereit sind.

![Eingabeaufforderungen aus dem Agenten-Traffic-Workflow](/help/dashboards/assets/prompt-suggestions-workflow.png)

#### Schritt 1: Identifizieren von Seiten mit hohem Signalaufkommen im Agent-Traffic {#prompt-suggestions-step-1}

Die Pipeline beginnt damit, Seiten auf Ihrer Site zu identifizieren, mit denen KI-Systeme bereits aktiv interagieren, und zwar mithilfe von zwei Signalen aus Ihren CDN-Daten: Wie häufig greifen KI-Systeme auf Ihre Seiten als Quelle zu, während sie echte Benutzerfragen beantworten, und ob diese Seiten bereits reale Benutzer von KI-generierten Antworten auf Ihre Site bringen.

* **Zitierungsversuche** - Wie KI-Systeme beim Beantworten von Benutzerfragen auf eine Seite als potenzielle Quelle zugegriffen haben. Die Pipeline sucht nach Seiten, die Woche für Woche eine konsistente Aktivität des Zitatversuchs zeigen, was ein ganzheitlicheres Bild des Interesses als einen einzigen Zeitpunkt liefert.
* **LLM Referral Traffic** - Instanzen, in denen ein Benutzer von einer KI-generierten Antwort angeklickt hat, um zur URL zu gelangen. Die Pipeline konzentriert sich auf die neuesten Verweisdaten und priorisiert Seiten mit dem höchsten Volumen an KI-gesteuerten Besuchen, um sicherzustellen, dass Vorschläge auf aktuellen und bewährten KI-Empfehlungsmustern basieren.

| Signal | Bedeutung |
|--------|---------------|
| Nur Zitatversuche | Agenten greifen durchgängig als potenzielle Quelle auf diese Seite zu |
| Nur LLM-Referral Traffic | Agenten senden Benutzer aktiv zu dieser Seite |
| Beide | Agenten greifen darauf zu und Benutzer klicken durch - das Ziel mit der höchsten Konfidenz |

Eine Seite kann sich durch ein Signal oder beide qualifizieren. Seiten mit beiden Signalen stellen die Ziele mit der höchsten Konfidenz für die sofortige Generierung dar.

#### Schritt 2: Analysieren des Seiteninhalts und des Seiteninhalts {#prompt-suggestions-step-2}

Für jede qualifizierte Seite liest die Pipeline den Seiteninhalt und:

* **Fasst** in einer knappen, faktengestützten Beschreibung zusammen, die die Grundlage für alles wird, was folgt.
* **Klassifiziert** den Seitentyp, egal ob es sich um ein Produkt, eine Ressource, einen Support oder einen Hub handelt.
* Identifiziert den **primären Journey-Intent** - die Art von Frage, die die Seite am besten beantworten kann, z. B. informativ, anweisend, vergleichend oder transaktionale Fragen.

Die beiden Klassifizierungen arbeiten zusammen. Beispielsweise sind Eingabeaufforderungen, die von einer Support-Seite wie einem Einrichtungshandbuch oder Tutorial generiert werden, wahrscheinlich eher für eine vorhandene Benutzerrolle relevant als für eine neue Zielgruppe.

#### Schritt 3: Überprüfen der bestehenden Eingabeaufforderungsabdeckung {#prompt-suggestions-step-3}

Bevor Sie neue Elemente generieren, prüft die Pipeline, ob jede qualifizierte Seite bereits von Eingabeaufforderungen abgedeckt ist, die in Ihrem LLM Optimizer-Konto konfiguriert sind. Sie wird in zwei Durchgängen ausgeführt:

1. Ein semantischer Ähnlichkeitstest, der schnell mögliche Eingabeaufforderungen aus Ihrer vorhandenen Eingabeaufforderungsbibliothek identifiziert, die möglicherweise mit der Seite in Verbindung stehen.
2. Eine LLM-gestützte Überprüfung, die bewertet, wie gut jede Eingabeaufforderung mit dem Seiteninhalt übereinstimmt - nicht nur, ob es sich um einen thematischen Zusammenhang handelt, sondern auch, ob er abdeckt, worum es auf der Seite geht.

Eine Seite gilt als abgedeckt, wenn mindestens eine vorhandene Eingabeaufforderung diesen Schwellenwert erreicht. Seiten ohne angemessene Übereinstimmung werden als Lücken identifiziert und mit Schritt 4 fortgefahren.

#### Schritt 4: Generieren, Qualitätsprüfung und Sortierung der Eingabeaufforderungen nach URL {#prompt-suggestions-step-4}

![Schnelle Generierung und Qualitätsprüfung](/help/dashboards/assets/prompt-suggestions-generation.png)

Für jede Lückenseite generiert die Pipeline natürliche Eingabeaufforderungen, die darauf basieren, worum es bei dem Seiteninhalt geht. Es beginnt mit der Identifizierung relevanter Personen - jemand, der realistischerweise Fragen stellen würde, die auf dieser Seite beantwortet werden, und der ein realistisches Szenario um diese Rolle herum aufbaut, bevor er Eingabeaufforderungen für Kandidaten generiert.

Jede Eingabeaufforderung durchläuft eine automatisierte Qualitätsüberprüfung in drei Dimensionen:

* Ob sie **spezifisch** für diese Seite ist und nicht eine generische Frage, die für jede Seite in der Kategorie gelten könnte.
* Ob sie **im** Inhalt der Seite begründet ist.
* Ob es nach etwas klingt, **ein „echter Benutzer** in ein KI-Tool wie ChatGPT eingeben würde.

Eingabeaufforderungen, die diese Überprüfung nicht bestehen, werden mit spezifischem Feedback neu geschrieben und erneut überprüft. Wenn sie immer noch nicht bestehen, werden sie verworfen.

Der letzte Schritt ist eine Diversitätsprüfung, bei der Eingabeaufforderungen für URLs, die einander zu ähnlich sind, aus der endgültigen Liste entfernt werden. Jede Eingabeaufforderung ist mit Ihrem vorkonfigurierten Thema und Ihrer vorkonfigurierten Kategorie versehen und enthält ein Feld zur Begründung, in dem erläutert wird, warum die Quell-URL aufgrund ihres Zitatversuchs und der Referral Traffic-Signale als Ziel ausgewählt wurde. Eingabeaufforderungen wird ebenfalls eine Prioritätsreihenfolge zugewiesen, sodass Sie wissen, bei welchen Vorschlägen Sie zuerst handeln müssen. Eine höhere Priorität bedeutet ein stärkeres kombiniertes KI-Signal von der Quell-URL. Eingabeaufforderungen können dann auf der Registerkarte **Eingabeaufforderungen** im Dashboard für die Kundenkonfiguration überprüft werden.

### Informationen zur Verwendung {#prompt-suggestions-how-to-use}

1. Öffnen Sie das Dashboard **Kundenkonfiguration** und navigieren Sie zur Registerkarte **Vorschläge auffordern**.
1. Verwenden Sie den **Source**-Filter, um **Zitierungsversuch** auszuwählen, um Vorschläge anzuzeigen, die aus Agentendatenverkehr generiert wurden.
1. Überprüfen Sie die Spalten **Argumentation** und **Priorität**, um jeden Vorschlag auszuwerten.
1. Wählen Sie die Eingabeaufforderungen aus, die Sie hinzufügen möchten, und klicken Sie auf **Auswahl hinzufügen**, um sie zu Ihren konfigurierten Eingabeaufforderungen hinzuzufügen.

![Registerkarte „Vorschläge auffordern“ mit dem Quellfilter für Zitationsversuche](/help/dashboards/assets/prompt-suggestions-citation-attempt.png)

![Ausgewählte Eingabeaufforderungsvorschläge hinzufügen](/help/dashboards/assets/prompt-suggestions-add-selection.png)

### Häufig gestellte Fragen {#prompt-suggestions-faq}

F.: Benötigt mein Unternehmen eine zusätzliche Konfiguration, um diese Funktion verwenden zu können?

Diese Funktion beruht auf CDN-Protokolldaten. Wenn Sie „CDN[Protokollweiterleitung“ bereits aktiviert ](#cdn-configuration), ist keine zusätzliche Einrichtung erforderlich. Ohne CDN-Protokolle sind keine Daten zu Zitierversuchen oder Referral Traffic für die Analyse verfügbar.

F: Warum wird in den Vorschlägen keine bestimmte URL angezeigt?

Es gibt einige gemeinsame Gründe. Die Seite weist möglicherweise noch keine konsistente KI-Abrufaktivität oder aussagekräftiges Referral Traffic auf. Ohne eines dieser Signale gelangt sie nicht in die Pipeline. Möglicherweise wird sie bereits von einer vorhandenen konfigurierten Eingabeaufforderung abgedeckt, da die Pipeline nur Vorschläge für echte Lücken generiert. Oder der Seitentyp ist möglicherweise nicht für die Eingabeaufforderungsgenerierung geeignet.

F: Können sich die Vorschläge im Laufe der Zeit ändern?

Ja. Die Pipeline wird regelmäßig ausgeführt, sobald neue CDN-Daten verfügbar werden. Im Zuge der Weiterentwicklung des Benutzer- und Agentenverhaltens (welche Seiten aufgerufen werden, wie oft und welche Referral Traffic verursachen) spiegeln die Vorschläge diese Änderungen wider. Seiten, die zuvor noch kein hohes Signal hatten, können sich in zukünftigen Läufen qualifizieren und bestehende Lücken, die behoben wurden, werden keine neuen Vorschläge mehr erzeugen.

F: Warum sehe ich URLs, die ich nicht in den Vorschlägen erwartet hätte?

Die angezeigten URLs basieren ausschließlich auf beobachtetem agentischem Verhalten - Seiten, auf die KI-Systeme konsistent zugegriffen haben oder auf die Benutzer verwiesen wurden, unabhängig davon, wie prominent sie in Ihrer Inhaltsstrategie angezeigt werden. In einigen Fällen kann es sich um Seiten handeln, die Sie nie für wichtig gehalten haben, die aber wiederholt von KI erreicht wurden. Wenn eine URL in den Vorschlägen angezeigt wird, liegt dies daran, dass sie von den Daten unterstützt wird. Es steht Ihnen immer frei, Vorschläge zu ignorieren, die nicht zu Ihrer Strategie passen, aber die Daten hinter jedem Vorschlag basieren auf echter KI-Aktivität.

F: Was bedeutet das Feld der Argumentation?

Jede Eingabeaufforderung enthält eine Erklärung, warum die Quell-URL als Vorschlag aufgeführt wurde. Bei Seiten, die sich durch Zitatversuche qualifizieren, wird gezeigt, wie die Seite basierend auf wöchentlichen Versuchen unter allen Seiten rangiert, auf die zugegriffen wird. Für Seiten, die sich durch Referral Traffic qualifizieren, wird dasselbe für Verweisseitenansichten angezeigt. Seiten mit beiden Signalen zeigen beides an. Auf diese Weise können Sie die Priorität verstehen und auswählen, welche Vorschläge zuerst veröffentlicht werden sollen.

Für eine Seite mit beiden Signalen könnte die Begründung wie folgt aussehen: *Generiert für [Seiten-URL] — rangiert unter den besten 3 % nach dem Median der wöchentlichen Zitatversuche und unter den besten 1 % nach LLM-Referral Traffic.*

F: Wie wird die Priorität bestimmt?

Die Priorität basiert auf einem kombinierten Score aus zwei Signalen: Wie eine Seite nach Zitierungsversuchen und wie sie nach LLM-Verweisseitenansichten unter allen Seiten rangiert. Beide werden als Perzentile ausgedrückt und addiert, sodass Seiten, die bei beiden Signalen stark punkten, auf natürliche Weise an die Spitze aufsteigen. Eine Seite, auf die KI konsistent zugreift und zu der Benutzer aktiv sendet, rangiert immer höher als eine Seite mit nur einem Signal.

F.: Wie entscheidet die Pipeline anhand von Zitatversuchen, welche Seiten qualifiziert sind?

Die Pipeline sucht nach Seiten, die im Laufe der Zeit eine konsistente KI-Abrufaktivität aufweisen. Um qualifiziert zu sein, muss eine Seite zwei Bedingungen erfüllen: Sie muss in mindestens der Hälfte der Wochen eine aussagekräftige Aktivität in den verfügbaren Daten aufweisen, und ihre mediane Anzahl an agenten Treffern während dieser aktiven Wochen muss auf allen Seiten unter den besten 25 % rangieren. Beide Bedingungen müssen zutreffen - die Häufigkeit allein ist nicht ausreichend und das Treffervolumen allein ist ebenfalls nicht ausreichend.

F.: Wie entscheidet die Pipeline, welche Seiten basierend auf Referral Traffic qualifiziert sind?

Eine Seite qualifiziert sich, wenn sie in den letzten drei Monaten unter den besten 10 % aller Seiten nach Gesamtzahl der LLM-Empfehlungsbesuche erscheint. Dadurch wird sichergestellt, dass Vorschläge auf Seiten basieren, die bereits echte, messbare Clickthroughs aus KI-Antworten generieren, die auf aktuellem Verhalten basieren.

F.: Sind Vorschläge in anderen Sprachen als Englisch verfügbar?

Noch nicht. Die Pipeline generiert derzeit nur Eingabeaufforderungen in englischer Sprache. In einer zukünftigen Version wird Unterstützung für mehrere Sprachen hinzugefügt.
