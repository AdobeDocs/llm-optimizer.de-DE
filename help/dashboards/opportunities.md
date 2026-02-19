---
title: Optimierungsmöglichkeiten
description: Erfahren Sie, wie Sie mit dem Dashboard „Möglichkeiten“ automatisch erkennen können, wie Ihre Site verbessert werden kann, um die Markensichtbarkeit zu erhöhen.
feature: Opportunities
source-git-commit: 33196139fef1cebd47b15aa964df2bac366ea12a
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 100%

---


# Optimierungsmöglichkeiten

Optimierungsmöglichkeiten sind automatisch ermittelte Erkenntnisse und geben an, wo Ihre Website und Ihre externe Präsenz verbessert werden können, um die Markensichtbarkeit in der KI-Suche zu erhöhen.

Zu diesen Optimierungen gehören Fehlerbehebungen auf der Seite (Hinzufügen strukturierter Inhalte, Kanoniken oder Zusammenfassungen), technische Anpassungen (Aufheben der Blockierung von KI-Crawlern oder Beheben von Fehlern) und die Beeinflussung von Inhalten auf autoritativen Websites von Drittanbietern. Wenn Sie diese Optimierungsmöglichkeiten berücksichtigen, wird Ihre Marke genau repräsentiert und mit höherer Wahrscheinlichkeit in generativen Antworten zitiert.

![Optimierungsmöglichkeiten](/help/dashboards/assets/oport.png)

## Dashboard „Möglichkeiten“

Die im Dashboard dargestellten Optimierungsmöglichkeiten werden basierend auf Player-Lücken, Trend-Themen und Leistungsdaten priorisiert und als Liste dargestellt. Sie können über das Suchfeld nach einer bestimmten Möglichkeit suchen. Außerdem werden Möglichkeiten nach Tags gruppiert und Sie können direkt auf ein Tag klicken, um alle unter diesem Tag gruppierten Möglichkeiten anzuzeigen.

Wenn Sie auf **Details** klicken, wird ein separates Fenster geöffnet, in dem weitere Informationen und zusätzliche Anleitungen bereitgestellt werden.

## Unterstützte Möglichkeiten

Nachfolgend finden Sie eine Tabelle der derzeit unterstützten Möglichkeiten:

| Möglichkeit | Typ | Identifizierte Probleme | Korrekturvorschläge |
|---------|----------|----------|----------|
| Zusammenfassen langer Absätze | Inhalt (Onsite) | Erkennt Absätze, die empfohlene Längenschwellen überschreiten. Zeigt betroffene URLs und übergroße Textbausteine an. | Erstellen Sie Kurzfassungen oder teilen Sie langen Text in kürzere, überschaubare Abschnitte auf. |
| Empfehlung strukturierter Inhalte (häufig gestellte Fragen) | Inhalt (Onsite) | Erkennt Prompts mit hoher Popularität ohne übereinstimmende Einträge in häufig gestellten Fragen. Zeigt ähnliche Prompts, Kategorien und betroffene URLs an. | Fügen Sie Schemablöcke mit häufig gestellten Fragen und knappen Antworten hinzu, die zu gängigen Abfragen passen. |
| Erkennung von blockiertem Agent-basierten Traffic | Technische GEO | Analysiert CDN-Protokolle hinsichtlich blockierter Anfragen bekannter AI Agents (z. B. GPTBot, PerplexityBot). Gibt die betroffenen URLs und Agents an. | Aktualisieren Sie robots.txt oder die Server-Konfigurationen, um den Zugriff für unterstützte KI-Crawler bei Bedarf zuzulassen. |
| Erkennung von 404s-/403s-/5xx-Problemen | Technische GEO | Überwacht CDN-Protokolle auf Fehlerantworten. Gibt Häufigkeit, betroffene URLs und geschätzte verlorene Treffer an. | Korrigieren Sie fehlerhafte Links, aktualisieren Sie Berechtigungen und beheben Sie Server-seitige Probleme, sodass wichtige Inhalte 200-Antworten zurückgeben. |
| Wiederherstellung der Inhaltssichtbarkeit (Early Access) | Technische GEO | Kennzeichnet Seiten, auf denen kritische Inhalte vor AI Agents verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die sichtbar gemacht werden können. | Rendern Sie die Seiten vorab, damit mehr Inhalt für AI Agents ohne JavaScript-Ausführung verfügbar ist. |

## Automatische Optimierung {#auto-optimization}

Die automatische Optimierung ermöglicht die Bereitstellung empfohlener Optimierungen mit einem Klick und reduziert so den manuellen Aufwand und die Time-to-Value. Optimierungen können entweder an der Inhaltsquelle oder am CDN-Edge angewendet werden. Die Edge-basierte automatische Optimierung ist derzeit für ausgewählte Möglichkeiten als Early Access verfügbar. Weitere Informationen finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.-->

### Weitere Tools

Die [LLM-Sichtbarkeitsprüfung](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) ist eine Chrome-Erweiterung, mit der Sie genau sehen können, auf welche Teile Ihrer Web-Seiteninhalte LLMs zugreifen können und was ihnen verborgen bleibt. Dieses Tool wurde als kostenloses und eigenständiges Diagnose-Tool entwickelt und erfordert keine Produktlizenz oder Einrichtung. Mit einem einzigen Klick können Benutzende die Maschinenlesbarkeit jeder Site bewerten und vergleichen, was AI Agents angezeigt wird und was menschlichen Benutzenden angezeigt wird. Außerdem bietet das Tool eine Schätzung, in welchem Umfang Inhalte mithilfe von LLM Optimizer sichtbar gemacht werden könnten.

<!--| Detect Missing Hreflang | Content (Onsite)| Flags pages missing hreflang attributes. Provides affected URLs and expected coverage by language/region.| Implement hreflang tags to indicate correct localized versions. |
| Detect Missing Canonicals | Content (Onsite) | Scans for pages without canonical tags or with conflicting tags. Lists affected URLs and duplicates. | Add canonical tags pointing to the preferred version of each page. Ensure consistent usage across variants. |-->
