---
title: Produktkataloganreicherung
description: Erfahren Sie, wie LLM Optimizer Produkte mit generischen oder technisch dichten Beschreibungen identifiziert und wie Sie diese mithilfe von KI-generierten Erzählungsanreicherungen, die von Adobe Commerce unterstützt werden, verbessern können.
feature: Opportunities
autotag-review: '2026-05-15T17:45:51.619Z'
TQID: 'https://experienceleague.adobe.com/5ihGQ8L-37uWsZSDo4TVCUPBPqsqqQ5waGbH3VKPIig'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 0%

---


# Produktkatalog anreichern

LLMs versuchen, Produktattribute mit dem realen Wert, Anwendungsfällen und dem Kundenwunsch zu verbinden. Wenn Produktnamen und -beschreibungen diesen Wert nicht klar kommunizieren, ist es weniger wahrscheinlich, dass Ihre Produkte in der KI-gestützten Erkennung zitiert, empfohlen oder angezeigt werden. Das liegt daran, dass KI-Agenten über Beziehungen und nicht über Rohdatenfelder argumentieren. Eine Produktliste mit einem Namen wie „Kaffeemühle X200“ und einer Beschreibung mit technischen Spezifikationen (Motorleistung, Mahleinstellungen usw.) gibt einem LLM sehr wenig zu arbeiten, wenn ein Käufer nach „der besten Espressomühle für ein Zuhause Barista“ fragt.

Die Opportunity zur Produktkataloganreicherung identifiziert Produkte in Ihrem Commerce-Katalog, bei denen Namen und Beschreibungen zu generisch, zu technisch kompakt oder zu mehrdeutig sind, um von LLMs korrekt interpretiert zu werden. Basierend auf Adobe Commerce generiert es erzählerische, absichtsreiche Anreicherungen für Ihre Produktnamen und Beschreibungen und wendet sie mit einem einzigen Klick direkt auf Ihren Commerce-Katalog an.

Sie zeigt zwei Schlüsselmetriken auf einen Blick:

- **URLs** - Eine Liste der Produktdetailseiten (Produkte in Ihrem Katalog), die auf Anreicherungsqualität bewertet wurden.
- **Agentenverkehr** - Die Gesamtzahl der Besuche und Interaktionen auf einer Site, die von autonomen KI-Agenten (wie LLM-gestützten Assistenten oder Bots) initiiert und gesteuert werden, die im Namen von Benutzern handeln, um Inhalte zu entdecken, abzurufen oder mit ihnen zu interagieren.

![Produktkatalog-Dashboard anreichern](/help/dashboards/opportunities/assets/enrich-product-catalog-overview.png)

>[!NOTE]
>
>Diese Opportunity befindet sich derzeit in Beta und kann von Adobe Commerce-Kunden aktiviert werden. Wenden Sie sich an Ihren Kundenbetreuer, um Zugang zur Beta-Version zu erhalten.

## Funktionsweise

Der Adobe Commerce-Katalogagent liest Ihre Produktkatalogdaten und analysiert jede Produkt-SKU - einschließlich aller technischen Attribute, des Kategoriekontexts, der Varianten sowie des bestehenden Namens und der Beschreibung. Es kennzeichnet Produkte, bei denen der aktuelle Name oder die aktuelle Beschreibung den Wert für den Kunden nicht kommunizieren, und generiert eine angereicherte Alternative, die technische Details in eine klare, zielgerichtete Sprache übersetzt.

Beispielsweise kann ein Produkt mit dem Namen *„Kaffeemühle X200“* mit der Beschreibung „18 Mahleinstellungen, 450W-Motor“ angereichert werden, um zu erklären, dass „der X200 eine Espresso-Konsistenz auf Café-Ebene liefert, da sein 18-stufiges Mahlsystem mit einem Motor mit hohem Drehmoment kombiniert, um wiederholbare Ergebnisse zu Hause zu erzielen“. Attribute wie Preis und Inventar werden absichtlich von der Anreicherung ausgeschlossen. Der Catalog Agent konzentriert sich auf wertsteigernde Attribute, die erklären, was das Produkt ist, wie es verwendet wird und warum es für einen Käufer wichtig ist.

