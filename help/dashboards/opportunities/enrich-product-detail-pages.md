---
title: Anreicherung der Produktdetailseite
description: Erfahren Sie, wie LLM Optimizer Produktseiten identifiziert, auf denen Katalogdaten vor KI-Agenten verborgen sind, und wie Sie diese Sichtbarkeit mithilfe von Edge-basierter Optimierung und Produktkatalogeinblicken auf der Grundlage von Adobe Commerce wiederherstellen können.
feature: Opportunities
source-git-commit: c0e4c82a5eedd864d654557173dd1dcfa5b78362
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 0%

---


# Anreichern von Produktdetailseiten

KI-Agenten können nur Produkte empfehlen, die sie vollständig verstehen. In den meisten Commerce-Storefronts sind Produktseiten für menschliche Käufer konzipiert. Diese Produkte basieren auf von JavaScript gerenderten Registerkarten, erweiterbaren Bedienfeldern, Shopping-Assistenten, interaktiven Modalen und Links zu oberflächennahen Produktvarianten, Spezifikationen und Funktionen. KI-Agenten analysieren die Tiefen der Produktdetailseite nicht. Das bedeutet, dass diese umfangreichen Produktdaten von den LLM-Crawler nicht gesehen werden, die die KI-gesteuerte Erkennung antreiben, selbst wenn sie für menschliche Besucher vollständig sichtbar sind.

Die Opportunity Produktdetailseiten anreichern identifiziert Produktseiten in Ihrem Adobe Commerce-Katalog, auf denen diese Sichtbarkeitslücke besteht. Basierend auf dem Adobe Commerce-Katalog vergleicht er, auf welche KI-Agenten in der Storefront zugreifen können, mit den vollständigen Produktdaten in Ihrem Katalog und zeigt alle Attribute, Varianten und die Tiefe Ihrer Produktmerkmale an, die in der Ansicht des KI-Agenten fehlen.

Sie zeigt die folgenden Schlüsselmetriken auf einen Blick:

- **Produktseiten** - Die Liste aller Produktdetailseiten, die mit einer Sichtbarkeitslücke bei Katalogdaten identifiziert wurden.
- **Agentenverkehr** - Die Gesamtzahl der Besuche und Interaktionen auf einer Site, die von autonomen KI-Agenten (wie LLM-gestützten Assistenten oder Bots) initiiert und gesteuert werden, die im Namen von Benutzern handeln, um Inhalte zu entdecken, abzurufen oder mit ihnen zu interagieren.

![Dashboard „Produktdetailseiten anreichern“](/help/dashboards/opportunities/assets/enrich-product-detail-pages-overview.png)

Diese Opportunity kann mithilfe von „Optimieren [ Edge&quot; optimiert ](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge). Optimierungen werden ausschließlich an KI-Agenten bereitgestellt, haben keine Auswirkungen auf Besucherinnen und Besucher (Bot-only-Bereitstellung), werden auf der CDN-Ebene ohne erforderliche CMS- oder Katalogänderungen angewendet und können innerhalb von Minuten ohne Entwicklerinteraktion wirksam werden. Dies macht sie zu einem schnellen Bereitstellungspfad mit geringem Risiko für große Produktkataloge.

## Funktionsweise

Der Adobe Commerce-Katalogagent liest Ihre gesamten Produktkatalogdaten, einschließlich Varianten, vertiefter Produktbeziehungen, Attributen, Facetten, Kategoriemetadaten und aller Produktmerkmale. Anschließend werden die Daten mit dem verglichen, auf was tatsächlich für KI-Agenten in der entsprechenden Storefront-PDP zugegriffen werden kann. Seiten, auf denen Katalogdaten aus KI-Crawler ausgeblendet sind, werden in der **URLs mit Vorschlägen** angezeigt, die nach dem agenten Traffic-Volumen priorisiert sind.

Für jede betroffene Produktseite bietet LLM Optimizer Folgendes:

- **KI-Analysevorschau** - Eine vollständige Liste der Kataloginformationen, die in der KI-Agentenansicht fehlen und warum sie für die LLM-gesteuerte Produkterkennung wichtig sind, einschließlich einer Liste wiederherstellbarer Datenpunkte wie Produktvarianten, Größenoptionen, Materialspezifikationen und Kompatibilitätsdetails.

Die Fehlerbehebung erfolgt mit [Optimieren bei Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge) - der Edge-basierten Bereitstellungsfunktion von Adobe, die eine vollständig vorgerenderte, KI-freundliche HTML-Momentaufnahme für LLM-Benutzeragenten auf CDN-Ebene bereitstellt. Dadurch werden alle zuvor ausgeblendeten Katalogdaten (einschließlich Produktvarianten, technischen Spezifikationen und Funktionsdetails) wiederhergestellt, ohne den Commerce-Katalog oder die für Menschen sichtbare Storefront-Benutzeroberfläche zu berühren.

![URLs mit Vorschlagstabelle](/help/dashboards/opportunities/assets/enrich-product-detail-pages-suggestions.png)

## URLs mit Vorschlägen

Die Tabelle **URLs mit**&quot; listet alle identifizierten Produktseiten auf, für die eine Optimierung vorteilhaft ist. Für jede Produkt-URL haben Sie folgende Möglichkeiten:

- **Vorschau** um die KI-Analyse anzuzeigen, einschließlich der fehlenden Kataloginformationen und der Gründe, warum sie für die KI-gesteuerte Auffindbarkeit wichtig sind
- **Als behoben markieren** sobald die Optimierung bereitgestellt und validiert wurde
- **Ignorieren** Vorschläge, die für Ihre Merchandising-Strategie nicht relevant sind

