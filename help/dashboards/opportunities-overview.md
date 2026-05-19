---
title: Optimierungsmöglichkeiten
description: Erfahren Sie, wie Sie mit dem Dashboard „Möglichkeiten“ automatisch erkennen können, wie Ihre Site verbessert werden kann, um die Markensichtbarkeit zu erhöhen.
feature: Opportunities
autotag-review: '2026-05-15T17:53:48.623Z'
TQID: 'https://experienceleague.adobe.com/FAbQhzuyT-kIitIaoVQ47dam-TpN-deU5Vbo1nmK5CA'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1227
ht-degree: 56%

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
| [LLM-freundliche Zusammenfassungen hinzufügen](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Inhalt (Onsite) | kennzeichnet Seiten mit hohem Traffic, denen es an prägnanten Zusammenfassungen und strukturierten Schlüsselpunkten auf Seiten- oder Abschnittsebene mangelt, wodurch es für KI-Agenten schwieriger wird, Markenansprüche zu durchsuchen und zu interpretieren. Zeigt die betroffenen URLs und wo Zusammenfassungen empfohlen werden. | Überprüfen Sie KI-generierte Zusammenfassungen und Schlüsselpunkte, die auf vorhandenen Inhalten basieren, und stellen Sie sie dann am CDN-Edge mit Optimieren bei Edge bereit, damit Agenten einen klareren, überschaubaren Kontext erhalten. |
| [Relevante FAQs hinzufügen](/help/dashboards/opportunities/add-relevant-faqs.md) | Inhalt (Onsite) | kennzeichnet Seiten mit hohem Traffic, denen strukturierte Fragen und Antworten fehlen, die auf Ihr Eingabeaufforderungsset abgestimmt sind, wodurch es für KI-Agenten schwieriger wird, Benutzerfragen mit Ihrer Seite abzugleichen. Zeigt die betroffenen URLs und wo FAQs empfohlen werden. | Überprüfen Sie KI-generierte, zielgerichtete FAQ-Inhalte, die auf vorhandenem Seitenmaterial basieren, und stellen Sie sie dann am CDN-Edge mit Optimieren bei Edge bereit, damit Agenten einen klareren Kontext mit Fragen und Antworten erhalten. |
| [Hinzufügen von Zusammenfassungen von Multimedia-Transkripten](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Inhalt (Onsite) | kennzeichnet Seiten, auf denen wichtige Informationen ohne maschinenlesbare Transkripte oder Zusammenfassungen in Videos oder andere Medien eingebettet sind, sodass diese Inhalte für KI-Agenten schwer zu verwenden sind. Zeigt betroffene URLs und empfohlenen Text an. | Überprüfen Sie die KI-generierten Transkriptzusammenfassungen, die auf den Medien und der Seite basieren, und stellen Sie sie dann am CDN-Edge mit Optimieren bei Edge bereit, damit die Agenten maschinenlesbaren Text erhalten (z. B. in der Nähe des entsprechenden Videos). |
| [Durch robots.txt blockierter Traffic](/help/dashboards/opportunities/traffic-blocked-by-robots.md) | Technische GEO | Analysiert die robots.txt-Datei auf Regeln, die AI Agents selektiv von Inhalten ausschließen, die ansonsten öffentlich zugänglich sind. Meldet betroffenen URLs und blockierten Agents. | Aktualisieren Sie die robots.txt-Datei, um den Zugriff für unterstützte KI-Crawler bei Bedarf zuzulassen. |
| [Fehler im Zusammenhang mit Agent-basiertem Traffic](/help/dashboards/opportunities/agentic-traffic-errors.md) | Technische GEO | Überwacht CDN-Protokolle auf 404-, 403- und 5xx-Fehlerantworten, die an AI Agents zurückgegeben werden. Meldet betroffene URLs und die Gesamtanzahl der fehlerhaften Treffer. | Korrigieren Sie fehlerhafte Links, aktualisieren Sie Berechtigungen und beheben Sie Server-seitige Probleme, sodass wichtige Inhalte 200-Antworten zurückgeben. |
| [Vereinfachung komplexer Inhalte](/help/dashboards/opportunities/simplify-complex-content.md) | Inhalt (Onsite) | kennzeichnet Seiten mit hohem Traffic, bei denen sich eine dichte oder komplexe Kopie unterhalb der Lesbarkeitsschwellen befindet, wodurch es für KI-Agenten schwieriger wird, wichtige Informationen zu interpretieren. Zeigt die betroffenen URLs und wo ein vereinfachter Text empfohlen wird. | Überprüfen Sie KI-generierten verbesserten Text, der auf vorhandenen Seiteninhalten basiert, und stellen Sie ihn dann am CDN-Edge mit Optimieren bei Edge bereit, damit Agenten klarere, leichter zu scannende Passagen erhalten. |
| [Content-Sichtbarkeit wiederherstellen](/help/dashboards/opportunities/recover-content-visibility.md) | Technische GEO | Kennzeichnet Seiten, auf denen kritische Inhalte vor AI Agents verborgen sind. Zeigt betroffene URLs und erwartete Inhalte an, die sichtbar gemacht werden können. | Rendern Sie die Seiten mit „Optimize at Edge“ auf der CDN-Ebene vorab, damit mehr Inhalt für AI Agents ohne JavaScript-Ausführung verfügbar ist. |
| [Inhaltsverzeichnis hinzufügen](/help/dashboards/opportunities/add-table-of-contents.md) | Technische GEO | Erkennt Seiten ohne klare strukturelle Organisation oder Navigationsüberschriften, was es für KI-Agenten schwierig macht, Inhalte zu analysieren und Benutzerabfragen zuzuordnen. Zeigt die betroffenen URLs an und wo ein strukturiertes Inhaltsverzeichnis empfohlen wird. | Überprüfen Sie das vorgeschlagene strukturierte Inhaltsverzeichnis mit verankerten Überschriften, die die Hauptabschnitte der Seite widerspiegeln, und stellen Sie es dann am CDN-Rand mit Optimieren in Edge bereit, damit ein Inhaltsverzeichnis in HTML eingefügt wird, um die Seitenstruktur zu verbessern, damit Modelle relevante Abschnitte leichter extrahieren, zuordnen und zitieren können. |
| [Wikipedia-Analyse](/help/dashboards/opportunities/wikipedia-analysis.md) | Offsite | Analysiert die Wikipedia-Seite Ihres Unternehmens im Vergleich zur Branchenkonkurrenz hinsichtlich Referenzen, Abschnitten, Inhaltslänge, Bildern und Vollständigkeit der Infobox. Ermittelt konkrete Lücken, bei denen Ihre Seite unter Branchen-Benchmarks fällt. | Lesen Sie die KI-generierten strategischen Empfehlungen, um Ihre Wikipedia-Präsenz zu verbessern, unter anderem durch Hinzufügen von Referenzen, Anreichern der Infobox, Erweitern von Abschnitten und Verbessern der Artikelqualität. |
| [YouTube-Sentiment-Analyse (Beta)](/help/dashboards/opportunities/youtube-sentiment-analysis.md) | Offsite, Social Media und Community | Analysiert YouTube-Videos, die für das Markenpräsenz-Prompt-Set für Markenerwähnungen, Sentiment, Share of Voice und wiederkehrende Themen zitiert werden. Wird nur angezeigt, wenn YouTube-Videos als Grundlage für Zitierungen für Ihr Prompt-Set ermittelt werden. | Lesen Sie die priorisierten Empfehlungen zur Verbesserung der Markenwahrnehmung in allen YouTube-Inhalten, einschließlich empfohlener Maßnahmen und der für deren Implementierung zuständigen Teams. |
| [Reddit-Sentiment-Analyse (Beta)](/help/dashboards/opportunities/reddit-sentiment-analysis.md) | Offsite, Social Media und Community | Analysiert Reddit-Threads, die für das Markenpräsenz-Prompt-Set für Markenerwähnungen, Sentiment, Share of Voice und wiederkehrende Themen zitiert werden. Wird nur angezeigt, wenn Reddit-Threads als Grundlage für Zitierungen für Ihr Prompt-Set ermittelt werden. | Lesen Sie die priorisierten Empfehlungen zur Verbesserung der Markenwahrnehmung in allen Reddit-Inhalten, einschließlich empfohlener Maßnahmen und der für deren Implementierung zuständigen Teams. |
| [Sentiment-Analyse von Zitierungen (Beta)](/help/dashboards/opportunities/cited-sentiment-analysis.md) | Offsite, Social Media und Community | Analysiert die am häufigsten zitierten URLs, die für das Markenpräsenz-Prompt-Set für Markenerwähnungen, Sentiment, Share of Voice und wiederkehrende Themen zitiert werden. | Lesen Sie die priorisierten Empfehlungen zur Verbesserung der Markenwahrnehmung auf allen Seiten, die KI-Systeme beim Beantworten von Prompts zu Ihrer Marke am häufigsten zitieren. |
| [Produktkatalog anreichern (Beta)](/help/dashboards/opportunities/enrich-product-catalog.md) | Inhalt (OnSite), Adobe Commerce | kennzeichnet Commerce-Katalogprodukte, deren Namen oder Beschreibungen zu generisch, technisch zu kompakt oder für LLMs zu mehrdeutig sind. Zeigt ausgewertete PDPs, den agenten Traffic-Kontext und KI-generierte Erzählungsanreicherungen an. | Überprüfen und bearbeiten Sie vorgeschlagene Produktnamen und Beschreibungen und stellen Sie dann Optimierungen bereit, um Aktualisierungen direkt in Ihrem Adobe Commerce-Katalog zu veröffentlichen (mit Rollback aus „Feste Vorschläge„). |
| [Anreichern von Produktdetailseiten](/help/dashboards/opportunities/enrich-product-detail-pages.md) | Technische GEO, Adobe Commerce | Vergleicht für Adobe Commerce-Storefronts vollständige Katalogdaten mit dem, auf was KI-Agenten auf jeder Produktdetailseite zugreifen können; zeigt PDPs an, auf denen Varianten, Spezifikationen, Attribute und zugehörige Katalogfelder im für Agenten sichtbaren HTML fehlen, priorisiert nach Agententraffic. | Hebt hervor, dass in der Agentenansicht wiederherstellbare Kataloginformationen fehlen und warum dies für die LLM-gesteuerte Produkterkennung wichtig ist; stellen Sie mit Optimize bei Edge bereit, um einen vollständig vorgerenderten, KI-freundlichen HTML-Snapshot für den Agent-Traffic am CDN-Edge bereitzustellen, damit Agenten einen umfangreichen Produktkontext aus Ihrem Katalog erhalten, ohne dass CMS- oder Katalogänderungen erforderlich sind. |

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
