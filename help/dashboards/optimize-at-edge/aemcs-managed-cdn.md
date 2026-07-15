---
title: Optimize at Edge – Von AEM Cloud Service verwaltetes CDN (Fastly)
description: Erfahren Sie, wie Sie das von AEM Cloud Service verwaltete CDN (Fastly) für „Optimize at Edge“ in LLM Optimizer konfigurieren.
feature: Opportunities
autotag-review: '2026-07-15T16:49:32.275Z'
TQID: 'https://experienceleague.adobe.com/2-IzfF1iTEzW-gpqPA-t3mffRuhMxaKi1Dp0A62IZ9U'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadcid: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 836
ht-degree: 100%

---


# Von AEM Cloud Service verwaltetes CDN (Fastly)

Diese Konfiguration leitet den Agent-basierten Traffic (Anfragen von KI-Bots und LLM-Benutzer-Agents) an den Backend-Service von Edge Optimize (`live.edgeoptimize.net`) weiter. Menschliche Besuchende und SEO-Bots werden weiterhin wie gewohnt von Ihrem Ursprung aus unterstützt. Um die Konfiguration zu testen, suchen Sie nach Abschluss der Einrichtung in der Antwort nach dem Header `x-edgeoptimize-request-id`.

## Voraussetzungen

Zugreifen auf diese Funktion:

