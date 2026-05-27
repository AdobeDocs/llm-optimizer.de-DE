---
title: Fehler im Zusammenhang mit Agent-basiertem Traffic
description: Erfahren Sie, wie LLM Optimizer HTTP-Fehler erkennt, die für AI Agents beim Crawling Ihrer Site auftreten, und wie Sie diese beheben, um die Barrierefreiheit von Inhalten und die KI-Sichtbarkeit zu verbessern.
feature: Opportunities
autotag-review: '2026-05-15T17:32:31.900Z'
TQID: 'https://experienceleague.adobe.com/9Gbva-14SNt8A0G0B2Qu26OOp34L5NaM0z6lCv4yrTg'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: e06fae5f-830b-4222-a469-b5e148d36465
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1045
ht-degree: 100%

---


# Fehler im Zusammenhang mit Agent-basiertem Traffic

Beim Crawling Ihrer Site treten für AI Agents dieselben HTTP-Fehler auf wie für menschliche Suchende, jedoch unterscheiden sich die Konsequenzen. Wenn ein AI Agent auf einen 404-, 403- oder 5xx-Fehler stößt, kann er nicht auf diese Inhalte zugreifen oder sie zitieren, was die Sichtbarkeit Ihrer Marke in KI-generierten Antworten direkt beeinträchtigt.

Die Möglichkeit „Fehler im Zusammenhang mit Agent-basiertem Traffic“ überwacht Ihre CDN-Protokolle auf HTTP-Fehler, die an AI Agents zurückgegeben werden, und zeigt die betroffenen URLs zusammen mit ihren Treffervolumen und Korrekturvorschlägen an. Es werden drei Fehlertypen abgedeckt, jeder mit seiner eigenen Möglichkeit im Dashboard:

- **404 Nicht gefunden**: Fehlerhafte Links, die AI Agents am Zugriff auf Inhalte hindern, die nicht mehr unter der erwarteten URL vorhanden sind.
- **403 Verboten**: Zugriffsbeschränkungen, die KI-Crawler von Inhalten ausschließen, die sie eigentlich erreichen können sollten.
- **5xx Server-Fehler**: Server-seitige Instabilität, durch die Inhalte vorübergehend oder dauerhaft für AI Agents nicht verfügbar sind.

Je nachdem, welche Fehler für Ihre Site festgestellt werden, kann jeder Fehlertyp als separate Möglichkeit im Dashboard angezeigt werden.

Die Möglichkeit zeigt außerdem zwei Schlüsselmetriken für jeden Fehlertyp an:

- **URLs insgesamt**: Anzahl der eindeutigen URLs, die Fehler an AI Agents zurückgeben.
- **Treffer insgesamt**: Gesamtanzahl der Fehlerantworten, die für alle Anfragen von AI Agents verzeichnet wurden.

![Dashboard für Fehler im Zusammenhang mit Agent-basiertem Traffic mit zusammenfassenden Metriken und Fehlerdetails](/help/dashboards/opportunities/assets/agentic-traffic-errors-overview.png)

## Funktionsweise

LLM Optimizer fragt Ihre CDN-Protokolle über Athena ab, um URLs zu ermitteln, die 404-, 403- oder 5xx-Status-Codes an AI-Agent-Benutzer-Agents zurückgeben. Zu den Benutzer-Agents gehören ChatGPT, Claude, Perplexity und Gemini. Pro Audit werden bis zu 500 URLs analysiert und nach Traffic-Volumen sortiert. Das Audit wird standardmäßig wöchentlich ausgeführt.

URLs werden überprüft, bevor sie angezeigt werden, um falsch positive Ergebnisse und veraltete Daten herauszufiltern. LLM Optimizer testet jede URL zum Bestätigen ihres aktuellen Status erneut und vergleicht die Antworten für AI Agents mit den Antworten für menschliche Suchende, um Crawler-spezifische Probleme zu identifizieren.

Bei **404-Fehlern** sind Vorschläge KI-gestützt. Daher analysiert LLM Optimizer die Struktur und den Inhalt der fehlerhaften URL, um alternative URLs zu empfehlen, die die Benutzerabsicht beibehalten, und fügt zum Erklären der Empfehlung einen Konfidenzwert und eine Begründung hinzu.

Bei **403- und 5xx-Fehlern** sind die Vorschläge vorlagenbasiert und bieten zielgerichtete Anleitungen für jeden Fehlertyp.

## Tabelle mit Fehlerdetails

Die Tabelle mit Fehlerdetails enthält alle betroffenen URLs, gefiltert nach **Benutzer-Agent**, **Länder-Code** und **Kategorie**. Für jede URL wird Folgendes angezeigt:

- **URL**: Die betroffene Seite.
- **Insgesamt**: Gesamtanzahl der Fehlertreffer von AI Agnents.
- Wöchentliche Trefferanzahl für die letzten Wochen, damit Sie nachverfolgen können, ob das Problem andauert oder sich verbessert.

![Tabelle mit Fehlerdetails mit Filtern und Spalten für wöchentliche Treffer](/help/dashboards/opportunities/assets/agentic-traffic-errors-table.png)

## Details des Vorschlags

Wenn Sie auf einen Vorschlag klicken, wird das Panel **Details des Vorschlags** geöffnet, das Folgendes anzeigt:

