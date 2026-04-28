---
title: Agent-Traffic-Fehler
description: Erfahren Sie, wie LLM Optimizer HTTP-Fehler erkennt, die von auf Ihre Site crawlen KI-Agenten auftreten, und wie Sie diese beheben können, um die Barrierefreiheit der Inhalte und die Sichtbarkeit der KI zu verbessern.
feature: Opportunities
source-git-commit: 101a0582a5112c7fdf1871a938b773b7159a9d4c
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---


# Agent-Traffic-Fehler

KI-Agenten, die Ihre Site crawlen haben, stoßen auf dieselben HTTP-Fehler wie menschliche Browser, die Folgen sind jedoch anders. Wenn ein KI-Agent auf einen 404-, 403- oder 5xx-Fehler trifft, kann er nicht auf diese Inhalte zugreifen oder sie zitieren, was die Sichtbarkeit Ihrer Marke in KI-generierten Antworten direkt beeinträchtigt.

Die Opportunity „Agent Traffic Errors“ überwacht Ihre CDN-Protokolle auf HTTP-Fehler, die an KI-Agenten zurückgegeben werden, und zeigt die betroffenen URLs zusammen mit ihren Treffervolumen und Fix-Vorschlägen an. Es werden drei Fehlertypen behandelt - jeder mit seiner eigenen Opportunity im Dashboard:

- **404 Nicht gefunden** - Fehlerhafte Links, die KI-Agenten am Zugriff auf Inhalte hindern, die nicht mehr unter der erwarteten URL vorhanden sind.
- **403 Verboten** - Zugriffsbeschränkungen, die KI-Crawler von Inhalten abhalten, die sie erreichen sollten.
- **5xx Server Errors** - Instabilität auf Serverseite, durch die Inhalte vorübergehend oder dauerhaft für KI-Agenten nicht verfügbar sind.

Je nachdem, welche Fehler für Ihre Site erkannt werden, kann jeder Fehlertyp als separate Möglichkeit im Dashboard angezeigt werden.

Die Opportunity zeigt außerdem zwei Schlüsselmetriken für jeden Fehlertyp:

- **URLs insgesamt** - Anzahl der eindeutigen URLs, die Fehler an KI-Agenten zurückgeben.
- **Treffer insgesamt** - Gesamtzahl der Fehlerantworten, die für alle KI-Agentenanfragen aufgezeichnet wurden.

![Dashboard für Agentenbezogene Traffic-Fehler mit Zusammenfassungsmetriken und Fehlerdetails](/help/dashboards/opportunities/assets/agentic-traffic-errors-overview.png)

## Funktionsweise

LLM Optimizer fragt Ihre CDN-Protokolle über Athena ab, um URLs zu identifizieren, die 404-, 403- oder 5xx-Status-Codes an KI-Agent-Benutzeragenten zurückgeben. Zu den Benutzeragenten gehören ChatGPT, Claude, Perplexity und Gemini. Pro Audit werden bis zu 500 URLs analysiert und nach Traffic-Volumen sortiert. Die Prüfung wird standardmäßig wöchentlich ausgeführt.

URLs werden vor dem Aufdecken validiert, um falsch positive und veraltete Daten herauszufiltern. LLM Optimizer testet jede URL erneut, um ihren aktuellen Status zu bestätigen, und vergleicht die Antworten des KI-Agenten mit den Antworten des menschlichen Browsers, um Crawler-spezifische Probleme zu identifizieren.

Bei **404** Fehlern sind Vorschläge KI-gestützt. Daher analysiert LLM Optimizer die Struktur und den Inhalt der fehlerhaften URL, um alternative URLs zu empfehlen, die die Benutzerabsicht beibehalten, und fügt einen Konfidenzwert und eine Begründung hinzu, die die Empfehlung erklärt.

Bei **403- und 5xx** Fehlern sind die Vorschläge vorlagenbasiert und bieten zielgerichtete Anleitungen für jeden Fehlertyp.

## Tabelle mit Fehlerdetails

Die Tabelle mit Fehlerdetails enthält alle betroffenen URLs, gefiltert nach **Benutzeragent**, **Länder-Code** und **Kategorie**. Für jede angezeigte URL gilt:

- **URL** - Die betroffene Seite.
- **Total** - Gesamtzahl der Fehlertreffer von KI-Agenten.
- Wöchentliche Trefferanzahl für die letzten Wochen, damit Sie verfolgen können, ob das Problem persistent ist oder sich verbessert hat.

![Fehlerdetailtabelle mit Filtern und wöchentlichen Trefferspalten](/help/dashboards/opportunities/assets/agentic-traffic-errors-table.png)

## Details des Vorschlags

Wenn Sie auf einen Vorschlag klicken, wird ein Bedienfeld **Vorschlagsdetails** geöffnet, das Folgendes anzeigt:

- Die betroffene URL und die empfohlene Aktion - zum Beispiel „Sollte eine gültige URL sein oder zu einer alternativen URL umgeleitet werden“.
- Ein **Statistiken**-Diagramm, das die Gesamtzahl der Treffer pro Woche durch den KI-Agenten-Benutzeragenten anzeigt, sodass Sie die Auswirkungen des Traffics verstehen können und feststellen können, ob das Problem persistent ist oder sich verbessert.
- **Freigeben** und **Verwerfen** Aktionen zur Verwaltung des Vorschlags.

