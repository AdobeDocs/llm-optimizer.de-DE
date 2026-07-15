---
title: Inhaltssichtbarkeit wiederherstellen
description: Erfahren Sie, wie LLM Optimizer Seiten identifiziert, auf denen kritische Inhalte vor AI Agents verborgen bleiben, und wie Sie mithilfe der Edge-basierten Optimierung Sichtbarkeit wiederherstellen können.
feature: Opportunities
autotag-review: '2026-07-15T18:06:12.342Z'
TQID: 'https://experienceleague.adobe.com/ILtulZHGNjX0Qes77aNZMe-Fs66BLryK3kHcORZ58A8'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 928
ht-degree: 100%

---


# Inhaltssichtbarkeit wiederherstellen

AI Agents können nur Inhalte zitieren, auf die sie zugreifen können. Wenn wichtige Inhalte auf Ihren Seiten hinter Client-seitigem Rendering und dynamischen Ladevorgängen (wie Produktbeschreibungen, Benutzerbewertungen, Rezepte und Kommentare) verborgen sind, übersehen AI Agents diese vollständig, sodass wertvolle Inhalte für die Systeme unsichtbar bleiben, die sie zitieren könnten.

Die Möglichkeit „Content-Sichtbarkeit wiederherstellen“ identifiziert Seiten Ihrer Site, auf denen diese Sichtbarkeitslücke auftritt. Für jede betroffene Seite wird genau angezeigt, welche Inhalte in der Ansicht des AI Agents fehlen. Lücken werden hervorgehoben und Sie können Änderungen ohne CMS-Änderungen oder Beteiligung von Entwickelnden anwenden.

Es werden vier Schlüsselmetriken auf einen Blick angezeigt:

- **URLs**: Anzahl der Seiten, für die eine Content-Sichtbarkeitslücke identifiziert wurde.
- **Geschätzter Inhaltsgewinn**: Der geschätzte Multiplikator des Inhalts, der durch Anwendung der Optimierung wiederhergestellt werden könnte.
- **Durchschnittliche Content-Sichtbarkeit**: Der durchschnittliche Prozentsatz der Inhalte, die derzeit für AI Agents auf den betroffenen Seiten sichtbar sind.

![Dashboard „Content-Sichtbarkeit wiederherstellen“](/help/dashboards/opportunities/assets/recover-content-visibility-overview.png)

