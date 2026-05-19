---
title: Durch robots.txt blockierter Traffic
description: Erfahren Sie, wie LLM Optimizer erkennt, wenn Ihre robots.txt-Datei AI Agents am Zugriff auf Ihren Inhalt hindert, und wie Sie dies beheben können.
feature: Opportunities
autotag-review: '2026-05-15T18:00:25.453Z'
TQID: 'https://experienceleague.adobe.com/9LGbxeIbWYZp-MN5Zww6g-dQ6BZT0IWzlA7XB-2Xlho'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 817
ht-degree: 100%

---


# Durch robots.txt blockierter Traffic

Ihre `robots.txt`-Datei steuert, welche Crawler auf Ihre Site zugreifen können. Wenn AI Agents selektiv für Inhalte blockiert werden, auf die allgemeine Crawler ansonsten zugreifen können, können diese Agents diese Inhalte nicht indizieren oder zitieren, was die Sichtbarkeit Ihrer Marke in KI-generierten Antworten direkt beeinträchtigt.

Die Möglichkeit „Durch robots.txt blockierter Traffic“ analysiert Ihre `robots.txt`-Datei im Kontext Ihrer Top-Seiten und identifiziert Regeln, die AI Agents am Zugriff auf Inhalte hindern, die sie erreichen sollten. Ergebnisse werden auf einzelner `robots.txt`-Zeilenebene angezeigt, sodass Sie bestimmte Anweisungen überprüfen und aktualisieren können, anstatt die gesamte Datei manuell überprüfen zu müssen.

Es werden zwei Schlüsselmetriken auf einen Blick angezeigt:

- **URLs insgesamt**: Anzahl der URLs, die von Blockierungsregeln in Ihrer `robots.txt`-Datei betroffen sind.
- **Blockierte Agents**: Anzahl der AI Agents, die am Zugriff auf diese URLs gehindert werden.

