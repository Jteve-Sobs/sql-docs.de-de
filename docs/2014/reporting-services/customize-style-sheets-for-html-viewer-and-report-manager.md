---
title: Anpassen von Stylesheets für den HTML-Viewer und Berichts-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- style sheets [Reporting Services]
ms.assetid: df805cff-b1de-4062-b2ac-423f37390fbd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d9c4a57413db37c8f93b1a311542398417bfeff0
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59969526"
---
# <a name="customize-style-sheets-for-html-viewer-and-report-manager"></a>Anpassen von Stylesheets für den HTML-Viewer und Berichts-Manager
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Stellt Standard cascading Style Sheets (CSS)-Dateien, die Stile für definieren die **Bericht** Symbolleiste im HTML-Viewer und Berichts-Manager. Wenn Sie ein Webentwickler sind oder Erfahrung im Erstellen von Cascading Stylesheets haben, können Sie auf eigenes Risiko die Standardstile ändern, um Farben, Schriftarten und Layout der Symbolleiste oder des Berichts-Managers zu ändern. In dieser Version sind weder die Standardstylesheets noch Anweisungen zum Ändern der Stylesheets dokumentiert.  
  
 Werden die Stylesheets unsachgemäß geändert, kann es beim Öffnen von Berichten zu Fehlern kommen. Wenn Sie nicht wissen, wie Sie zum Ändern von Stylesheets vorgehen müssen, sollten Sie die Standardstylesheets verwenden. Wenn Sie die Stylesheets anpassen möchten, sollten Sie von allen CSS-Standarddateien eine Sicherungskopie erstellen, bevor Sie Änderungen vornehmen.  
  
 Das Ändern von Stylesheets hat keine Auswirkung auf das Aussehen von veröffentlichten Berichten, die auf einem Berichtsserver ausführt werden. In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]enthalten Berichte keinen Verweis auf die verwendeten Stylesheets. Ad-hoc-Berichte, die vom Berichtsserver automatisch generiert werden, verwenden Stilinformationen, die in den Berichtsserver-Programmdateien als eingebettete Ressource gespeichert sind. Berichte, die Sie im Berichts-Designer erstellen, verwenden die Schriftarten, die Farben und das Layout, die Sie in der Berichtsdefinition angeben. Stile werden inline mit dem übrigen Layout erstellt.  
  
> [!NOTE]  
>  Wenn Sie vordefinierte Berichtsstile verwenden möchten, müssen Sie zum Erstellen eines Berichts den Berichts-Assistenten verwenden. Der Berichts-Assistent stellt eine Reihe von Designs bereit, die Sie zum Erstellen von gestalteten Berichten mit verschiedenen Farbkombinationen und Schriften verwenden können. Die Stilvorlagen, die die Designs für einen Bericht definieren, können geändert werden.  
  
## <a name="reporting-services-style-sheets"></a>Reporting Services-Stylesheets  
 In der folgenden Tabelle sind die in einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Installation verwendeten Stylesheetdateien (CSS) beschrieben.  
  
|Stylesheet|Description|  
|-----------------|-----------------|  
|Htmlviewer.css|Enthält ein Beispielstylesheet, das Sie als Vorlage zum Erstellen von benutzerdefinierten Stilen für die **Berichtssymbolleiste** im HTML-Viewer verwenden können.<br /><br /> Die vom HTML Viewer verwendeten Standardstile werden im Berichtsserver kompiliert. Die Datei Htmlviewer.css enthält ein Beispiel der vom Viewer verwendeten Stile.|  
|ReportingServices.css|Definiert Stile für den Berichts-Manager.|  
  
> [!NOTE]  
>  Die folgenden Stylesheets werden für die Onlinedokumentation des Berichts-Manager verwendet und sollten niemals geändert werden: SQL.CSS und Mailto.css. Andere Stylesheets definieren Stile für Berichte und den Berichts-Manager, die in SharePoint-Webparts geöffnet werden. Zu diesen Stylesheets gehören die Dateien "Rswebparts.css", "Sp_full.css" und "Sp_small.css". Es wird nicht empfohlen, die SharePoint-Stylesheets zu ändern. Weitere Informationen zur Verwendung von Webparts finden Sie unter [anzeigen und Durchsuchen systemeigenen Modus Berichte mithilfe von SharePoint-Webparts &#40;SSRS&#41;](reports/view-and-explore-native-mode-reports-using-sharepoint-web-parts-ssrs.md).  
  
## <a name="configuring-reporting-services-to-use-a-custom-style-sheet"></a>Konfigurieren von Reporting Services für die Verwendung eines benutzerdefinierten Stylesheets  
 Das Stylesheet muss eine gültige Cascading Stylesheet-Datei (CSS) sein und sich im Ordner Styles befinden. Standardmäßig befindet sich der Ordner Styles unter \< *Laufwerk*>: \Programme\Microsoft SQL Server\MSSQL. *n*\Reporting Services\ReportServer\Styles.  
  
 Möchten Sie für den HTML-Viewer zur Laufzeit ein benutzerdefiniertes Stylesheet verwenden, wählen Sie eine der folgenden Vorgehensweisen aus:  
  
-   Hinzufügen der <`HTMLViewerStyleSheet`> zum Festlegen der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Konfigurationsdatei.  
  
-   Geben Sie das Stylesheet in einer Berichts-URL an.  
  
### <a name="modifying-the-rsreportserverconfig-file"></a>Ändern der Datei RSReportServer.config  
 Sie können die Datei RSReportServer.config ändern, um ein benutzerdefiniertes Stylesheet für den HTML-Viewer anzugeben. Die <`HTMLViewerStyleSheet`> Einstellung ist standardmäßig nicht in der Datei enthalten. Geben Sie ihn in der <`Configuration`> Auswahl der RSReportServer.config-Datei, und geben Sie dann auf das Stylesheet, das Sie verwenden möchten. Geben Sie den Namen des Stylesheets ohne die Dateierweiterung CSS ein.  
  
 Das folgende Beispiel zeigt, wie ein Stylesheet angegeben wird:  
  
```  
<Configuration>  
...  
          <HTMLViewerStyleSheet>MyStyleSheet</HTMLViewerStyleSheet>  
...  
</Configuration>  
```  
  
### <a name="specifying-a-style-sheet-on-a-report-url"></a>Angeben eines Stylesheets in einer Berichts-URL  
 Zum Angeben eines benutzerdefinierten Stylesheets in einer Berichts-URL können Sie den URL-Zugriffsparameter `rc:StyleSheet` verwenden. Weitere Informationen zur Vorgehensweise beim Angeben von URL-Zugriffsparameter finden Sie unter [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
 Das folgende Beispiel zeigt, wie benutzerdefinierte Stile hinzugefügt werden:  
  
```  
http://localhost/reportserver?/AdventureWorksSampleReports/Product+Line+Sales&rs:Command=Render&rc:Stylesheet=MyStyleSheet  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [HTML-Viewer und die Berichtssymbolleiste](html-viewer-and-the-report-toolbar.md)   
 [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md)  
  
  
