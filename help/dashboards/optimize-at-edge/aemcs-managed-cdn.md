---
title: Optimize at Edge – Von AEM Cloud Service verwaltetes CDN (Fastly)
description: Erfahren Sie, wie Sie das von AEM Cloud Service verwaltete CDN (Fastly) für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
source-git-commit: 184d6008c2579014c6ff453e8bfff4bb898f4b82
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 20%

---


# Von AEM Cloud Service verwaltetes CDN (Fastly)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header-`x-edgeoptimize-request-id`.

## Voraussetzungen

Zugriff auf diese Funktion:

- Bezahlte Kundinnen und Kunden müssen Zugriff auf das **IMS**&#x200B;Produktprofil von Adobe LLM Optimizer-Benutzenden haben. Wenden Sie sich an den Administrator Ihres Unternehmens, um Zugriff anzufordern.
  ![Benutzer zu einem Produktprofil hinzufügen](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- Testkunden müssen zur IMS-Gruppe **LLMO**) gehören. Wenn die Gruppe nicht vorhanden ist, kann der Administrator Ihres Unternehmens sie erstellen und Sie hinzufügen.
  ![Erstellen der LLMO-Admin-IMS-Gruppe](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Diese Funktion wird in Safari oder im Inkognito-/privaten Browser-Modus nicht unterstützt.

## Schritte zum Aktivieren des Routings

Weiterleiten von Agent-basiertem Traffic an Edge Optimize:

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus.

   ![Navigieren zu „Kundenkonfiguration“](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Suchen Sie den Abschnitt **Optimierungen für KI-Agenten bereitstellen**. Klicken Sie auf die **Aktivieren**.

   ![Optimierungen für KI-Agenten bereitstellen - Ausstehend](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Wählen Sie im Bestätigungsdialog die Option **Aktivieren** aus, um zu bestätigen, dass Sie das Routing aktivieren möchten. Wenn ein Fehler auftritt, finden Sie weitere Informationen zur Behebung [&#x200B; Fehlers &#x200B;](#troubleshooting) Abschnitt „Fehlerbehebung“.

   ![Bestätigungsdialogfeld für Optimierungsmodul aktivieren](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Nach der Bestätigung dauert das Routing einige Minuten.

   ![Routing läuft](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Laden Sie die Seite nach 5 Minuten neu, um zu überprüfen, ob das Routing abgeschlossen ist. Sobald das Routing konfiguriert und aktiv ist, wird der Status auf **Abgeschlossen** mit einem grünen Häkchen aktualisiert, das bestätigt, dass das Routing aktiviert ist. Ihrerseits sind keine weiteren Maßnahmen erforderlich.

   ![Optimierung für KI-Agenten bereitstellen - abgeschlossen](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Um das Routing jederzeit zu deaktivieren, kehren Sie zum Abschnitt **Bereitstellen von Optimierungen für KI** Agenten“ auf der Registerkarte **CDN-Konfiguration** zurück und klicken Sie auf **Deaktivieren**.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich an Ihr Adobe-Accountteam oder an `llmo-at-edge@adobe.com`.

## Fehlerbehebung

Wenn beim Aktivieren oder Deaktivieren des Routings ein Fehler auftritt, sieht dies in etwa wie folgt aus:

![Fehler beim Bestätigungsdialogfeld](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Verwenden Sie die folgende Liste, um den Fehler zu identifizieren, und befolgen Sie die Anweisungen.

1. **Benutzer hat keinen LLMO-Produktzugriff**

   **Ursache:** Das Benutzerkonto hat den LLM Optimizer-Produktkontext nicht in Ihrem Adobe IMS-Profil. Dies ist für gebührenpflichtige Kunden erforderlich, um CDN-Routing zu konfigurieren.

   **Empfehlung:** Überprüfen Sie, ob Ihnen das Produktprofil **Adobe LLM Optimizer-Benutzer** in Adobe Admin Console von Ihrem Organisationsadministrator zugewiesen wurde.

2. **Nur Mitglieder der LLMO-Administratorgruppe können CDN-Routing konfigurieren**

   **Ursache:** Ihr Konto ist kein Mitglied der IMS-Gruppe **LLMO Admin**. Dies ist für Testkunden erforderlich, um das CDN-Routing zu konfigurieren.

   **Empfehlung:** Vergewissern Sie sich, dass Sie der IMS-Gruppe **LLMO Admin** in Adobe Admin Console von Ihrem Organisationsadministrator hinzugefügt wurden.

3. **Der angeforderte CDN-Typ aem-cs-fastly stimmt nicht mit dem für diese Domain erkannten CDN überein**

   **Ursache:** Dies zeigt an, dass der für Ihre Site erkannte CDN-Typ nicht *AEM Cloud Service Managed CDN (Fastly)* ist.

   **Empfehlung:** Stellen Sie sicher, dass Ihre Site über AEM Cloud Service Managed CDN (Fastly) bereitgestellt wird.

4. **Fehlersuchort**

   **Ursache:** LLM Optimizer konnte Ihre Site während der Routing-Einrichtung nicht erreichen. Dies kann vorkommen, wenn die Site ausgefallen ist, nicht erreichbar ist oder die Anfrage eine Zeitüberschreitung aufweist.

   **Empfehlung:** Stellen Sie sicher, dass Ihre Site öffentlich zugänglich ist, und geben Sie eine gültige Antwort zurück, und versuchen Sie es dann erneut.

5. **Site hat keine gültige Antwort für den Routing-Test zurückgegeben**

   **Ursache:** Die Site hat beim Testen während des Setups einen unerwarteten HTTP-Status (nicht 2xx oder 301) zurückgegeben.

   **Empfehlung:** Überprüfen Sie, ob Ihre Site eine erfolgreiche Antwort (2xx) für die in LLM Optimizer registrierte Basis-URL zurückgibt, und versuchen Sie es dann erneut.

6. **Die Authentifizierung beim Upstream-IMS-Service ist fehlgeschlagen**

   **Ursache:** Die Sitzung ist möglicherweise abgelaufen oder bei der Authentifizierung bei Adobe IMS ist während der Routing-Anfrage ein Problem aufgetreten.

   **Empfehlung:** Melden Sie sich von LLM Optimizer ab, melden Sie sich wieder an und versuchen Sie dann erneut, das Routing zu aktivieren.

Wenn das Problem weiterhin besteht, wenden Sie sich an Ihr Adobe-Account-Team oder Ihren `llmo-at-edge@adobe.com`.

## (Optional) Überprüfen Sie die Einrichtung

Nachdem die Routing-Konfiguration abgeschlossen ist, können Sie optional überprüfen, ob der AI-Bot-Traffic an Edge Optimize weitergeleitet wird und ob der menschliche Traffic nicht betroffen ist.

1. **Bot-Traffic testen (sollte optimiert werden)**

   Simulieren Sie eine KI-Bot-Anfrage mithilfe eines Agent-basierten Benutzer-Agents:

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: chatgpt-user"
   ```

   Eine erfolgreiche Antwort enthält den `x-edgeoptimize-request-id`-Header, der bestätigt, dass die Anfrage über Edge Optimize weitergeleitet wurde:

   ```
   < HTTP/2 200
   < x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
   ```

2. **Testen Sie den menschlichen Traffic (sollte NICHT betroffen sein)**

   Simulieren Sie eine normale menschliche Browser-Anfrage:

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
   ```

   Die Antwort sollte die `x-edgeoptimize-request-id`-Kopfzeile nicht enthalten. Der Seiteninhalt und die Antwortzeit sollten nach der Aktivierung von „Optimize at Edge“ unverändert bleiben.

3. **Wie kann zwischen den beiden Szenarien unterschieden werden**

   | Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Traffic (nicht betroffen) |
   |---|---|---|
   | `x-edgeoptimize-request-id` | Vorhanden – enthält eine eindeutige Anfrage-ID | Abwesend |
   | `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover stattgefunden hat (Wert: `1`) | Abwesend |

4. **Routing-Status in LLM Optimizer überprüfen**

   Sie können das Routing auch in der Benutzeroberfläche von LLM Optimizer bestätigen. Öffnen Sie **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus. Wenn das Routing aktiv ist, wird im Abschnitt **Optimierungen für KI-** bereitstellen“ **Abgeschlossen** angezeigt.

   ![Optimierung für KI-Agenten bereitstellen - abgeschlossen](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
