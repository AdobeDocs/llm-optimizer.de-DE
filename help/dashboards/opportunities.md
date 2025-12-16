---
title: Optimierungsmöglichkeiten
description: Erfahren Sie, wie Sie mit dem Opportunities-Dashboard automatisch erkennen können, wie Ihre Site verbessert werden kann, um die Sichtbarkeit Ihrer Marke zu erhöhen.
feature: Opportunities
source-git-commit: 39658a057fd4d67f74dc286e1687e384133ac653
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Optimierungsmöglichkeiten

Optimierungsmöglichkeiten werden automatisch erkannt und zeigen, wo Ihre Website und externe Präsenz verbessert werden kann, um die Sichtbarkeit der Marke bei der KI-Suche zu erhöhen.

Diese Optimierungen umfassen Fehlerbehebungen auf der Seite (Hinzufügen strukturierter Inhalte, Kanoniken oder Zusammenfassungen), technische Anpassungen (Aufheben der Blockierung von KI-Crawlern oder Beheben von Fehlern) und die Beeinflussung von Inhalten auf autorisierenden Websites von Drittanbietern. Wenn Sie diese Optimierungsmöglichkeiten ansprechen, wird Ihre Marke genau dargestellt und wird eher in generativen Antworten zitiert.

![Optimierungsmöglichkeiten](/help/dashboards/assets/oport.png)

## Opportunities-Dashboard

Die im Dashboard dargestellten Optimierungsmöglichkeiten werden basierend auf Player-Lücken, Trend-Themen und Leistungsdaten priorisiert und als Liste dargestellt. Sie können über das Suchfeld nach einer bestimmten Opportunity suchen. Außerdem werden Opportunitys nach Tags gruppiert, und Sie können direkt auf ein Tag klicken, um alle unter diesem Tag gruppierten Opportunitys anzuzeigen.

Wenn Sie **Details** klicken, wird ein separates Fenster geöffnet, in dem weitere Informationen und zusätzliche Anleitungen bereitgestellt werden.

## Unterstützte Opportunities

Nachfolgend finden Sie eine Tabelle der derzeit unterstützten Opportunitys:

| Opportunity | Typ | Identifizierte Probleme | Vorschläge korrigieren |
|---------|----------|----------|----------|
| Zusammenfassen langer Absätze | Inhalt (OnSite) | Erkennt Absätze, die empfohlene Längenschwellen überschreiten. Zeigt betroffene URLs und übergroße Textbausteine an. | Erstellen Sie Abstracts oder teilen Sie langen Text in kürzere, überschaubare Abschnitte auf. |
| Empfohlene strukturierte Inhalte (FAQs) | Inhalt (OnSite) | Erkennt Eingabeaufforderungen mit hoher Popularität ohne übereinstimmende FAQ-Einträge. Zeigt verwandte Eingabeaufforderungen, Kategorien und betroffene URLs an. | Fügen Sie häufig gestellte Fragen (FAQ) zu Schemablöcken mit knappen Antworten hinzu, um gängige Abfragen abzugleichen. |
| Fehlenden Hrefang erkennen | Inhalt (OnSite) | Markiert Seiten ohne Heflang-Attribute. Betroffene URLs und erwartete Abdeckung nach Sprache/Region. | Implementieren Sie Heflang-Tags, um die richtigen lokalisierten Versionen anzugeben. |
| Fehlende Kanonikale erkennen | Inhalt (OnSite) | Sucht nach Seiten ohne kanonische Tags oder mit widersprüchlichen Tags. Listet die betroffenen URLs und Duplikate auf. | Fügen Sie kanonische Tags hinzu, die auf die bevorzugte Version jeder Seite verweisen. Sicherstellung einer konsistenten Nutzung über Varianten hinweg. |
| Leere Überschriften erkennen | Inhalt (OnSite) | Kennzeichnet Seiten, bei denen Überschriften-Tags vorhanden sind, aber keinen Text enthalten. Zeigt URL und Speicherort leerer Tags an. | Fügen Sie Überschriften, die den darunter liegenden Inhalt widerspiegeln, beschreibenden Text hinzu. |
| Doppelte Überschriften erkennen | Inhalt (OnSite) | Scannt HTML-Überschriften-Tags und kennzeichnet wiederholte Überschriften. Zeigt betroffene URLs und duplizierte Textausschnitte an. | Überschriften ändern, um eindeutig zu sein und die Hierarchie beizubehalten (H1 → H2 → H3). Doppelte Abschnitte zusammenführen oder umbenennen. |
| Erkennen von blockiertem Agentenverkehr | Technische GEO | Analysiert CDN-Protokolle auf blockierte Anfragen bekannter KI-Agenten (z. B. GPTBot, PerplexBot). meldet betroffene URLs und Agenten. | Aktualisieren Sie die robots.txt- oder Server-Konfigurationen, um ggf. Zugriff für unterstützte KI-Crawler zu ermöglichen. |
| 404s/403s/5xx Probleme erkennen | Technische GEO | Überwacht CDN-Protokolle auf Fehlerantworten. meldet Häufigkeit, betroffene URLs und geschätzte verlorene Treffer. | Korrigieren Sie fehlerhafte Links, aktualisieren Sie Berechtigungen und beheben Sie Server-seitige Probleme, sodass wichtige Inhalte 200 Antworten zurückgeben. |
| Content-Sichtbarkeit wiederherstellen (Early Access) | Technische GEO | Markiert Seiten, auf denen kritische Inhalte vor KI-Agenten verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die wiederhergestellt werden können. | Rendern Sie die Seiten vorab, damit mehr Inhalt für KI-Agenten ohne JavaScript-Ausführung verfügbar ist. |

## Automatische Optimierung {#auto-optimization}

Die automatische Optimierung ermöglicht die Bereitstellung empfohlener Optimierungen mit einem Klick und reduziert so den manuellen Aufwand und die Wertschöpfungszeit. Optimierungen können entweder an der Inhaltsquelle oder am CDN-Edge angewendet werden. Die Edge-basierte automatische Optimierung ist derzeit für ausgewählte Opportunitys im Early Access-Modus verfügbar. Weitere Informationen finden Sie auf der Seite [Optimieren bei Edge](/help/dashboards/optimize-at-edge.md).

<!--### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.-->

### Weitere Tools

Der [LLM-Sichtbarkeitsprüfer](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) ist eine Chrome-Erweiterung, mit der Sie genau sehen können, auf wie viel Ihrer Webseiteninhalte LLMs zugreifen können und was verborgen bleibt. Es wurde als kostenloses, eigenständiges Diagnosewerkzeug entwickelt und erfordert keine Produktlizenz oder Einrichtung. Mit einem einzigen Klick können Benutzer die maschinelle Lesbarkeit jeder Site bewerten und einen Vergleich zwischen dem, was KI-Agenten sehen, und dem, was menschliche Benutzer sehen, anzeigen. Außerdem schätzt, wie viel Inhalt mithilfe von LLM Optimizer wiederhergestellt werden könnte.
