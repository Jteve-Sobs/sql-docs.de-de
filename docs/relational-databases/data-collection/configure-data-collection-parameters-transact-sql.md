---
title: Konfigurieren von Parametern für die Datensammlung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31d9f661908adc148fea48b020fa8b8b215c4755
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909701"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Konfigurieren von Parametern für die Datensammlung (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Bevor Sie einen benutzerdefinierten Sammlungssatz erstellen, müssen Sie zuerst Datensammlungsparameter konfigurieren. Hierfür können Sie die gespeicherten Prozeduren verwenden, die mit dem Datensammler bereitgestellt werden. Um diese Aufgabe auszuführen, müssen Sie mit dem Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] den folgenden Vorgang durchführen.  
  
> [!NOTE]  
>  Parameter für die Datensammlung können nur einmal konfiguriert werden. Nach der Konfiguration werden diese Parameter für alle zusätzlichen Sammlungssätze verwendet, die Sie erstellen.  
  
### <a name="configure-data-collection-parameters"></a>Konfigurieren von Parametern für die Datensammlung  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der Datenbank her, in der Sie einen benutzerdefinierten Sammlungssatz erstellen möchten.  
  
2.  Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  

    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
