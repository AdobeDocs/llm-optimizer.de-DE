---
title: Komplexe Inhalte vereinfachen
description: Erfahren Sie, wie LLM Optimizer Seiten mit hohem Traffic mit hoher Kopierdichte identifiziert, die für KI-Agenten schwer zu interpretieren sind, und wie Sie mit Optimize bei Edge vereinfachten Text überprüfen und bereitstellen können.
feature: Opportunities
autotag-review: '2026-07-15T18:04:55.581Z'
TQID: 'https://experienceleague.adobe.com/uMK9qeAGMNrtvR0TYbeg8SIOKlwKf4L5NIE9ZgsJaUw'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 785
ht-degree: 10%

---


# Komplexe Inhalte vereinfachen

Die Opportunity zur Vereinfachung komplexer Inhalte identifiziert Seiten mit hohem Traffic-Aufkommen, auf denen dichter oder komplexer Text vorhanden ist, was die Interpretation wichtiger Informationen durch KI-Agenten erschwert. Es führt klarere, leichter zu scannende Versionen der vorhandenen Kopie ein, während die ursprüngliche Bedeutung erhalten bleibt. Auf diese Weise können Agenten wichtige Informationen zuverlässiger analysieren, zusammenfassen und extrahieren.

Für jede betroffene URL können Sie Vorschläge für **Verbesserter Text** überprüfen, mit **Vorschau** vergleichen und dann mit [Optimieren in Edge) bereitstellen, &#x200B;](/help/dashboards/optimize-at-edge/overview.md) der Agent-Traffic klarere HTML-Informationen erhält, ohne dass Änderungen am Content Management System (CMS) erforderlich sind.

## So wird das Problem behoben

Fehlerbehebungen werden mit [Optimieren in Edge](/help/dashboards/optimize-at-edge/overview.md) angewendet, die:

- Bereitstellung eines vorab gerenderten HTML-Snapshots für KI-Agenten.
- Aktualisiert die für den Agenten sichtbare Seite, sodass komplexe Passagen ersetzt oder durch &quot;**Text“** der Live-Seite erweitert werden.
- Funktioniert auf CDN-Ebene (keine CMS-Änderungen).
- Ist nur KI - keine Auswirkungen auf menschliche Besucher oder SEO-Bots.
- Wird innerhalb von Minuten bereitgestellt und kann **der Benutzeroberfläche** LLM Optimizer vollständig rückgängig gemacht werden.

## Funktionsweise

LLM Optimizer kennzeichnet Seiten, die hohen Agent-Traffic erhalten und bei denen Inhalte unterhalb der Lesbarkeitsschwellen bewertet werden, und schlägt dann Neuschreibungen der Kopie vor. Für jede Seite gibt es Folgendes:

**Verbesserter Text** - vereinfachter Inhalt, der auf dem basiert, was bereits auf der Seite vorhanden ist.
**Vorschau** - ein Vergleich vor und nach dem Vergleich für den authentischen Traffic.

Betroffene URLs werden in der Tabelle **URLs mit Vorschlägen** auf der Registerkarte **Aktuelle**&quot; angezeigt, wo Sie eine Zeile erweitern können, um jede Empfehlung zu überprüfen.

![URLs mit Vorschlägen zu aktuellen Vorschlägen, erweiterte Zeile mit verbessertem Text und Vorschau](/help/dashboards/opportunities/assets/simplify-complex-content-expand.png)

Die Tabelle **URLs mit Vorschlägen** listet Seiten auf, auf denen vereinfachte Inhalte das Verständnis durch Agenten erleichtern würden. Die Vorschläge sind in **Aktuelle Vorschläge**, **Feste Vorschläge** und **Ignorierte Vorschläge** unterteilt. Für jede URL haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile** um **Verbesserter Text** Vorschläge für diese Seite anzuzeigen.
- **Vorschau** des Vorher-Nachher-Vergleichs für agenten Traffic.
- **Als behoben markieren** wenn Sie die Opportunity außerhalb von LLM Optimizer angesprochen haben.
- **Ignorieren** Sie nicht relevante Vorschläge.

**Ansichten** umfassen **Aktuelle**), **Feste Vorschläge** (Status **Optimiert** bei Bereitstellung) und **Ignorierte Vorschläge**. Sie können die Live-Bereitstellung mit **Live anzeigen** unter **Feste Vorschläge** überprüfen und jederzeit ein Rollback durchführen.