Unter [Wiederherstellen der Content-Sichtbarkeit](https://www.youtube.com/watch?v=BigPyJssFCw) können Sie ein Überblickvideo zu dieser Möglichkeit ansehen.

Diese Möglichkeit kann mithilfe von [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md) optimiert werden. Optimierungen werden ausschließlich an AI Agents bereitgestellt, ohne dass dies Auswirkungen auf menschliche Besuchende hat (Bot-only-Bereitstellung). Optimierungen werden dann auf der CDN-Ebene angewendet, ohne dass CMS-Änderungen erforderlich sind, und können innerhalb von Minuten ohne Entwicklerinteraktion wirksam werden, was eine schnelle Bereitstellung mit geringem Risiko ermöglicht.

## Funktionsweise

LLM Optimizer analysiert Ihre Seiten und vergleicht die Inhalte, auf die AI Agents zugreifen können, mit dem tatsächlichen Inhalt der Seite. Seiten, die einen hohen Agent-basierten Traffic erhalten, aber eine niedrige Content-Sichtbarkeit haben, werden in der Tabelle **URLs mit Vorschlägen** priorisiert nach Volumen des Agent-basierten Traffics angezeigt.

Für jede betroffene URL bietet LLM Optimizer Folgendes:

- **KI-Analyse**: Eine Beschreibung davon, welche Inhalte fehlen und warum sie für die LLM-Kompatibilität wichtig sind, zusammen mit einer Liste der Inhaltsreferenzen, die wiederhergestellt werden können
- **Content-Sichtbarkeit**: Der Prozentsatz des Inhalts, der derzeit für AI Agents auf dieser Seite sichtbar ist
- **Verhältnis des Inhaltsgewinns**: Der geschätzte Multiplikator des durch Anwendung der Optimierung wiederherstellbaren Inhalts
- **Vorschau**: Ein direkter HTML-Vergleich, die einen Vergleich der derzeitigen mit der nachbearbeiteten Seite anzeigt, sodass Sie die Änderung vor der Bereitstellung überprüfen können

Die Korrektur erfolgt mit [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md), der Edge-basierten Bereitstellungsfunktion von Adobe, die eine vollständig vorgerenderte, KI-freundliche HTML-Momentaufnahme für LLM-Benutzer-Agents auf CDN-Ebene bereitstellt und zuvor ausgeblendete Inhalte wiederherstellt, ohne Änderungen an ihrem CMS vorzunehmen.

<!-- [URLs with suggestions](/help/dashboards/opportunities/assets/recover-content-visibility-urls.png)-->

## URLs mit Vorschlägen

Die Tabelle **URLs mit Vorschlägen** listet alle betroffenen Seiten auf und kann nach Klassifizierung gefiltert werden. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile**, um die KI-Analyse anzuzeigen, einschließlich der fehlenden Inhalte und der Gründe, warum sie wichtig sind.
- **Zeigen Sie eine Vorschau** des direkten HTML-Vergleichs der aktuellen Seite mit der nachbearbeiteten Version an.
- **Markieren Sie das Problem als korrigiert**, sobald es behoben ist.
- **Ignorieren** Sie nicht relevante Vorschläge.

Die Vorschläge sind in drei Ansichten unterteilt: **Aktuelle Vorschläge**, **Korrigierte Vorschläge** und **Ignorierte Vorschläge**. Sobald ein Vorschlag implementiert ist, wird er in den Bereich „Korrigierte Vorschläge“ verschoben und erhält den Status **Optimiert**. Zusätzlich kann mit der Aktion **Live anzeigen** überprüft werden, ob die Optimierung für den Agent-basierten Traffic live ist. Korrigierte Vorschläge können jederzeit rückgängig gemacht werden.

![Korrigierte Vorschläge mit dem Status „Optimiert“](/help/dashboards/opportunities/assets/recover-content-visibility-fixed.png)

## Bereitstellen der Optimierung

Nachdem Sie die Vorschläge überprüft und die zu optimierenden URLs ausgewählt haben, klicken Sie auf **Optimierungen bereitstellen**, um die Korrektur auf CDN-Edge zu veröffentlichen. Ein Bestätigungsdialogfeld **In Edge bereitstellen** zeigt die ausgewählten URLs an, deren Typ (Prerender) und den angewendeten Vorschlag an. Nach der Bereitstellung wird auf einem Bestätigungsbildschirm angezeigt, welche URLs erfolgreich optimiert wurden.

>[!NOTE]
>
>Das Bereitstellen von Optimierungen erfordert den Abschluss des Onboarding-Prozesses „Optimize at Edge“. Falls Sie das Onboarding noch nicht abgeschlossen haben, gelangen Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess. Ausführliche Informationen zur Funktionsweise von „Optimize at Edge“, zu den unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

![Dialogfeld „In Edge bereitstellen“](/help/dashboards/opportunities/assets/recover-content-visibility-deploy.png)

## Ausprobieren in der Demo

Probieren Sie die Möglichkeit „Content-Sichtbarkeit wiederherstellen“ in der Frescopa-Demoumgebung aus.

[„Content-Sichtbarkeit wiederherstellen“ in der Frescopa-Demo ansehen](https://play.llmo.now/org/demo-org/opportunities/prerender/75729489-756a-4c2b-9905-155b1715da5c)

## Häufig gestellte Fragen

**Warum ist der Inhalt meiner Seite für AI Agents verborgen?**

Die meisten modernen Websites nutzen JavaScript, um Inhalte nach der ersten Seitenanforderung dynamisch zu laden. AI Agents führen in der Regel kein JavaScript aus, daher werden Client-seitig gerenderte Inhalte – Produktlisten, Benutzerbewertungen, Links zu Blogartikeln und ähnliche Elemente – vom AI Agent nie gesehen, selbst wenn sie für menschliche Besuchende vollständig sichtbar sind.

**Hat diese Optimierung Auswirkungen auf meine menschlichen Besuchenden oder SEO-Bots?**

Nein. „Optimize at Edge“ zielt ausschließlich auf KI-Benutzer-Agents ab. Menschliche Besuchende und SEO-Bots wird die Originalseite genau wie zuvor angezeigt, ohne dass sich ihr Erlebnis oder die Leistung ändert.

**Muss ich mein CMS ändern oder Entwickelnde einbeziehen?**

Nein. Die Optimierung wird auf CDN-Edge angewendet und erfordert keine Authoring-Änderungen, Code-Bereitstellungen oder Entwicklerbeteiligung. Nach dem Onboarding von „Optimize at Edge“ können Sie Änderungen innerhalb von Minuten direkt über die LLM Optimizer-Oberfläche bereitstellen und rückgängig machen.

**Was passiert, wenn sich der Inhalt meiner Seite nach der Bereitstellung ändert?**

Für die Wiederherstellung der Content-Sichtbarkeit verwendet LLM Optimizer niedrige Cache-TTL-Einstellungen, sodass jede Inhaltsaktualisierung auf Ihrer Site innerhalb weniger Minuten eine Aktualisierung auslöst. AI Agents wird stets die aktuellste Version Ihrer Inhalte zur Verfügung gestellt.

**Was sind die ersten Schritte mit „Optimize at Edge“?**

Den vollständigen Onboarding-Prozess, CDN-Konfigurationsanleitungen und Voraussetzungen finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).