Die Vorschläge sind in drei Ansichten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**. Sobald ein Vorschlag bereitgestellt wurde, wechselt er zu Feste Vorschläge mit dem Status **Optimiert** und zu einer **Live anzeigen**-Aktion, um zu überprüfen, ob die Anreicherung für agenten Traffic live ist. Feste Vorschläge können jederzeit zurückgesetzt werden.

## Bereitstellen der Optimierung

Nachdem Sie die Vorschläge geprüft und die zu optimierenden Produktseiten ausgewählt haben, klicken Sie auf **Optimierungen bereitstellen**, um die Anreicherung am CDN-Edge zu veröffentlichen. In **Bestätigungsdialogfeld „Für Edge bereitstellen** werden die ausgewählten Produkt-URLs, der Optimierungstyp und die angewendete Anreicherung angezeigt. Nach der Bereitstellung wird in einem Bestätigungsbildschirm bestätigt, welche Produktseiten erfolgreich optimiert wurden.

Die Optimierung wird ausschließlich KI-Benutzeragenten über die CDN-Edge-Ebene bereitgestellt. Besuchende sehen Ihr bestehendes Storefront-Erlebnis weiterhin genau wie zuvor, ohne dass sich Ihr PDP-Design, Ihre Seitenleistung oder Ihr Markenerlebnis ändern.

>[!NOTE]
>
>Für die Bereitstellung von Optimierungen ist es erforderlich, (1) LLM Optimizer mit Adobe Commerce zu verbinden und (2) den Onboarding-Prozess „Optimieren bei Edge&quot; abzuschließen.

Wenn Ihre Commerce-Instanz noch nicht mit LLM Optimizer verbunden ist, werden Sie zur Verbindungseinrichtung weitergeleitet, bevor Anreicherungen angewendet werden können.

Wenn Sie noch nicht eingestiegen sind, werden Sie durch Klicken auf **Optimierungen bereitstellen** zum Onboarding-Prozess weitergeleitet. Ausführliche Informationen zur Funktionsweise von „Optimieren bei Edge&quot;, zu unterstützten CDN-Anbietern und zum Onboarding-Prozess finden Sie auf der Seite [Optimieren bei Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge).

![Dialogfeld „Für Edge bereitstellen“](/help/dashboards/opportunities/assets/enrich-product-detail-pages-deploy.png)

## In der Demo ausprobieren

Sehen Sie sich die Opportunity Produktdetailseiten anreichern mithilfe der Demo-Umgebung von Frescopa in Aktion an.

[Sehen Sie sich die Demo „Anreichern von Produktdetailseiten“ im Frescopa an](https://play.llmo.now/org/demo-org/opportunities/commerce-product-page-enrichment/4e8b0428-0893-4864-a00e-fc1d77fb3372?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Häufig gestellte Fragen

**Warum sind meine Produktkatalogdaten vor KI-Agenten verborgen?**

Commerce-Storefronts sind für Käufer gedacht. Produkteigenschaften, Varianten, Größenoptionen, Materialdetails und andere technische Spezifikationen werden häufig durch JavaScript-gesteuerte Interaktionen wie Registerkarten, ausblendbare Bedienfelder, Popup-Modale, Links und Einkaufs-Assistenten angezeigt. KI-Agenten analysieren die Tiefen der Produktdetailseite nicht, sodass alle diese Daten für LLM-Crawler nicht sichtbar sind, selbst wenn sie vollständig in Ihrem Produktkatalog vorhanden sind. Das Ergebnis ist, dass KI-Agenten Produktempfehlungen basierend auf einem Bruchteil der tatsächlichen Produktinformationen bereitstellen.

**Welche Arten von Produktdaten werden bei dieser Optimierung wiederhergestellt?**

Der Katalogagent ruft alle im Adobe Commerce-Katalog verfügbaren Produktinformationen ab, auf die derzeit nicht in der Storefront für KI-Agenten zugegriffen werden kann. Dazu gehören Produktmerkmale, Beziehungen, Varianten (Größen, Farben, Konfigurationen), technische Spezifikationen und Attribute, Kompatibilitätsdetails, Kategoriemetadaten und Facettenwerte.

**Wird sich diese Optimierung auf meine menschlichen Besucher, SEO-Bots oder die Leistung meiner Storefront auswirken?**

Nein. Bei Edge optimieren werden nur KI-Benutzeragenten berücksichtigt. Besuchende und SEO-Bots erhalten die ursprüngliche Produktseite genau wie zuvor, ohne Änderungen an ihrem Erlebnis, ihrer Seitenladeleistung oder ihrem Storefront-Design.

**Muss ich meinen Commerce-Katalog, CMS, ändern oder Entwickler einbeziehen?**

Nein. Die Optimierung wird auf der CDN-Edge-Ebene angewendet und erfordert keine Änderungen am Adobe Commerce-Katalog, keine Code-Bereitstellungen und keine Interaktion mit Entwicklern. Nach dem Onboarding von Optimizer bei Edge können Sie Anreicherungen direkt in der LLM Optimizer-Benutzeroberfläche bereitstellen und in Minuten zurücksetzen.

**Was passiert, wenn sich meine Produktdaten nach der Bereitstellung ändern?**

Für die Möglichkeit, Produktdetailseiten anzureichern, verwendet LLM Optimizer TTL-Einstellungen mit niedrigem Cache, damit jede Produktaktualisierung in Ihrem Commerce-Katalog innerhalb von Minuten eine Aktualisierung Trigger hat. KI-Agenten erhalten immer die aktuellsten verfügbaren Produktdaten.