![Dashboard „Durch robots.txt blockierter Traffic“](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Funktionsweise

LLM Optimizer ruft Ihre `robots.txt`-Datei ab und vergleicht Ihre Top-Seiten mit sechs wichtigen AI-Agents-Benutzer-Agents:

- ClaudeBot
- GPTBot
- OAI-SearchBot
- OAI-User
- PerplexityBot
- Perplexity-User

Eine URL wird nur markiert, wenn **der Zugriff für einen Platzhalter-Benutzer-Agent (`*`) zugelassen wird, aber für einen bestimmten AI Agent blockiert wird**. Eine pauschale Blockierung, bei der alle Crawler gleichermaßen eingeschränkt sind, wird nicht gemeldet. Das Audit zielt speziell auf den selektiven Ausschluss von AI Agents ab, was das verwertbarste Ergebnis für GEO darstellt.

>[!NOTE]
>Bei dieser Möglichkeit wird keine KI für die Entwicklung oder Bereitstellung von Vorschlägen verwendet. Die Ergebnisse basieren vollständig auf der direkten Analyse Ihrer `robots.txt`-Datei.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **robots.txt** und **Details zum blockierten Traffic nach Agent**.

## robots.txt

Auf dieser Registerkarte wird Ihre vollständige `robots.txt`-Datei angezeigt, wobei die blockierten Anweisungen rot hervorgehoben sind. Jede hervorgehobene Zeile steht für eine Regel, die selektiv einen oder mehrere AI Agents am Zugriff auf eine URL hindert, die ansonsten öffentlich zugänglich ist.

![Ansicht von robots.txt mit hervorgehobenen blockierten Anweisungen](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Durch Klicken auf eine hervorgehobene Anweisung werden weitere Informationen über ihre Auswirkungen und die vorgeschlagene Fehlerbehebung angezeigt.

## Details zum blockierten Traffic nach Agent

Diese Registerkarte enthält eine Aufschlüsselung des blockierten Traffics, der nach AI Agent organisiert ist. Für jeden blockierten Agent wird Folgendes angezeigt:

- **Problembeschreibung**: Eine Erläuterung, welcher Agent blockiert wird und warum dies wichtig ist.
- **Lösung**: Anleitung zum Öffnen der `robots.txt`-Datei und zum Überprüfen der konkreten Zeilennummer neben jeder betroffenen URL.
- Eine Tabelle der betroffenen URLs mit **Zeile**, **Rang** und **URL** für jede blockierte Seite.

Jeder Agent (z. B. OAI-User, GPTBot, OAI-SearchBot) verfügt über eine eigene Unterregisterkarte, sodass Sie Blockierungen pro Agent behandeln können.

## Fehlerbehebung

Um das Problem eines blockierten Agents zu beheben, öffnen Sie die `robots.txt`-Datei und suchen Sie die Zeilennummer, die neben jeder einzelnen betroffenen URL auf der Registerkarte „Details zum blockierten Traffic nach Agent“ angezeigt wird. Aktualisieren oder entfernen Sie die blockierende Anweisung für den entsprechenden AI Agent, um den Zugriff auf die betroffene URL zu ermöglichen.

Um beispielsweise die Blockierung von GPTBot von einer bestimmten Seite aufzuheben, entfernen oder aktualisieren Sie die Anweisung:

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Nachdem Ihre `robots.txt`-Datei aktualisiert und erneut veröffentlicht wurde, erkennt LLM Optimizer die Änderung beim nächsten Audit-Durchgang und markiert den Vorschlag als behoben.

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „Durch robots.txt blockierter Traffic“ in der Frescopa-Demoumgebung aus.

[„Durch robots.txt blockierter Traffic“ in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Häufig gestellte Fragen

**Warum hat das Blockieren von AI Agents Auswirkungen auf GEO?**

Für die Generative Engine Optimization ist es erforderlich, dass KI-Crawler auf Ihre Site-Inhalte zugreifen und diese indizieren können. Durch das Blockieren von AI Agents wird die Erwähnung Ihrer Seiten in KI-generierten Antworten direkt verhindert, was Zitierungen, Markenerwähnungen und allgemeine KI-Sichtbarkeit reduziert. Selbst eine einzige blockierte Seite mit hohem Traffic-Aufkommen kann einen erheblichen Verlust an KI-gestützter Markenpräsenz darstellen.

**Was ist der Unterschied zwischen pauschalem und selektivem Blockieren?**

Eine pauschale Blockierung bedeutet, dass alle Crawler, einschließlich der allgemeinen Web-Crawler, am Zugriff auf eine Seite gehindert werden. Selektive Blockierung bedeutet, dass allgemeine Crawler auf die Seite zugreifen können, bestimmte AI Agents jedoch nicht. Bei dieser Möglichkeit wird nur auf selektive Blockierung hingewiesen, da es sich hierbau um einen beabsichtigten oder versehentlichen Ausschluss von AI Agents aus ansonsten öffentlichen Inhalten handelt, was das verwertbarste Ergebnis darstellt.

**Welche AI Agents überprüft LLM Optimizer?**

LLM Optimizer prüft auf ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot und Perplexity-User.

**Was passiert, wenn ich bestimmte AI Agents absichtlich blockieren möchte?**

Sie können jede markierte Anweisung überprüfen und die Blockierung absichtlich beibehalten. Abgelehnte Vorschläge werden über Audit-Durchgänge hinweg beibehalten und erst dann wieder angezeigt, wenn sich die `robots.txt`-Datei ändert und die Regel erneut auftritt.

**Wie verfolgt LLM Optimizer Änderungen an meiner Datei robots.txt im Laufe der Zeit?**

LLM Optimizer verwendet Hashing, um Ihre `robots.txt`-Inhalte über mehrere Durchgänge hinweg zu verfolgen. Wenn eine zuvor aufgelöste Blockierungsregel erneut auftritt, z. B. nach einer `robots.txt`-Aktualisierung, wird sie als neuer Vorschlag wieder angezeigt.

**Wie werden die Top-Seiten bestimmt?**

Seiten werden aus einer Kombination Ihrer SEO-Seiten mit dem höchsten Traffic-Aufkommen, der von AI Agents besuchten Top-URLs aus CDN-Protokollen und allen benutzerdefinierten, in Ihrer Site-Konfiguration angegebenen URLs bezogen.