![Bedienfeld „Vorschlagsdetails“ für ein 404-Diagramm mit Statistiken](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion.png)

In einigen **5xx**-Fällen (und ähnlichen Fällen) kann das Bedienfeld Folgendes feststellen, wenn keine alternativen URLs für dieselbe Domain verfügbar sind, und erklären, wie die Empfehlungen den Domain- und Listenregeln folgen. Beispielsweise den Vorschlag, die Basis-Domain-URL zu verwenden, um den SEO-Wert beizubehalten, wenn keine engere Übereinstimmung angeboten werden kann.

![Bedienfeld „Vorschlagsdetails“ für einen Server-Fehler mit erläuternder Meldung](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion-503.png)

## Fehlerbehebung

Die Fehlerbehebung hängt vom Fehlertyp ab:

**404-Fehler** - Der Vorschlag enthält eine oder mehrere alternative URLs, die von KI empfohlen werden und auf der Struktur und dem Inhalt der fehlerhaften URL basieren, sowie einen Konfidenzwert und eine Begründung. Implementieren Sie eine Server-seitige Umleitung von der fehlerhaften URL zur vorgeschlagenen Alternative, um den Zugriff des KI-Agenten wiederherzustellen und die Auffindbarkeit der Inhalte beizubehalten.

**403-Fehler** - Überprüfen Sie die Zugriffsberechtigungen, um sicherzustellen, dass KI-Crawler nicht durch Inhalte blockiert werden, auf die sie zugreifen können sollten. Insbesondere gilt:
- Zugriffsberechtigungen überprüfen - KI-Crawler blockiert.
- Stellen Sie sicher, dass die Sicherheitseinstellungen keine legitimen Crawler blockieren.

**5xx-Fehler** - Untersuchen Sie Server-seitige Probleme, die sich auf die gekennzeichneten Seiten auswirken. Insbesondere gilt:
- Serverstabilität für Seiten mit hohem Traffic untersuchen.
- Überprüfen Sie die Anwendungsprotokolle auf wiederkehrende Fehler.
- Überwachen des Zustands und der Kapazität der Infrastruktur.

## In der Demo ausprobieren

Sehen Sie sich die Opportunity „Agent Traffic Errors“ in Aktion an, indem Sie die Demo-Umgebung von Frescopa verwenden.

- [404-Fehler in der Frescopa-Demo anzeigen](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-4xxs)
- [5xx Fehler in der Frescopa-Demo anzeigen](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-5xxs)

## Häufig gestellte Fragen

**Warum sind HTTP-Fehler für die Sichtbarkeit der KI wichtig?**

In Systemen, die den Abruf erweitern, entdecken KI-Crawler Links und versuchen, Seiteninhalte abzurufen, die in ihre Antworten aufgenommen werden sollen. Wenn eine Seite fehlt, einen Fehler zurückgibt oder nicht zugänglich ist, kann ihr Inhalt nicht abgerufen oder zitiert werden. Durch die direkte Behebung dieser technischen Fehler erhöht sich die Wahrscheinlichkeit, dass Ihre Inhalte erfolgreich indiziert und von KI-Systemen zitiert werden.

**Was ist der Unterschied zwischen einem 404- und einem 403-Fehler?**

Ein 404-Fehler bedeutet, dass die Seite an der angeforderten URL nicht vorhanden ist - sie wurde entweder gelöscht oder ohne Umleitung verschoben. Ein 403-Fehler bedeutet, dass die Seite zwar vorhanden ist, der Zugriff jedoch verweigert wird, entweder für alle Crawler oder speziell für KI-Agenten. Beide verhindern, dass KI-Agenten auf Ihre Inhalte zugreifen, aber die Fehlerbehebung ist für jeden unterschiedlich.

**Warum kann ein 403-Fehler nur KI-Agenten betreffen und nicht menschliche Besucher?**

Einige Sicherheitskonfigurationen oder Einstellungen für die Zugriffssteuerung blockieren möglicherweise den Zugriff von Benutzeragenten des KI-Agenten auf Inhalte, auf die Besuchende normalerweise zugreifen können. LLM Optimizer kennzeichnet diese Fälle speziell durch den Vergleich der Antworten des KI-Agenten mit den Antworten menschlicher Browser.

**Wie werden falsch-positive Ergebnisse herausgefiltert?**

LLM Optimizer testet URLs erneut, um ihren aktuellen Status zu bestätigen, bevor sie als Vorschläge angezeigt werden, und vergleicht KI-Agentenantworten mit menschlichen Browser-Antworten, um Crawler-spezifische Probleme zu identifizieren. URLs, die keine Fehler mehr zurückgeben, werden nicht angezeigt.

**Wie oft wird die Analyse aktualisiert?**

Die Prüfung wird standardmäßig wöchentlich ausgeführt, wobei Fehlerdaten aus den CDN-Protokollen der Vorwoche abgerufen werden. Die Tabelle mit Fehlerdetails zeigt die wöchentliche Trefferanzahl an, sodass Sie Trends im Zeitverlauf verfolgen können.

**Welche KI-Agenten werden überwacht?**

LLM Optimizer überwacht Fehlerantworten von allen erkannten Benutzeragentenmustern für KI-Agenten, einschließlich: ChatGPT, Claude, Perplexity und Gemini-Crawler.
