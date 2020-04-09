---
title: Reporting Services-Problembehandlung, Probleme beim Rendern von Berichten
description: In diesem Artikel erfahren Sie, wie Sie Anzeigeprobleme beim Senden des kompilierten Berichts und der Layoutdaten an einen Berichtsrenderer in SQL Server Reporting Services diagnostizieren und beheben.
ms.date: 02/27/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
ms.assetid: 1e0fb399-4c16-438a-92cb-db3e877896d0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3a834ee415fd725c26314b95d507b86ff5280f78
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662784"
---
# <a name="troubleshoot-reporting-services-report-rendering-issues"></a>Reporting Services-Problembehandlung, Probleme beim Rendern von Berichten
Nach dem Kombinieren der Berichtsdaten und der Layoutinformationen wird der kompilierte Bericht an einen Berichtsrenderer gesendet. Wenn Sie z. B. lokal eine Vorschau eines Berichts anzeigen, verwenden Sie den HTML-Renderer zum Anzeigen des kompilierten Berichts. Dieses Thema soll Ihnen beim Behandeln von Problemen beim Rendern von Berichten helfen.   
  
## <a name="why-do-i-have-extra-white-space-including-blank-pages-in-my-report"></a>Weshalb wird zusätzlicher Leerraum, u. a. leere Seiten, in meinem Bericht angezeigt?  
Berichtselemente werden während der Berichtsverarbeitung automatisch so angepasst, dass als Teil des Berichts definierter Leerraum beibehalten wird. Leerraum in der Berichtsentwurfsansicht wird beibehalten. Auf der Berichtsentwurfsoberfläche stellt der weiße Hintergrund einen Leerraum dar, der beibehalten wird, wenn ein Bericht, je nach Zielmedium, angezeigt, exportiert oder gedruckt wird.  
  
### <a name="white-space-and-page-breaks-interact-during-rendering"></a>Leerstellen und Seitenumbrüche interagieren während des Renderings  
Wenn Sie einen Bericht anzeigen oder in ein bestimmtes Dateiformat exportieren, verarbeitet die entsprechende Renderingerweiterung den Bericht und speichert ihn im angegebenen Dateiformat. Jede Renderingerweiterung verarbeitet den Leerraum in einem Bericht nach bestimmten Regeln. Der Leerraum wird darüber hinaus von den Eigenschaften für die Seiteneinstellung, Seitenumbrüchen bei Berichtselementen, der relativen Position von Berichtselementen im Hauptteil des Berichts, der KeepTogether-Eigenschaft für bestimmte Berichtselemente und von der Tatsache beeinflusst, ob sich Berichtselemente in übergeordneten Containern befinden.   
  
