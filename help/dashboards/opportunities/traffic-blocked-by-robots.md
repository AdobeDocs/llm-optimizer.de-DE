---
title: Traffic durch robots.txt blockiert
description: Erfahren Sie, wie LLM Optimizer erkennt, wenn Ihre robots.txt-Datei AI-Agenten am Zugriff auf Ihren Inhalt hindert, und wie Sie sie beheben können.
feature: Opportunities
autotag-review: '2026-05-15T18:00:25.453Z'
TQID: 'https://experienceleague.adobe.com/9LGbxeIbWYZp-MN5Zww6g-dQ6BZT0IWzlA7XB-2Xlho'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 817
ht-degree: 1%

---


# Traffic durch robots.txt blockiert

Ihre `robots.txt`-Datei steuert, welche Crawler auf Ihre Site zugreifen können. Wenn KI-Agenten selektiv für Inhalte blockiert werden, auf die ansonsten allgemeine Crawler zugreifen können, können diese Agenten diese Inhalte nicht indizieren oder zitieren, was die Sichtbarkeit Ihrer Marke in KI-generierten Antworten direkt beeinträchtigt.

Die Opportunity „Traffic blockiert durch robots.txt“ analysiert Ihre `robots.txt`-Datei im Vergleich zu Ihren Top-Seiten und identifiziert Regeln, die KI-Agenten am Zugriff auf Inhalte hindern, die sie erreichen sollten. Er zeigt Ergebnisse auf der Ebene einzelner `robots.txt` an, sodass Sie bestimmte Anweisungen überprüfen und aktualisieren können, anstatt die gesamte Datei manuell zu überprüfen.

Sie zeigt zwei Schlüsselmetriken auf einen Blick:

- **URLs insgesamt** - Anzahl der URLs, die von Blockierungsregeln in Ihrem `robots.txt` betroffen sind.
- **Blockierte Agenten** - Anzahl der KI-Agenten, die am Zugriff auf diese URLs gehindert werden.

![Durch das Dashboard robots.txt blockierter Traffic](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Funktionsweise

LLM Optimizer ruft Ihre `robots.txt` ab und vergleicht Ihre Top-Seiten mit sechs wichtigen Benutzeragenten des KI-Agenten:

- ClaudeBot
- GPTBot
- OAI-SearchBot
- OAI-User
- RatlosigkeitBot
- Perplexity-User

Eine URL wird nur gekennzeichnet, wenn sie **für den Platzhalter(`*`)-Benutzeragenten zulässig, aber nicht für einen bestimmten KI-Agenten)**. Eine generelle Blockierung, bei der alle Crawler gleichermaßen eingeschränkt sind, wird nicht gemeldet. Der Audit zielt speziell auf den selektiven Ausschluss von KI-Agenten ab, der für GEO den umsetzbarsten Befund darstellt.

>[!NOTE]
>Bei dieser Gelegenheit wird keine KI für die Entwicklung oder Bereitstellung von Vorschlägen verwendet. Die Ergebnisse basieren vollständig auf der direkten Analyse Ihrer `robots.txt`.

Die Ergebnisse werden auf zwei Registerkarten angezeigt: **robots.txt** und **Blocked Traffic Details by Agent**.

## robots.txt

Auf dieser Registerkarte wird Ihre vollständige `robots.txt`-Datei mit rot markierten Sperranweisungen angezeigt. Jede hervorgehobene Zeile steht für eine Regel, die selektiv einen oder mehrere KI-Agenten am Zugriff auf eine URL hindert, die ansonsten öffentlich zugänglich ist.