- Zahlende Kundschaften müssen Zugriff auf das IMS-Produktprofil **Adobe LLM Optimizer-Benutzende** haben. Wenden Sie sich an die bzw. den Admin Ihrer Organisation, um Zugriff anzufordern.
  ![Hinzufügen von Benutzenden zu einem Produktprofil](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- Kundschaften mit der Testversion müssen Teil der IMS-Gruppe **LLMO-Admin** sein. Wenn die Gruppe nicht vorhanden ist, kann die bzw. der Admin Ihres Unternehmens sie erstellen und Sie hinzufügen.
  ![Erstellen der IMS-Gruppe „LLMO-Admin“](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Diese Funktion wird in Safari oder im Inkognito-/privaten Browser-Modus nicht unterstützt.

## Schritte zum Aktivieren des Routings

Weiterleiten von Agent-basiertem Traffic an Edge Optimize:

1. Öffnen Sie in LLM Optimizer **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration**.

   ![Navigieren zu „Kundenkonfiguration“](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Suchen Sie den Abschnitt **Optimierungen für AI Agents bereitstellen**. Klicken Sie auf die Schaltfläche **Aktivieren**.

   ![Optimierungen für AI Agents bereitstellen – ausstehend](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Wählen Sie im Bestätigungsdialogfeld die Option **Aktivieren** aus, um zu bestätigen, dass Sie das Routing aktivieren möchten. Wenn ein Fehler auftritt, finden Sie im Abschnitt [Fehlerbehebung](#troubleshooting) Informationen zum Lösen dieses Fehlers.

   ![Bestätigungsdialog „Optimierungs-Engine aktivieren“](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Das Abschließen des Routings kann nach der Bestätigung einige Minuten dauern.

   ![Routing im Gange](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Laden Sie die Seite nach 5 Minuten neu, um zu überprüfen, ob das Routing abgeschlossen ist. Sobald das Routing konfiguriert und aktiv ist, wird der Status auf **Abgeschlossen** aktualisiert und es wird ein grünes Häkchen angezeigt, das bestätigt, dass das Routing erfolgreich aktiviert wurde. Ihrerseits sind keine weiteren Maßnahmen erforderlich.

   ![Optimierungen für AI Agents bereitstellen – abgeschlossen](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Um das Routing jederzeit zu deaktivieren, kehren Sie zum Abschnitt **Optimierungen für AI Agents bereitstellen** in der Registerkarte **CDN-Konfiguration** zurück und klicken Sie auf **Deaktivieren**.

Wenn Sie Hilfe zu den oben genannten Schritten benötigen, wenden Sie sich an Ihr Adobe-Accountteam oder an `llmo-at-edge@adobe.com`.

## Fehlerbehebung

Wenn beim Aktivieren oder Deaktivieren des Routings ein Fehler auftritt, wird dies etwa wie folgt angezeigt:

![Bestätigungsdialogfeld bei Fehler](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Verwenden Sie die folgende Liste zum Identifizieren des Fehlers und befolgen Sie die Anweisungen.

1. **Person hat keinen LLMO-Produktzugriff**

   **Ursache:** Das Benutzerkonto verfügt nicht über den LLM Optimizer-Produktkontext in Ihrem Adobe IMS-Profil. Dies ist für zahlende Kundschaften erforderlich, um CDN-Routing zu konfigurieren.

   **Empfehlung:** Stellen Sie sicher, dass Ihnen das Produktprofil **Adobe LLM Optimizer-Benutzende** in Adobe Admin Console von Ihrer bzw. Ihrem Organisationsadmin zugewiesen wurde.

2. **Nur Mitglieder der Gruppe „LLMO-Admin“ können CDN-Routing konfigurieren**

   **Ursache:** Ihr Konto ist kein Mitglied der IMS-Gruppe **LLMO-Admin**. Dies ist für Nutzende der Testversion erforderlich, um CDN-Routing zu konfigurieren.

   **Empfehlung:** Stellen Sie sicher, dass Sie der IMS-Gruppe **LLMO-Admins** in Adobe Admin Console hinzugefügt wurden.

3. **Der angeforderte CDN-Typ „aem-cs-fastly“ stimmt nicht mit dem für diese Domain erkannten CDN überein**

   **Ursache:** Dies bedeutet dass der für Ihre Site erkannte CDN-Typ nicht *AEM Cloud Service Managed CDN (Fastly)* ist.

   **Empfehlung:** Stellen Sie sicher, dass Ihre Site über AEM Cloud Service Managed CDN (Fastly) bereitgestellt wird.

4. **Fehler beim Testen der Site**

   **Ursache:** LLM Optimizer konnte Ihre Site während der Routing-Einrichtung nicht erreichen. Dies kann vorkommen, wenn die Site ausgefallen, unerreichbar oder ein Timeout der Anfrage aufgetreten ist.

   **Empfehlung:** Stellen Sie sicher, dass Ihre Site öffentlich zugänglich ist und eine gültige Antwort zurückgibt, und versuchen Sie es dann erneut.

5. **Site hat keine gültige Antwort für den Routing-Test zurückgegeben**

   **Ursache:** Die Site hat beim Testen während der Einrichtung einen unerwarteten HTTP-Status (nicht 2xx oder 301) zurückgegeben.

   **Empfehlung:** Stellen Sie sicher, dass Ihre Site eine erfolgreiche Antwort (2xx) für die in LLM Optimizer registrierte Basis-URL zurückgibt, und versuchen Sie es dann erneut.

6. **Die Authentifizierung beim Upstream-IMS-Service ist fehlgeschlagen**

   **Ursache:** Die Sitzung ist möglicherweise abgelaufen oder bei der Authentifizierung bei Adobe IMS ist während der Routing-Anfrage ein Problem aufgetreten.

   **Empfehlung:** Melden Sie sich von LLM Optimizer ab, melden Sie sich wieder an und versuchen Sie dann erneut, das Routing zu aktivieren.

Wenn das Problem weiterhin besteht, wenden Sie sich an Ihr Adobe-Accountteam oder an `llmo-at-edge@adobe.com`.

## (Optional) Überprüfen der Einrichtung

Stellen Sie nach Abschluss der Einrichtung sicher, dass Bot-Traffic an Edge Optimize weitergeleitet wird und dass der menschliche Traffic nicht betroffen ist.

1. **Testen von Bot-Traffic (sollte optimiert werden)**

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

2. **Testen von menschlichem Traffic (sollte NICHT betroffen sein)**

   Simulieren Sie eine normale menschliche Browser-Anfrage:

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
   ```

   Die Antwort sollte nicht den Header `x-edgeoptimize-request-id` enthalten. Der Seiteninhalt und die Antwortzeit sollten nach der Aktivierung von „Optimize at Edge“ unverändert bleiben.

3. **Unterscheiden zwischen den zwei Szenarien**

   | Kopfzeile | Bot-Traffic (optimiert) | Menschlicher Traffic (nicht betroffen) |
   |---|---|---|
   | `x-edgeoptimize-request-id` | Vorhanden – enthält eine eindeutige Anfrage-ID | Abwesend |
   | `x-edgeoptimize-fo` | Nur vorhanden, wenn Failover stattgefunden hat (Wert: `1`) | Abwesend |

4. **Überprüfen des Routing-Status in LLM Optimizer**

   Sie können das Routing auch in der Benutzeroberfläche von LLM Optimizer bestätigen. Öffnen Sie **Kundenkonfiguration** und wählen Sie die Registerkarte **CDN-Konfiguration** aus. Wenn das Routing aktiv ist, wird im Abschnitt **Optimierungen für AI Agents bereitstellen** **Abgeschlossen** angezeigt.

   ![Optimierungen für AI Agents bereitstellen – abgeschlossen](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
