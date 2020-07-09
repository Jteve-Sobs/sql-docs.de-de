---
title: Erstellen eines benutzerdefinierten Sammlungssatzes -Generischer T-SQL-Abfragesammlertyp
ms.date: 06/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 8ca7e286d5e6d754bfa13c1e10907b7c040b86a9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733864"
---
# <a name="create-custom-collection-set---generic-t-sql-query-collector-type"></a>Erstellen eines benutzerdefinierten Sammlungssatzes -Generischer T-SQL-Abfragesammlertyp
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Sie können auch mithilfe der mit dem Datensammler bereitgestellten gespeicherten Prozeduren einen benutzerdefinierten Sammlungssatz mit Sammelelementen erstellen, die den generischen T-SQL-Abfragesammlertyp verwenden. Das Ausführen dieses Tasks umfasst die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um die folgenden Vorgänge durchzuführen:  
  
-   Konfigurieren von Uploadzeitplänen  
  
-   Definieren und Erstellen des Sammlungssatzes  
  
-   Definieren und Erstellen eines Auflistelements  
  
-   Überprüfen, ob der Sammlungssatz und die Sammelelemente vorhanden sind.  
  
> [!NOTE]  
>  Bevor Sie einen benutzerdefinierten Sammlungssatz erstellen, müssen Sie Datensammlungsparameter konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Parametern für die Datensammlung &#40;Transact-SQL&#41;](../../relational-databases/data-collection/configure-data-collection-parameters-transact-sql.md).  
  
### <a name="define-and-create-the-collection-set"></a>Definieren und Erstellen des Sammlungssatzes  
  
1.  Definieren Sie mit der gespeicherten Prozedur „sp_syscollector_create_collection_set“ einen neuen Sammlungssatz.  
  
    ```sql
    USE msdb;  
    GO
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  

    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  

    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     Der Auflistmodus kann auf 0 (zwischengespeichert) oder 1 (nicht zwischengespeichert) festgelegt werden.  
  
     Der Protokolliergrad kann auf 0, 1 oder 2 festgelegt werden.  
  
     Die folgenden vorkonfigurierten Zeitpläne werden mit dem Datensammler bereitgestellt:  
  
    -   CollectorSchedule_Every_5min  
  
    -   CollectorSchedule_Every_10min  
  
    -   CollectorSchedule_Every_15min  
  
    -   CollectorSchedule_Every_30min  
  
    -   CollectorSchedule_Every_60min  
  
    -   CollectorSchedule_Every_6h  
  
     Wenn Sie keinen der bereitgestellten Zeitpläne verwenden möchten, können Sie einen neuen Zeitplan erstellen und für den Sammlungssatz verwenden. Weitere Informationen finden Sie unter [Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
### <a name="define-and-create-a-collection-item"></a>Definieren und Erstellen eines Auflistelements  
  
1.  Da das neue Sammelelement auf einem generischen Sammlertyp basiert, der bereits installiert ist, können Sie den folgenden Code ausführen, um die GUID so festzulegen, dass Sie dem generischen T-SQL-Abfragesammlertyp entspricht.  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  

    SELECT @collector_type_uid = collector_type_uid
      FROM [msdb].[dbo].[syscollector_collector_types]   
      WHERE name = N'Generic T-SQL Query Collector Type';  

    DECLARE @collection_item_id int;  
    ```  
  
2.  Verwenden Sie die gespeicherte Prozedur „sp_syscollector_create_collection_item“, um das Sammelelement zu erstellen. Deklarieren Sie das Schema für das Auflistelement so, dass es dem Schema zugeordnet wird, das für den generischen T-SQL-Abfragesammlertyp erforderlich ist.  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  

    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a>Überprüfen, ob der neue Sammlungssatz und das Sammelelement vorhanden sind  
  
1.  Bevor Sie den neuen Sammlungssatz starten, führen Sie die folgende Abfrage aus, um zu überprüfen, dass der neue Sammlungssatz und sein Auflistelement erstellt wurden.  
  
    ```sql  
    USE msdb;  
    GO
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     Sie können auch eine visuelle Prüfung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]durchführen. Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Datensammlung**. Der neue Sammlungssatz wird angezeigt. Das rote Kreissymbol für den Sammlungssatz gibt an, dass der Sammlungssatz beendet wurde.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden die in den vorherigen Schritten dokumentierten Beispiele miteinander kombiniert. Beachten Sie, dass die für das Sammelelement festgelegte Auflistungshäufigkeit (5 Sekunden) ignoriert wird, da der Auflistungsmodus des Sammlungssatzes auf 0 festgelegt ist, was dem Modus mit Zwischenspeicherung entspricht. Weitere Informationen finden Sie unter [Data Collection](../../relational-databases/data-collection/data-collection.md).  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  

SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  

SELECT @collector_type_uid = collector_type_uid
  FROM syscollector_collector_types   
  WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  

EXEC sp_syscollector_create_collection_item  
    @name= N'Query Stats - Test 1',  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
    <Query>  
      <Value>select * from sys.dm_exec_query_stats</Value>  
      <OutputTable>dm_exec_query_stats</OutputTable>  
    </Query>  
     </ns:TSQLQueryCollector>',  
        @collection_item_id = @collection_item_id OUTPUT,  
        @frequency = 5, -- This parameter is ignored in cached mode  
        @collection_set_id = @collection_set_id,  
        @collector_type_uid = @collector_type_uid;  
        
SELECT @collection_item_id;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Zeitpläne verwalten](../../ssms/agent/manage-schedules.md)   
 [Starten oder Beenden eines Sammlungssatzes](../../relational-databases/data-collection/start-or-stop-a-collection-set.md)  
  
  