Um zusätzliche Seiten aufgrund der Berichtsbreite zu vermeiden, ziehen Sie die Kante der Berichtsentwurfoberfläche so, dass diese mit dem äußeren Berichtselement übereinstimmt. Ziehen Sie für ein Berichtslayout von links nach rechts den rechten Rand, sodass dieser auf das äußerste Berichtselement ausgerichtet wird. Weitere Informationen finden Sie unter [Renderingverhalten](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
### <a name="white-space-is-not-preserved-at-the-end-of-a-report"></a>Leerraum am Ende eines Berichts wird nicht beibehalten  
In Reporting Services wird eine Option bereitgestellt, mit der Sie steuern können, ob Leerraum am Ende eines Berichts beibehalten oder entfernt werden soll.   
  
Wenn Leerraum am Ende eines Berichts beibehalten werden soll, wählen Sie den Bericht aus, führen Sie im Eigenschaftenbereich einen Bildlauf zu ConsumeContainerWhitespace aus, und geben Sie False ein.   
  
## <a name="why-do-my-reports-look-different-when-exported-to-different-formats"></a>Warum sehen meine Berichte anders aus, wenn sie in andere Formate exportiert werden?  
Nachdem Sie einen Bericht ausgeführt haben, können Sie ihn in ein anderes Format exportieren, z. B.  Excel, Word oder PDF. Je nach Format, in das Sie den Bericht exportieren, könnten bestimmte Regeln und Einschränkungen gelten. Sie können vielen Einschränkungen dadurch begegnen, dass Sie sie beim Erstellen des Berichts berücksichtigen. Sie müssen im Bericht ggf. ein etwas anderes Layout verwenden, die Elemente im Bericht sorgfältig ausrichten, die Fußzeilen im Bericht auf eine Textzeile beschränken usw. Zudem können Sie mit dem integrierten globalen Objekt in RenderFormat bedingt unterschiedliche Berichtslayouts für verschiedene Renderer verwenden. Andere integrierte globale Werte können Ihnen helfen, die Paginierung im exportierten Format zu verwalten und Arbeitsblattregisterkarten in Excel zu benennen. Weitere Informationen finden Sie unter [Exportieren von Berichten](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md) und [Verwenden von integrierten globalen Werten und Benutzerverweisen](../../reporting-services/report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).  
  
## <a name="how-can-i-view-all-my-report-data-on-one-page"></a>Wie kann ich alle Berichtsdaten auf einer Seite anzeigen?  
Für eine interaktive Anzeige bei Berichten, die nicht über extrem viele Daten verfügen, sollten Sie alle Daten auf einer Seite anzeigen.   
  
Wenn Sie bei Renderern mit weichen Seitenumbrüchen alle Daten auf einer Seite anzeigen möchten, legen Sie in den Berichtseigenschaften InteractiveHeight auf 0 fest. Bei Renderern mit weichem Seitenumbruch werden vorhandene Seitenumbrüche ignoriert.   
  
> [!NOTE]  
> Wenn ein Bericht keine Seitenumbrüche enthält, muss der gesamte Bericht verarbeitet werden, bevor Sie die erste Seite anzeigen können.   
  
Weitere Informationen zu den Kategorien von Renderern finden Sie unter [Renderingverhalten](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
## <a name="reports-do-not-run-when-your-browser-is-configured-to-prompt-for-credentials"></a>Berichte werden nicht ausgeführt, wenn der Browser so konfiguriert ist, dass Anmeldeinformationen angefordert werden.  
Das Anzeigen Ihrer Berichte schlägt möglicherweise mit einer Fehlermeldung fehl, wenn der Browser so konfiguriert ist, dass Anmeldeinformationen angefordert werden und die Datenquelle für die integrierte Windows-Authentifizierung konfiguriert ist. Dies tritt auf, wenn sich die Datenquelle auf einem anderen Computer als der Berichtsserver befindet, die Datenquelle so konfiguriert ist, dass Windows-Authentifizierung verwendet wird, und der Browser auf das Anfordern von Anmeldeinformationen festgelegt ist. Folgende sind Beispiele für Meldungen, die Sie sehen.  
  
Wenn die Datenquelle für einen Microsoft SQL Server-Verbindungstyp konfiguriert ist:  
`An error has occurred during report processing.`  
`Cannot create a connection to data source 'localhost'.`  
`Login failed for user '(null)'. Reason: Not associated with a trusted SQL Server connection.`  
  
Wenn die Datenquelle für einen Microsoft SharePoint-Listenverbindungstyp konfiguriert ist:  
`An error occurred during client rendering.`   
`An error has occurred during report processing.`   
`Query execution failed for dataset 'DataSet1'.`   
`The request failed with HTTP status 401: Unauthorized.`  
  
**So können Sie dieses Problem umgehen:** Ändern Sie die Datenquelle, um gespeicherte Anmeldeinformationen statt der Windows-Anmeldeinformationen zu verwenden.  
  
**Dieses Problem gilt für:** Browser, die so konfiguriert sind, dass Anmeldeinformationen angefordert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Fehler und Ereignisse (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
[Troubleshoot Data Retrieval issues with Reporting Services Reports (Problembehandlung: Probleme beim Abrufen von Daten in Reporting Services-Berichten)](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Troubleshoot Reporting Services Subscriptions and Delivery (Problembehandlung: Abonnements und Übermittlung in Reporting Services)](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