![Ansicht „robots.txt“ mit hervorgehobenen Sperranweisungen](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Durch Klicken auf eine hervorgehobene Anweisung werden weitere Informationen über ihre Auswirkungen und die vorgeschlagene Fehlerbehebung angezeigt.

## Details zum blockierten Traffic nach Agent

Diese Registerkarte enthält eine Aufschlüsselung des blockierten Traffics, der nach KI-Agent organisiert ist. Für jeden blockierten Agenten wird Folgendes angezeigt:

- **Problembeschreibung** - Eine Erläuterung, welcher Agent blockiert wird und warum dies wichtig ist.
- **Lösung** - Anleitung zum Öffnen der `robots.txt`-Datei und zum Überprüfen der spezifischen Zeilennummer neben jeder betroffenen URL.
- Eine Tabelle der betroffenen URLs mit den **LINE**, **Rank** und **URL** für jede blockierte Seite.

Jeder Agent (z. B. OAI-User, GPTBot, OAI-SearchBot) verfügt über eine eigene Unterregisterkarte, sodass Sie Blöcke pro Agent adressieren können.

## Fehlerbehebung

Um einen blockierten Agent-Fund zu beheben, öffnen Sie die `robots.txt`-Datei und suchen Sie die Zeilennummer, die neben den einzelnen betroffenen URLs auf der Registerkarte Details zum blockierten Traffic nach Agent angezeigt wird. Aktualisieren oder entfernen Sie die Disallow-Anweisung für den entsprechenden KI-Agenten, um den Zugriff auf die betroffene URL zu ermöglichen.

Um beispielsweise GPTBot von einer bestimmten Seite zu entsperren, entfernen oder aktualisieren Sie die Anweisung:

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Nachdem Ihre `robots.txt` aktualisiert und erneut veröffentlicht wurde, erkennt LLM Optimizer die Änderung beim nächsten Audit-Durchgang und markiert den Vorschlag als aufgelöst.

## In der Demo ausprobieren

Sehen Sie sich die Opportunity „Traffic blockiert von robots.txt“ in Aktion an, indem Sie die Demo-Umgebung von Frescopa verwenden.

[Traffic Blocked by robots.txt in der Frescopa Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Häufig gestellte Fragen

**Warum ist das Blockieren von KI-Agenten für GEO wichtig?**

Für die Optimierung der generativen Engine ist es erforderlich, dass KI-Crawler auf Ihre Website-Inhalte zugreifen und diese indizieren können. Durch das Blockieren von KI-Agenten werden Ihre Seiten direkt in KI-generierten Antworten nicht angezeigt, was die Zitate, die Markenerwähnung und die allgemeine KI-Sichtbarkeit reduziert. Selbst eine einzige blockierte Seite mit hohem Traffic-Aufkommen kann einen erheblichen Verlust an KI-gesteuerter Markenerfahrung darstellen.

**Was ist der Unterschied zwischen pauschalem und selektivem Blockieren?**

Eine generelle Blockierung bedeutet, dass alle Crawler - einschließlich der allgemeinen Web-Crawler - von einer Seite aus gesperrt sind. Selektive Blockierung bedeutet, dass allgemeine Crawler-Benutzende auf die Seite zugreifen können, bestimmte KI-Agenten jedoch nicht. Bei dieser Gelegenheit wird nur auf selektive Blockierung hingewiesen, da dies einen beabsichtigten oder versehentlichen Ausschluss von KI-Agenten aus ansonsten öffentlichen Inhalten darstellt, was den umsetzbarsten Fund darstellt.

**Welche KI-Agenten überprüft LLM Optimizer?**

LLM Optimizer prüft auf ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot und Perplexity-User.

**Was passiert, wenn ich bestimmte KI-Agenten absichtlich blockieren möchte?**

Sie können jede gekennzeichnete Anweisung überprüfen und den Block absichtlich beibehalten. Abgelehnte Vorschläge werden über Audit-Durchgänge hinweg beibehalten und erst dann wieder angezeigt, wenn sich die `robots.txt` ändert und die Regel erneut angezeigt wird.

**Wie verfolgt LLM Optimizer Änderungen an meiner robots.txt im Laufe der Zeit?**

LLM Optimizer verwendet Hashing, um Ihre `robots.txt` Inhalte über mehrere Ausführungen hinweg zu verfolgen. Wenn eine zuvor aufgelöste Blockierungsregel erneut angezeigt wird - z. B. nach einer `robots.txt` Aktualisierung -, wird sie als neuer Vorschlag wieder angezeigt.

**Wie werden die Top-Seiten festgelegt?**

Seiten werden aus einer Kombination Ihrer SEO-Seiten mit dem höchsten Traffic, der von KI-Agenten besuchten Top-URLs aus CDN-Protokollen und allen benutzerdefinierten URLs, die in Ihrer Site-Konfiguration angegeben sind, bezogen.