Produkte mit Anreicherungsvorschlägen werden in der Tabelle **URLs mit Vorschlägen** angezeigt, die nach der Anreicherungswirkung priorisiert sind. Für jedes identifizierte Produkt bietet LLM Optimizer Folgendes:

- **Aktueller Name** - Der bestehende Produktname, wie er in Ihrem Adobe Commerce-Katalog angezeigt wird.
- **Aktualisierter Name** - Der von KI generierte, wertgesteuerte Produktname, der den LLMs den kundenrelevanten Kontext und die Absicht mitteilt.
- **Aktuelle Beschreibung** - Die vorhandene Produktbeschreibung, wie sie in Ihrem Adobe Commerce-Katalog angezeigt wird.
- **Vorgeschlagene Beschreibung** - Die von KI generierte Beschreibung, die die technischen Attribute Ihres Produkts in eine Erzählung übersetzt, die LLMs hilft zu verstehen, was das Produkt ist, welchen Erzählungswert es hat und warum es wichtig ist.

![Produkte mit Vorschlagstabelle](/help/dashboards/opportunities/assets/enrich-product-catalog-suggestions.png)

## Produkte mit Vorschlägen

Die Tabelle **URLs mit**&quot; listet alle Produkte mit Anreicherungsmöglichkeiten auf. Für jedes Produkt haben Sie folgende Möglichkeiten:

- **Erweitern Sie die Zeile** um die KI-Analyse und die vorgeschlagene Anreicherung anzuzeigen.
- **Bearbeiten** Sie den vorgeschlagenen Produktnamen oder die Beschreibung, bevor Sie sie anwenden, um sie an Ihre Markensprache und Ihre Merchandising-Richtlinien anzupassen.
- **Stellen Sie die** für die Produkte bereit, die Sie anreichern möchten, und veröffentlichen Sie sie direkt in Ihrem Adobe Commerce-Katalog.
- **Als behoben markieren** sobald die Anreicherung überprüft und angewendet wurde.
- **Ignorieren** Vorschläge, die für Ihre Katalogstrategie nicht relevant sind.

Die Vorschläge sind in drei Ansichten unterteilt: **Aktuelle Vorschläge**, **Feste** und **Ignorierte Vorschläge**. Sobald eine Anreicherung angewendet wird, wechselt sie zu Feste Vorschläge mit dem Status **Angewendet** und zu einer **Im Katalog anzeigen** Aktion, um die Aktualisierung in Adobe Commerce zu überprüfen. Angewendete Anreicherungen können jederzeit zurückgesetzt werden, wodurch der ursprüngliche Produktname und die ursprüngliche Beschreibung wiederhergestellt werden.

<!--[Fixed suggestions with Applied status](/help/dashboards/opportunities/assets/enrich-product-catalog-fixed.png)-->

## Bereitstellen der Optimierung

Nachdem Sie die Vorschläge für Ihre ausgewählten Produkte geprüft und optional bearbeitet haben, klicken Sie auf **Optimierungen bereitstellen**, um den aktualisierten Produktnamen und die aktualisierte Beschreibung in Ihrem Adobe Commerce-Katalog zu veröffentlichen. Ein Bestätigungsdialogfeld zeigt die ausgewählten Produkte und die vorgenommenen Änderungen an. Nach der Bestätigung wird in einem Ergebnisbildschirm bestätigt, welche Produkte erfolgreich aktualisiert wurden.

Da Anreicherungen direkt auf den Adobe Commerce-Katalog angewendet werden, sind die aktualisierten Produktnamen und Beschreibungen sofort auf allen Kanälen verfügbar, die Ihren Katalog verwenden - einschließlich Ihrer Storefronts, Anzeigen-Feeds und aller direkten LLM-Produktintegrationen. Dadurch wird sichergestellt, dass jede Oberfläche, auf der Ihr Produkt erscheint, konsistente und hochwertige Informationen kommuniziert.

>[!NOTE]
>
>Zur Kataloganreicherung muss LLM Optimizer mit Adobe Commerce verbunden sein. Wenn Ihre Commerce-Instanz noch nicht mit LLM Optimizer verbunden ist, werden Sie zur Verbindungseinrichtung weitergeleitet, bevor Anreicherungen angewendet werden können.

