---
title: Excel-Verbindungs-Manager | Microsoft-Dokumentation
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58b73e5bd1f82d619f00e50d554d2043196d7884
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298549"
---
# <a name="excel-connection-manager"></a>Excel-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mit einem Excel-Verbindungs-Manager kann ein Paket eine Verbindung mit einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel-Arbeitsmappendatei herstellen. Die Excel-Quelle und das Excel-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden den Excel-Verbindungs-Manager.  
 
> [!IMPORTANT]
> Ausführliche Informationen über das Herstellen einer Verbindung mit Excel-Dateien sowie Einschränkungen und bekannte Probleme beim Laden von Daten aus oder in Excel-Dateien finden Sie unter [Load data from or to Excel with SQL Server Integration Services (SSIS) (Laden von Daten aus oder in Excel mit SQL Server Integration Services (SSIS))](../load-data-to-from-excel-with-ssis.md).

 Wenn Sie einem Paket einen Excel-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit als Excel-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der Sammlung **Verbindungen** im Paket den Verbindungs-Manager hinzufügt.  
  
 Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **EXCEL**festgelegt.  
  
## <a name="configure-the-excel-connection-manager"></a>Konfigurieren des Excel-Verbindungs-Managers  
 Es gibt folgende Möglichkeiten, um den Excel-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Pfad der Excel-Arbeitsmappendatei an.  
  
-   Geben Sie die Excel-Version an, die zum Erstellen der Datei verwendet wurde.  
  
-   Geben Sie an, ob die erste Zeile in den ausgewählten Arbeitsmappen oder Bereichen Spaltennamen enthält.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Verbindungs-Manager-Editor für Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="excel-connection-manager-editor"></a>Verbindungs-Manager-Editor für Excel
  Mithilfe des Dialogfelds **Verbindungs-Manager-Editor für Excel** können Sie einer vorhandenen oder neuen [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] -Arbeitsmappendatei eine Verbindung hinzufügen.  
  
### <a name="options"></a>enthalten  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und den Dateinamen einer vorhandenen oder neuen Excel-Arbeitsmappendatei ein.  
   
 **Durchsuchen**  
 Verwenden Sie das Dialogfeld **Öffnen**, um zum Ordner zu navigieren, in dem die Excel-Datei enthalten ist bzw. in dem Sie die neue Datei erstellen möchten.  
  
 **Excel-Version**  
 Geben Sie die Version von Microsoft Excel an, die zum Erstellen der Datei verwendet wurde.  
  
 **Erste Zeile enthält Spaltennamen**  
 Geben Sie an, ob die erste Zeile der Daten in der ausgewählten Arbeitsmappe Spaltennamen enthält. Der Standardwert für diese Option ist **True**.  
  
## <a name="related-tasks"></a>Related Tasks  
[Load data from or to Excel with SQL Server Integration Services (SSIS) (Laden von Daten aus oder in Excel mit SQL Server Integration Services (SSIS))](../load-data-to-from-excel-with-ssis.md)  
[Excel-Quelle](../data-flow/excel-source.md)  
[Excel-Ziel](../data-flow/excel-destination.md)
