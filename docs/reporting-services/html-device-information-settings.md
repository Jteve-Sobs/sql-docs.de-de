---
title: Geräteinformationseinstellungen für HTML | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- HTML [Reporting Services], rendering
- device information settings [Reporting Services], HTML rendering
ms.assetid: f505f478-dd6d-444a-957c-34f7cfb98911
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7c0d477364c4920e8220aef96629b24e34650ebb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65503104"
---
# <a name="html-device-information-settings"></a>HTML-Geräteinformationseinstellungen
In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das HTML-Format aufgeführt.  
  
> [!IMPORTANT]  
>  Die in der Tabelle unten aufgelisteten Geräteinformationseinstellungen mit einem **(\*)** wurden als veraltet markiert und sollten in neuen Anwendungen nicht verwendet werden. Weitere Informationen finden Sie unter [Als veraltet markierte Funktionen in SQL Server Reporting Services in SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)   
  
|Einstellung|value|  
|-------------|-----------|  
|**AccessibleTablix**|Gibt an, ob mit zusätzlichen Barrierefreiheitsmetadaten zu Verwendung mit Sprachausgaben gerendert werden soll. Die zusätzlichen Barrierefreiheitsmetadaten bewirken, dass der gerenderte Bericht mit den folgenden technischen Standards in "Web-based Intranet and Internet Information and Applications", Abschnitt (1194.22) der Electronic and Information Technology Accessibility Standards (Abschnitt 508) kompatibel ist:<br /><br /> (g) Zeilen- und Spaltenüberschriften werden für Datentabellen identifiziert.<br /><br /> (h) Markup wird verwendet, um Datenzellen und Headerzellen für Datentabellen zuzuordnen, die zwei oder mehr Logikebenen für Zeilen- oder Spaltenüberschriften haben.|  
|**ActionScript(\*)**|Gibt den Namen der JavaScript-Funktion an, die verwendet werden soll, wenn ein Aktionsereignis auftritt, z. B. ein Drillthrough oder ein Lesezeichenklick. Wenn dieser Parameter angegeben wird, löst ein Aktionsereignis die genannte JavaScript-Funktion statt eines Postbacks zum Server aus.|  
|**BookmarkID**|Die Lesezeichen-ID im Bericht, zu der gesprungen werden soll|  
|**DocMap**|Gibt an, ob die Berichtsdokumentstruktur angezeigt oder ausgeblendet werden soll. Der Standardwert dieses Parameters ist **true**.|  
|**ExpandContent**|Gibt an, ob der Bericht in einer Tabellenstruktur eingeschlossen werden soll, wodurch die horizontale Größe beschränkt wird|  
|**FindString**|Der Text, nach dem im Bericht gesucht werden soll. Der Standardwert dieses Parameters ist eine leere Zeichenfolge.|  
|**GetImage (\*)**|Ruft ein bestimmtes Symbol für die Benutzeroberfläche des HTML-Viewers ab.|  
|**HTMLFragment**|Gibt an, ob anstelle eines vollständigen HTML-Dokuments ein HTML-Fragment erstellt wird. Ein HTML-Fragment enthält den Berichtsinhalt in einem TABLE-Element und lässt das HTML-Element und das BODY-Element aus. Der Standardwert ist **false**. Wenn Sie mit der **M:ReportExecution2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@, ReportExecution2005.Warning[]@,System.String[]@)** -Methode der SOAP-API HTML rendern, müssen Sie diese Geräteinformationen auf **TRUE** festlegen, sofern Sie einen Bericht mit Bildern rendern. Wenn Sie mithilfe von SOAP rendern und die **HTMLFragment** -Eigenschaft auf **true** festgelegt ist, werden URLs mit Sitzungsinformationen erstellt, die verwendet werden können, um Bilder ordnungsgemäß anzufordern. Die Bilder müssen hochgeladene Ressourcen in der Berichtsserver-Datenbank sein.|  
|**ImageConsolidation**|Gibt an, ob das gerenderte Diagramm, die gerenderte Karte, das gerenderte Messgerät und die gerenderten Indikatorbilder in ein großes Bild konsolidiert werden. Die Konsolidierung von Bildern hilft, die Leistung des Berichts im Clientbrowser zu verbessern, wenn der Bericht viele Datenvisualisierungselemente enthält. Der Standardwert für die meisten modernen Browser ist **true** .|  
|**JavaScript**|Gibt an, ob JavaScript im gerenderten Bericht unterstützt wird. Der Standardwert lautet **true**.|  
|**LinkTarget**|Das Ziel für Links im Bericht. Sie können ein Fenster oder einen Bereich als Ziel auswählen, indem Sie den Namen des Fensters angeben, z.B. **LinkTarget**=*Fenstername*, oder Sie können ein neues Fenster als Ziel wählen, indem Sie **LinkTarget**=_blank verwenden. Andere gültige Zielnamen sind beispielsweise _self, _parent und _top.|  
|**OnlyVisibleStyles(\*)**|Gibt an, dass für die gerade gerenderte Seite nur freigegebene Formate generiert werden|  
|**OutlookCompat**|Gibt an, ob beim Rendern zusätzliche Metadaten verwendet werden sollen, um die Darstellung des Berichts in Outlook zu optimieren. Der Standardwert ist **false**.|  
|**Parameter**|Gibt an, ob der Parameterbereich der Symbolleiste angezeigt oder ausgeblendet werden soll. Wenn Sie diesen Parameter auf den Wert **true**festlegen, wird der Parameterbereich der Symbolleiste angezeigt. Der Standardwert dieses Parameters ist **true**.|  
|**PrefixId**|Bei Verwendung mit **HTMLFragment**wird das angegebene Präfix allen **ID** -Attributen des zu erstellenden HTML-Fragments hinzugefügt.|  
|**ReplacementRoot(\*)**|Die Zeichenfolge, die allen Drillthrough-, Umschalt- und Lesezeichenlinks im Bericht vorangestellt wird, wenn das Rendern außerhalb des ReportViewer-Steuerelements erfolgt. Diese wird beispielsweise verwendet, um den Klick eines Benutzers auf eine benutzerdefinierte Seite umzuleiten.|  
|**ResourceStreamRoot(\*)**|Die Zeichenfolge, die der URL für alle Bildressourcen vorangestellt wird, z. B. Bilder für die Umschaltfläche oder Sortierung.|  
|**Abschnitt**|Die Seitenzahl des zu rendernden Berichts. Der Wert **0** gibt an, dass alle Abschnitte des Berichts gerendert werden. Der Standardwert ist **1**.|  
|**StreamRoot (\*)**|Der im HTML-Bericht dem Wert des **src** -Attributs des IMG-Elements vorangestellte Pfad, welcher vom Berichtsserver zurückgegeben wird. Standardmäßig stellt der Berichtsserver den Pfad bereit. Sie können diese Einstellung verwenden, um einen Stammpfad für die Bilder in einem Bericht anzugeben (beispielsweise **https://\<Servername>/resources/companyimages**).|  
|**StyleStream**|Gibt an, ob Formate und Skripts als separater Datenstrom statt im Dokument erstellt werden. Der Standardwert ist **false**.|  
|**Symbolleiste**|Gibt an, ob die Symbolleiste ein- oder ausgeblendet werden soll. Der Standardwert dieses Parameters ist **true**. Wenn der Wert dieses Parameters **FALSE**ist, werden alle verbleibenden Optionen (außer der Dokumentstruktur) ignoriert. Wenn Sie diesen Parameter weglassen, wird die Symbolleiste automatisch für Renderingformate angezeigt, die sie unterstützen.<br /><br /> Die Symbolleiste für den Berichts-Viewer wird gerendert, wenn Sie den URL-Zugriff verwenden, um einen Bericht zu rendern. Die Symbolleiste wird nicht durch die SOAP-API gerendert. Die **Toolbar** -Geräteinformationseinstellung wirkt sich jedoch darauf aus, wie der Bericht bei Verwendung der SOAP- **Render** -Methode angezeigt wird. Ist der Wert dieses Parameters **true** , wenn Sie SOAP zum Rendern in das HTML-Format verwenden, so wird nur der erste Teil des Berichts gerendert. Wenn der Wert **false**ist, wird der ganze HTML-Bericht als einzelne HTML-Seite gerendert.|  
|**UserAgent**|Die **user-agent** -Zeichenfolge des Browsers, von dem die Anforderung stammt und die sich in der HTTP-Anforderung befindet.|  
|**Zoom (\*)**|Der Zoomfaktor für den Bericht als ganzzahliger Prozentsatz oder Zeichenfolgenkonstante. Standardwerte für die Zeichenfolge sind **Page Width** und **Whole Page**. Dieser Parameter wird von Versionen von [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer, die älter als Internet Explorer 5.0 sind, sowie allen nicht von[!INCLUDE[msCoName](../includes/msconame-md.md)] bereitgestellten Browsern ignoriert. Der Standardwert dieses Parameters ist **100**.|  
|**DataVisualizationFitSizing**|Gibt das Verhalten für die Datenvisualisierungsanpassung in einem Tablix an. Dies schließt Diagramm, Messgerät und Karte ein.<br /><br /> Mögliche Werte: **Ungefähr** und **Genau**.<br /><br /> Der Standardwert lautet **Ungefähr**. Wird die Einstellung aus der Datei **rsreportserver.config** entfernt, lautet der Wert für das Standardverhalten **Genau**.<br /><br /> Die Aktivierung von **Genau** hat möglicherweise Auswirkungen auf die Leistung, da die Verarbeitung zur Ermittlung der genauen Größe möglicherweise länger dauert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
