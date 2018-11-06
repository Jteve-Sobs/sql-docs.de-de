---
title: Ausführen von Hilfsprogramm- und Nicht-Hilfsprogramm-Sammlungssätzen auf derselben Instanz von SQL-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 74bbb7c7e971df4a7d570b91dc5f231a71d87bf3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030957"
---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>Ausführen von Hilfsprogramm- und Nicht-Hilfsprogramm-Sammlungssätzen auf derselben Instanz von SQL-Instanz
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der Sammlungssatz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms kann parallel mit Sammlungssätzen verwendet werden, die nicht zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm gehören. Eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann also von anderen Sammlungssätzen überwacht werden, während sie einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm zugeordnet ist. Sie müssen den Nicht-Hilfprogramm-Sammlungssatz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch deaktivieren, während die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm registriert wird.  
  
 Nachdem die Instanz beim UCP registriert wurde, können Sie Nicht-Hilfsprogramm-Sammlungssätze von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erneut starten. Beachten Sie jedoch, dass alle Sammlungssätze für die verwaltete Instanz ihre Daten in das UMDW (Utility Management Data Warehouse) hochladen. Der UMDW-Dateiname lautet sysutility_mdw.  
  
 Um Hilfsprogramm-Sammlungssätze von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parallel mit Nicht-Hilfsprogramm-Sammlungssätzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auszuführen, sollten Sie Folgendes berücksichtigen:  
  
-   Parallele Sammlungssätze werden unterstützt.  
  
-   Sie müssen vorhandene Datensammler deaktivieren, während Sie Instanzen im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm registrieren.  
  
-   Um die Überprüfungsanforderungen zu erfüllen, müssen Sie die folgenden gespeicherten Prozeduren für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen, bevor Sie einen UCP erstellen, und für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , bevor Sie die Instanz im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm registrieren:  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Wenn Sie diese gespeicherten Prozeduren nicht ausführen, bevor Sie den Assistenten zum Erstellen von UCPs oder den Assistenten zum Hinzufügen verwalteter Instanzen starten, schlägt der Vorgang fehl.  
  
-   Sie müssen das UMDW des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms (sysutility_mdw) für alle Sammlungssätze auf einer verwalteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Konfigurieren des Data Warehouse für den Steuerungspunkt für das Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
