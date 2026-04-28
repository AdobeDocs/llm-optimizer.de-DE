---
title: Optimierungsmöglichkeiten
description: Erfahren Sie, wie Sie mit dem Dashboard „Möglichkeiten“ automatisch erkennen können, wie Ihre Site verbessert werden kann, um die Markensichtbarkeit zu erhöhen.
feature: Opportunities
source-git-commit: 96bb7d73c8cdd2151df12030bbf28723857c78e1
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 58%

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
| Empfohlene strukturierte Inhalte | Inhalt (Onsite) | Erkennt Prompts mit hoher Popularität ohne übereinstimmende Einträge in häufig gestellten Fragen. Zeigt ähnliche Prompts, Kategorien und betroffene URLs an. | Fügen Sie Schemablöcke mit häufig gestellten Fragen und knappen Antworten hinzu, die zu gängigen Abfragen passen. |
| [Traffic durch robots.txt blockiert](/help/dashboards/opportunities/traffic-blocked-by-robots.md) | Technische GEO | Analysiert die Datei „robots.txt“ auf Regeln, die KI-Agenten selektiv von Inhalten ausschließen, die ansonsten öffentlich zugänglich wären. meldet betroffene URLs und blockierte Agenten. | Aktualisieren Sie Ihre Datei „robots.txt“, um ggf. Zugriff auf unterstützte KI-Crawler zuzulassen. |
| [Agent-Traffic-Fehler](/help/dashboards/opportunities/agentic-traffic-errors.md) | Technische GEO | Überwacht CDN-Protokolle auf Fehlerantworten von 404, 403 und 5xx, die an KI-Agenten zurückgegeben werden. meldet betroffene URLs und Treffer insgesamt als verloren. | Korrigieren Sie fehlerhafte Links, aktualisieren Sie Berechtigungen und beheben Sie Server-seitige Probleme, sodass wichtige Inhalte 200-Antworten zurückgeben. |
| Komplexe Inhalte vereinfachen | Inhalt (Onsite) | kennzeichnet lange, komplexe Absätze, die Lesbarkeitsschwellen überschreiten und das KI-Verständnis verringern können. | Rendern Sie die Seiten vorab, damit mehr Inhalt für AI Agents ohne JavaScript-Ausführung verfügbar ist. |
| [Content-Sichtbarkeit wiederherstellen](/help/dashboards/opportunities/recover-content-visibility.md) | Technische GEO | Kennzeichnet Seiten, auf denen kritische Inhalte vor AI Agents verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die sichtbar gemacht werden können. | Geben Sie die Seiten auf CDN-Ebene mit der Option Optimieren auf Edge vorab wieder, sodass mehr Inhalte für KI-Agenten ohne JavaScript-Ausführung verfügbar sind. |
| [Wikipedia-Analyse](/help/dashboards/opportunities/wikipedia-analysis.md) | extern | Analysiert die Wikipedia-Seite Ihres Unternehmens im Vergleich zur Konkurrenz der Branche hinsichtlich Verweisen, Abschnitten, Inhaltslänge, Bildern und Vollständigkeit der Postfächer. kennzeichnet spezifische Lücken, bei denen Ihre Seite unter branchenübliche Benchmarks fällt. | Lesen Sie die KI-generierten strategischen Empfehlungen, um Ihre Wikipedia-Präsenz zu verbessern, einschließlich des Hinzufügens von Verweisen, der Anreicherung Ihres Posteingangs, der Erweiterung von Abschnitten und der Verbesserung der Artikelqualität. |
| [YouTube Sentiment Analysis (Beta)](/help/dashboards/opportunities/youtube-sentiment-analysis.md) | Offsite, Social und Community | Analysiert YouTube-Videos, die für die Markenpräsenz-Eingabeaufforderung für Markenerwähnung, Sentiment, Share of Voice und wiederkehrende Themen zitiert wurden. Wird nur angezeigt, wenn YouTube-Videos als Zitate für die Eingabeaufforderung erkannt werden. | Überprüfen Sie priorisierte Empfehlungen zur Verbesserung der Markenwahrnehmung im gesamten YouTube-Content, einschließlich empfohlener Maßnahmen und der für deren Implementierung zuständigen Teams. |
| [Reddit Sentiment Analysis (Beta)](/help/dashboards/opportunities/reddit-sentiment-analysis.md) | Offsite, Social und Community | Analysiert Reddit-Threads, die für Ihre Markenpräsenz-Eingabeaufforderung für Markenerwähnung, Sentiment, Share of Voice und wiederkehrende Themen genannt werden. Wird nur angezeigt, wenn Reddit-Threads als Zitate für die Eingabeaufforderung erkannt werden. | Überprüfen Sie priorisierte Empfehlungen zur Verbesserung der Markenwahrnehmung in allen Reddit-Inhalten, einschließlich empfohlener Maßnahmen und der für deren Implementierung zuständigen Teams. |
| [zitierte Sentiment-Analyse (Beta)](/help/dashboards/opportunities/cited-sentiment-analysis.md) | Offsite, Social und Community | Analysiert die am häufigsten zitierten URLs, die für die Markenpräsenz-Eingabeaufforderung für Markenerwähnung, Sentiment, Share of Voice und wiederkehrende Themen erkannt wurden. | Lesen Sie priorisierte Empfehlungen, um die Wahrnehmung der Marke auf den Seiten zu verbessern, die KI-Systeme am häufigsten zitieren, wenn sie auf Eingabeaufforderungen zu Ihrer Marke reagieren. |

## Automatische Optimierung {#auto-optimization}

Die automatische Optimierung ermöglicht die Bereitstellung empfohlener Optimierungen mit einem Klick und reduziert so den manuellen Aufwand und die Time-to-Value. Optimierungen können entweder an der Inhaltsquelle oder am CDN-Edge angewendet werden. Die Edge-basierte automatische Optimierung ist derzeit für ausgewählte Möglichkeiten als Early Access verfügbar. Weitere Informationen finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--
### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.
-->

### Weitere Tools

Die [LLM-Sichtbarkeitsprüfung](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) ist eine Chrome-Erweiterung, mit der Sie genau sehen können, auf welche Teile Ihrer Web-Seiteninhalte LLMs zugreifen können und was ihnen verborgen bleibt. Dieses Tool wurde als kostenloses und eigenständiges Diagnose-Tool entwickelt und erfordert keine Produktlizenz oder Einrichtung. Mit einem einzigen Klick können Benutzende die Maschinenlesbarkeit jeder Site bewerten und vergleichen, was AI Agents angezeigt wird und was menschlichen Benutzenden angezeigt wird. Außerdem bietet das Tool eine Schätzung, in welchem Umfang Inhalte mithilfe von LLM Optimizer sichtbar gemacht werden könnten.

<!--
| Detect Missing Hreflang | Content (Onsite)| Flags pages missing hreflang attributes. Provides affected URLs and expected coverage by language/region.| Implement hreflang tags to indicate correct localized versions. |
| Detect Missing Canonicals | Content (Onsite) | Scans for pages without canonical tags or with conflicting tags. Lists affected URLs and duplicates. | Add canonical tags pointing to the preferred version of each page. Ensure consistent usage across variants. |
-->