![Dialogfeld Anreicherungen anwenden](/help/dashboards/opportunities/assets/enrich-product-catalog-deploy.png)

## In der Demo ausprobieren

Sehen Sie sich die Opportunity Produktkatalog anreichern mithilfe der Demo-Umgebung von Frescopa in Aktion an.

[Anzeigen des Produktkatalogs „Anreichern“ in der Frescopa-Demo](https://play.llmo.now/org/demo-org/opportunities/commerce-product-catalog-enrichment/e5f2a854-7477-421c-820f-74d5dd595647?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Häufig gestellte Fragen

**Warum schaden generische Produktnamen und Beschreibungen der KI-Auffindbarkeit?**

LLMs stimmen nicht mit Produkten mit Kundenabfragen überein, indem nach Schlüsselwortüberschneidungen gesucht wird. Sie denken über Beziehungen nach, verbinden das, was ein Käufer zu finden beabsichtigt, mit dem, was ein Produkt tatsächlich tut, wofür es ist und wie es im Vergleich zu Alternativen aussieht. Ein Produktname oder eine Produktbeschreibung, der bzw. die technische Spezifikationen auflistet, ohne den realen Wert zu kommunizieren, gibt einem LLM nur sehr wenig Kontext, mit dem er arbeiten kann. Das Ergebnis ist, dass Ihr Produkt seltener zitiert wird, wenn ein Käufer eine relevante Frage stellt, selbst wenn Ihr Produkt für seine Bedürfnisse am besten geeignet ist.

**Welche Produktattribute verwendet der Katalogagent, um Anreicherungen zu generieren?**

Der Catalog Agent verwendet wertsteigernde Attribute in Ihrem Commerce-Katalog, die LLMs dabei helfen zu verstehen, was ein Produkt ist, wie es verwendet wird und warum es wichtig ist. Wertsteigernde Attribute wie Produktmerkmale, Anwendungsfälle, Materialeigenschaften, Kategoriekontext und Kompatibilitätsdetails. Attribute wie Preis- und Lagerbestände werden absichtlich ausgeschlossen, da sie nicht zum semantischen Produktverständnis beitragen und Beschreibungen bei veränderten Bedingungen weniger haltbar machen können.

**Kann ich die KI-generierte Anreicherung bearbeiten, bevor ich sie anwende?**

Ja. Jeder Vorschlag enthält eine bearbeitbare Vorschau des vorgeschlagenen Produktnamens und der Beschreibung. Sie können die Anreicherung ändern, um sie an Ihre Markensprache anzupassen, alle Ungenauigkeiten zu korrigieren oder zusätzlichen Kontext einzubinden, bevor Sie ihn auf Ihren Katalog anwenden.

**Wird die Anreicherung das ändern, was menschliche Besucher auf meiner Storefront sehen?**

Ja, Besucher sehen den aktualisierten Produktnamen und die aktualisierte Beschreibung in der Storefront zusammen mit allen anderen Kanälen, die aus Ihrem Commerce-Katalog bezogen werden. Dies ist beabsichtigt: Ziel ist es, zu verbessern, wie Ihr Produkt überall verstanden wird, nicht nur von KI-Agenten und auch um Cloaking-Risiken zu vermeiden.

**Was passiert über meine anderen Vertriebskanäle, wenn ich eine Anreicherung anwende?**

Da die Anreicherung direkt in Ihren Adobe Commerce-Katalog geschrieben wird, wird sie automatisch auf alle Kanäle übertragen, die Ihren E-Commerce-Katalog als deren Wahrheitsquelle verwenden, einschließlich mehrerer Storefronts, Werbe-Pipelines und direkter LLM-Produkt-Feeds. Dadurch wird Markenkonsistenz und kohärente Produktinformationen für LLMs sichergestellt, die das Internet für Ihre Produkte crawlen haben.

**Kann ich eine Anreicherung zurücksetzen, wenn ich mit dem Ergebnis nicht zufrieden bin?**

Ja. Ein Rollback der angewendeten Anreicherungen kann jederzeit über die Ansicht Feste Vorschläge ausgeführt werden, wodurch der ursprüngliche Produktname und die ursprüngliche Beschreibung in Ihrem Adobe Commerce-Katalog wiederhergestellt werden.