- Die betroffene URL und die empfohlene Aktion, zum Beispiel „Sollte eine gültige URL sein oder zu einer alternativen URL umleiten“.
- Ein Diagramm mit **Statistiken**, das die Gesamtanzahl der Treffer pro Woche durch den AI-Agent-Benutzer-Agent anzeigt, sodass Sie die Auswirkungen des Traffics verstehen und feststellen können, ob das Problem andauert oder sich verbessert.
- Die Aktionen **Freigeben** und **Verwerfen** zum Verwalten des Vorschlags.

![Panel „Details des Vorschlags“ für einen 404-Fehler mit Diagramm mit Statistiken](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion.png)

In einigen **5xx**-Fällen (und ähnlichen Fällen) wird im Panel möglicherweise darauf hingewiesen, wenn keine alternativen URLs derselben Domain verfügbar sind, und es wird erklärt, wie Empfehlungen die Domain- und Listenregeln befolgen. Beispielsweise der Vorschlag, dass die Basis-Domain-URL den SEO-Wert aufrechterhält, wenn keine passendere Übereinstimmung bereitgestellt werden kann.

![Panel „Details des Vorschlags“ für einen Server-Fehler mit erläuternder Meldung](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion-503.png)

## Fehlerbehebung

Die Fehlerbehebung hängt vom Fehlertyp ab:

**404-Fehler**: Der Vorschlag enthält eine oder mehrere alternative URLs, die von KI empfohlen werden und auf der Struktur und dem Inhalt der fehlerhaften URL basieren, sowie einen Konfidenzwert und eine Begründung. Implementieren Sie eine Server-seitige Umleitung von der fehlerhaften URL zur vorgeschlagenen Alternative, um den Zugriff des AI Agents wiederherzustellen und die Auffindbarkeit der Inhalte aufrechtzuerhalten.

**403-Fehler**: Überprüfen Sie die Zugriffsberechtigungen, um sicherzustellen, dass KI-Crawler nicht von Inhalten ausgeschlossen werden, auf die sie zugreifen können sollten. Insbesondere gilt:
- Überprüfen Sie Zugriffsberechtigungen – KI-Crawler blockiert.
- Stellen Sie sicher, dass die Sicherheitseinstellungen keine zulässigen Crawler blockieren.

**5xx-Fehler**: Untersuchen Sie Server-seitige Probleme, die sich auf die markierte Seiten auswirken. Insbesondere gilt:
- Überprüfen Sie die Server-Stabilität für Seiten mit hohem Traffic-Aufkommen.
- Überprüfen Sie die Anwendungsprotokolle auf wiederkehrende Fehler.
- Überwachen Sie den Zustand und die Kapazität der Infrastruktur.

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „Fehler im Zusammenhang mit Agent-basiertem Traffic“ in der Frescopa-Demoumgebung aus.

- [404-Fehler in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-4xxs)
- [5xx-Fehler in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-5xxs)

## Häufig gestellte Fragen

**Warum sind HTTP-Fehler für die KI-Sichtbarkeit relevant?**

In Systemen mit erweiterter Abfragefunktion entdecken KI-Crawler Links und versuchen, Seiteninhalte abzurufen, um sie in ihre Antworten einzubeziehen. Wenn eine Seite fehlt, einen Fehler zurückgibt oder nicht zugänglich ist, kann ihr Inhalt nicht abgerufen oder zitiert werden. Durch die Behebung dieser technischen Fehler erhöht sich die Wahrscheinlichkeit direkt, dass Ihre Inhalte von KI-Systemen erfolgreich indexiert und zitiert werden.

**Was ist der Unterschied zwischen einem 404- und 403-Fehler?**

Ein 404-Fehler bedeutet, dass die Seite unter der angeforderten URL nicht existiert. Sie wurde entweder gelöscht oder ohne Umleitung verschoben. Ein 403-Fehler bedeutet, dass die Seite existiert, der Zugriff jedoch verweigert wird, entweder für alle Crawler oder speziell für AI Agents. Beides verhindert, dass AI Agents auf Ihre Inhalte zugreifen, die Lösung ist jedoch jeweils unterschiedlich.

**Warum betrifft ein 403-Fehler möglicherweise nur AI Agents und nicht menschliche Besuchende?**

Bestimmte Sicherheitskonfigurationen oder Zugriffssteuerungseinstellungen können dazu führen, dass AI-Agent-Benutzer-Agents von Inhalten ausgeschlossen werden, auf die menschliche Besuchende normal zugreifen können. LLM Optimizer ermittelt diese Fälle durch Vergleichen von Antworten für AI Agents mit Antworten für menschliche Suchende gezielt.

**Wie werden falsch positive Ergebnisse herausgefiltert?**

LLM Optimizer testet URLs vor dem Anzeigen von Vorschlägen zum Bestätigen ihres aktuellen Status erneut und vergleicht die Antworten für AI Agents mit den Antworten für menschliche Suchende, um Crawler-spezifische Probleme zu identifizieren. URLs, die keine Fehler mehr zurückgeben, werden nicht angezeigt.

**Wie oft wird die Analyse aktualisiert?**

Das Audit wird standardmäßig wöchentlich durchgeführt und ruft Fehlerdaten aus den CDN-Protokollen der Vorwoche ab. Die Tabelle mit Fehlerdetails zeigt die wöchentlichen Trefferzahlen an, sodass Sie Trends im Laufe der Zeit nachverfolgen können.

**Welche AI Agents werden überwacht?**

LLM Optimizer überwacht Fehlerantworten für alle erkannten AI-Agent-Benutzer-Agent-Muster, einschließlich ChatGPT, Claude, Perplexity und Gemini Crawler.