Wählen Sie die URLs oder Zeileneinträge aus, für **Sie** Kontrollkästchen verwenden möchten, und verwenden Sie dann **Als behoben markieren**, **Vorschläge ignorieren** oder **Optimierungen bereitstellen** in der Kopfzeile **Opportunity-Plan**. Die Demo-Benutzeroberfläche zeigt auch eine Auswahlanzahl und zugehörige Aktionen mit der Liste an.

![Opportunity-Plan, Aktuelle Vorschläge, erweiterte Zeile und Bereitstellungsoptimierungen im Plan-Header](/help/dashboards/opportunities/assets/simplify-complex-content-select.png)

### Bereitstellen der Optimierung

Wenn Sie bereit sind, am Edge zu veröffentlichen, klicken Sie auf **Optimierungen bereitstellen**. In **Dialogfeld „Für Edge bereitstellen** werden die ausgewählten URLs und Optimierungsdetails aufgelistet. Überprüfen Sie die Liste und wählen Sie **Bereitstellen** oder **Abbrechen**.

![Dialogfeld „In Edge bereitstellen“](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-dialog.png)

Nach erfolgreicher Bereitstellung bestätigt **Bereitstellung abgeschlossen** wie viele Optimierungen aktiviert wurden, und stellt fest, dass es möglicherweise einige Zeit dauern kann, bis KI-Agenten die Aktualisierung indizieren. Schließen Sie das Dialogfeld und öffnen Sie **Behobene Vorschläge**, um den Status zu überprüfen.

![Bestätigung des Bereitstellungsabschlusses](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-confirm.png)

>[!NOTE]
>
>Das Bereitstellen von Optimierungen erfordert den Abschluss des Onboarding-Prozesses „Optimize at Edge“. Falls Sie das Onboarding noch nicht abgeschlossen haben, gelangen Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess. Ausführliche Informationen zur Funktionsweise von „Optimize at Edge“, zu den unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Behobene Vorschläge und Live-Ansicht

Bei **Behobenen**) werden bereitgestellte URLs in **Statusspalte** Optimiert“ angezeigt. Erweitern Sie eine Zeile, um bereitgestellte (**Text)** Anweisungen zu überprüfen.

![Registerkarte „Behobene Vorschläge“ mit Status „Optimiert“, erweiterter vereinfachter Kopie, Live-Ansicht und Details](/help/dashboards/opportunities/assets/simplify-complex-content-fixed.png)

Klicken Sie **der Zeile auf** Live anzeigen“, um eine schreibgeschützte Ansicht des **aktuellen Seiteninhalts** zu öffnen, der zur Überprüfung bereitgestellt wird (einschließlich vereinfachter Passagen, falls angewendet). Verwenden Sie **Details** für die Analyse.

![Live anzeigen - aktueller Seiteninhalt einschließlich vereinfachtem Text für Agenten](/help/dashboards/opportunities/assets/simplify-complex-content-view-live.png)

Wenn Sie Edge-Änderungen stapelweise rückgängig machen müssen, wählen Sie die optimierten Zeilen mithilfe der Kontrollkästchen aus und verwenden Sie dann **Rollback** in der Kopfzeile.

![Es wurden Vorschläge korrigiert, bei denen die bereitgestellte Zeile erweitert, der Status optimiert und das Rollback in der Kopfzeile angezeigt wurde](/help/dashboards/opportunities/assets/simplify-complex-content-rollback.png)

## Rollback

Wenn Sie es sich anders überlegen, können Sie jede bereitgestellte Optimierung zurücksetzen. Wählen Sie in **Ansicht** Feste Vorschläge“ die optimierten Zeilen aus, die Sie zurücksetzen möchten, und klicken Sie dann auf **Rollback** in der Kopfzeile.

Im Dialogfeld **Rollback** werden die Vorschläge aufgelistet, für die ein Rollback durchgeführt wird, mit einer kurzen Warnung, dass bereitgestellte Optimierungen zurückgesetzt werden. Bestätigen Sie die Liste und klicken Sie dann auf **Rollback** oder **Abbrechen**.

![Dialogfeld „Rollback“ mit Vorschlägen zum Zurücksetzen](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-dialog.png)

Nach Abschluss des Vorgangs wird eine Zusammenfassung **Erfolgreich zurückgesetzt** angezeigt. Schließen Sie sie, um zum Dashboard zurückzukehren.

![Rollback abgeschlossen - Rollback erfolgreich durchgeführt](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-confirm.png)

## Ausprobieren in der Demo

Erfahren Sie mehr über den Workflow zur Vereinfachung komplexer Inhalte in der [Frescopa-](https://play.llmo.now/org/demo-org)&quot;.
