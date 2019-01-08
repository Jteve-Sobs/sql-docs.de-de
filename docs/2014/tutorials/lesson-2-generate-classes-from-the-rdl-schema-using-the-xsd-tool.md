---
title: 'Lektion 2: Generieren von Klassen aus dem RDL-Schema mithilfe des Xsd-Tools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 818400a678b16f524e79da607a25775ad756ca5d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53374492"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Lektion 2: Generieren von Klassen aus dem RDL-Schema mithilfe des Xsd-Tool
  Nachdem Sie das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt erstellt haben, rufen Sie eine lokale Kopie des Berichtsdefinitionsschemas ab, und führen Sie das XML-Schemadefinitionstool (Xsd.exe) aus.  
  
### <a name="to-generate-the-rdl-classes"></a>So generieren Sie RDL-Klassen  
  
1.  Öffnen Sie eine Instanz des [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (oder äquivalenten Webbrowser), und navigieren Sie zu folgender URL:  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  Nachdem das RDL-Schema im Browser geöffnet wurde, klicken Sie auf das Menü **Datei** , und wählen Sie **Speichern unter**aus.  
  
3.  Navigieren Sie zu dem Speicherort, an dem Sie das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projekt erstellt haben, und speichern Sie das Schema unter dem Dateinamen ReportDefinition.xsd.  
  
4.  Nachdem die Datei gespeichert wurde, öffnen Sie eine Instanz der [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] -Eingabeaufforderung. Um eine Instanz der Eingabeaufforderung zu öffnen, klicken Sie im Startmenü, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft Visual Studio 2010**, zeigen Sie auf **Visual Studio-Tools** , und klicken Sie auf **Visual Studio-Eingabeaufforderung (2010)**.  
  
5.  Ändern Sie den aktuellen Pfad in den Speicherort, an dem Sie die Datei ReportDefinition.xsd gespeichert haben:  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Generieren Sie mit dem folgenden Befehl die Datei ReportDefinition.cs, in der die Klassen für das RDL-Schema enthalten sind:  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Verwenden Sie zum Generieren der Datei ReportDefinition.vb folgenden Befehl:  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Fügen Sie dem Projekt ReportDefinition.xsd hinzu. Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**. Navigieren Sie zum Speicherort der Datei ReportDefinition.xsd, wählen Sie ReportDefinition.xsd aus, und klicken Sie auf **Hinzufügen**.  
  
    > [!NOTE]  
    >  Nachdem Sie das Projekt die Datei ReportDefinition.xsd hinzugefügt haben, sehen Sie im **Projektmappen-Explorer** , dass die Datei ReportDefinition.cs (. vb) nicht vorhanden ist. Um die Datei anzuzeigen, klicken Sie neben der Datei ReportDefinition.xsd auf die Schaltfläche zum Erweitern/Reduzieren.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 In der nächsten Lektion schreiben Sie Code, um eine Berichtsdefinition mithilfe der aus dem RDL-Schema generierten Klassen von einem Berichtsserver zu laden. Finden Sie unter [Lektion 3: Laden Sie eine Berichtsdefinition vom Berichtsserver](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema generiert &#40;SSRS-Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Berichtsdefinitionssprache (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
