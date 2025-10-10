---
title: Optimierungsmöglichkeiten
description: Dies ist die Artikelübersicht.
source-git-commit: 77bddfa7351d573c20a0f68a08b69000bc06beb8
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Optimierungsmöglichkeiten

Optimierungsmöglichkeiten werden automatisch erkannt und zeigen, wo Ihre Website und externe Präsenz verbessert werden kann, um die Sichtbarkeit der Marke bei der KI-Suche zu erhöhen. Diese Optimierungen umfassen Fehlerbehebungen auf der Seite (Hinzufügen strukturierter Inhalte, Kanoniken oder Zusammenfassungen), technische Anpassungen (Aufheben der Blockierung von KI-Crawlern oder Beheben von Fehlern) und die Beeinflussung von Inhalten auf autorisierenden Websites von Drittanbietern. Wenn Sie diese Optimierungsmöglichkeiten ansprechen, wird Ihre Marke genau dargestellt und wird eher in generativen Antworten zitiert.

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
| Fehlende Kanonikale erkennen | Inhalt (OnSite) | Erkennt Absätze, die empfohlene Längenschwellen überschreiten. Zeigt betroffene URLs und übergroße Textbausteine an. | Erstellen Sie Abstracts oder teilen Sie langen Text in kürzere, überschaubare Abschnitte auf. |
| Leere Überschriften erkennen | Inhalt (OnSite) | Kennzeichnet Seiten, bei denen Überschriften-Tags vorhanden sind, aber keinen Text enthalten. Zeigt URL und Speicherort leerer Tags an. | Fügen Sie Überschriften, die den darunter liegenden Inhalt widerspiegeln, beschreibenden Text hinzu. |
| Doppelte Überschriften erkennen | Inhalt (OnSite) | Scannt HTML-Überschriften-Tags und kennzeichnet wiederholte Überschriften. Zeigt betroffene URLs und duplizierte Textausschnitte an. | Überschriften ändern, um eindeutig zu sein und die Hierarchie beizubehalten (H1 → H2 → H3). Doppelte Abschnitte zusammenführen oder umbenennen. |
| Erkennen von blockiertem Agentenverkehr | Technische GEO | Analysiert CDN-Protokolle auf blockierte Anfragen bekannter KI-Agenten (z. B. GPTBot, PerplexBot). meldet betroffene URLs und Agenten. | Aktualisieren Sie die robots.txt- oder Server-Konfigurationen, um ggf. Zugriff für unterstützte KI-Crawler zu ermöglichen. |
| 404s/403s/5xx Probleme erkennen | Technische GEO | Überwacht CDN-Protokolle auf Fehlerantworten. meldet Häufigkeit, betroffene URLs und geschätzte verlorene Treffer. | Korrigieren Sie fehlerhafte Links, aktualisieren Sie Berechtigungen und beheben Sie Server-seitige Probleme, sodass wichtige Inhalte 200 Antworten zurückgeben. |
