---
title: Sys. dm_db_file_space_usage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b803b86c216d877c0e056dd4892931575ca91010
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741936"
---
# <a name="sysdmdbfilespaceusage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zur Speicherverwendung aller Dateien in der Datenbank zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_db_file_space_usage**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|Datenbank-ID|  
|file_id|**smallint**|Die Datei-ID<br /><br /> FILE_ID ordnet File_id in [Sys. dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) und Fileid in [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md).|  
|filegroup_id|**smallint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die Dateigruppen-ID.|  
|total_page_count|**bigint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die Gesamtanzahl von Seiten in der Datei.|  
|allocated_extent_page_count|**bigint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die Gesamtzahl der Seiten in den zugeordneten Blöcken der Datei.|  
|unallocated_extent_page_count|**bigint**|Gesamtzahl der Seiten in den nicht zugeordneten Blöcken der Datei.<br /><br /> Nicht verwendete Seiten in nicht zugeordneten Blöcken sind nicht enthalten.|  
|version_store_reserved_page_count|**bigint**|Gesamtzahl der Seiten in den gleichartigen Blöcken, die dem Versionsspeicher zugeordnet werden. Versionsspeicherseiten werden nie aus gemischten Blöcken zugeordnet.<br /><br /> IAM-Seiten sind nicht enthalten, da sie immer aus gemischten Blöcken zugeordnet werden. PFS-Seiten sind dann enthalten, wenn sie aus einem einheitlichen Block zugeordnet werden.<br /><br /> Weitere Informationen finden Sie unter [sys.dm_tran_version_store &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md).|  
|user_object_reserved_page_count|**bigint**|Gesamtzahl der Seiten, die aus gleichartigen Blöcken für Benutzerobjekte in der Datenbank zugeordnet werden. Nicht verwendete Seiten aus einem zugeordneten Block sind in der Gesamtzahl enthalten.<br /><br /> IAM-Seiten sind nicht enthalten, da sie immer aus gemischten Blöcken zugeordnet werden. PFS-Seiten sind dann enthalten, wenn sie aus einem einheitlichen Block zugeordnet werden.<br /><br /> Sie können die Total_pages-Spalte in der [Sys. allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) Katalogsicht, um die Anzahl der reservierten Seiten jeder Zuordnungseinheit im Benutzerobjekt zurückgegeben. Beachten Sie jedoch, dass die Spalte Total_pages IAM-Seiten enthält.|  
|internal_object_reserved_page_count|**bigint**|Gesamtzahl der Seiten in gleichartigen Blöcken, die für interne Objekte in der Datei zugeordnet werden. Nicht verwendete Seiten aus einem zugeordneten Block sind in der Gesamtzahl enthalten.<br /><br /> IAM-Seiten sind nicht enthalten, da sie immer aus gemischten Blöcken zugeordnet werden. PFS-Seiten sind dann enthalten, wenn sie aus einem einheitlichen Block zugeordnet werden.<br /><br /> Es ist keine Katalogsicht bzw. kein dynamisches Verwaltungsobjekt vorhanden, die bzw. das die Seitenanzahl für jedes interne Objekt zurückgibt.|  
|mixed_extent_page_count|**bigint**|Gesamtzahl der zugeordneten und nicht zugeordneten Seiten in zugeordneten gemischten Blöcken in der Datei. Gemischte Blöcke enthalten Seiten, die verschiedenen Objekten zugeordnet werden. Diese Gesamtzahl enthält alle IAM-Seiten in der Datei.|
|modified_extent_page_count|**bigint**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Gesamtzahl der Seiten, die geändert werden, zugeordneten Blöcken der Datei, seit der letzten vollständigen datenbanksicherung. Anzahl der geänderten Seiten kann verwendet werden, zum Nachverfolgen der Umfang der differenzielle Änderungen in der Datenbank seit der letzten vollständigen Sicherung, zu entscheiden, ob die differenzielle Sicherung benötigt wird.|
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
|distribution_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Die eindeutige numerische Id, die die Verteilung.|  
  
## <a name="remarks"></a>Hinweise  
 Die Anzahl von Seiten wird immer auf Blockebene angegeben. Deshalb sind die Seitenanzahlen immer ein Vielfaches von acht (8). Die Blöcke, die GAM-Zuordnungsseiten (Global Allocation Map) und SGAM-Zuordnungsseiten (Shared Global Allocation Map) enthalten, werden gleichartigen Blöcken zugeordnet. Sie sind nicht in den zuvor beschriebenen Seitenanzahlen enthalten. Weitere Informationen zu Seiten und Blöcken finden Sie unter [Seiten und Blöcken Architecture Guide](../../relational-databases/pages-and-extents-architecture-guide.md). 
  
 Der Inhalt des aktuellen Versionsspeichers befindet sich in [Sys. dm_tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md). Versionsspeicherseiten werden auf der Dateiebene anstelle der Sitzungs- und Taskebene nachverfolgt, da es sich bei ihnen um globale Ressourcen handelt. Eine Sitzung kann Versionen generieren, doch können die Versionen nach dem Sitzungsende nicht entfernt werden. Beim Cleanup des Versionsspeichers muss die am längsten ausgeführte Transaktion, die Zugriff auf die bestimmte Version benötigt, berücksichtigt werden. Die am längsten ausgeführte Transaktion, die im Zusammenhang mit der Version Store bereinigen kann ermittelt werden, anhand der Spalte Elapsed_time_seconds in [Sys. dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md).  
  
 Häufige Änderungen in der Spalte Mixed_extent_page_count hinweisen intensiven Gebrauch von SGAM-Seiten. In diesem Fall sind zahlreiche PAGELATCH_UP-Wartevorgänge enthalten, bei denen die Warteressource eine SGAM-Seite ist. Weitere Informationen finden Sie unter [Sys. dm_os_waiting_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md), [Sys. dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md), und [sys.dm_os_latch_ Statistiken &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md).  
  
## <a name="user-objects"></a>Benutzerobjekte  
 Die folgenden Objekte sind in den Seitenzählern für Benutzerobjekte enthalten:  
  
-   Benutzerdefinierte Tabellen und Indizes  
  
-   Systemtabellen und -indizes  
  
-   Globale temporäre Tabellen und Indizes  
  
-   Lokale temporäre Tabellen und Indizes  
  
-   Tabellenvariablen  
  
-   In Tabellenwertfunktionen zurückgegebene Tabellen  
  
## <a name="internal-objects"></a>Interne Objekte  
 Interne Objekte gibt es nur in ' tempdb '. Die folgenden Objekte sind in den Seitenzählern für interne Objekte enthalten:  
  
-   Arbeitstabellen für Cursor- oder Spoolvorgänge und temporären LOB-Speicher (Large Object)  
  
-   Arbeitsdateien für Vorgänge wie z. B. Hashjoins  
  
-   Sortierläufe  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Aktion|Beziehung|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id, file_id|sys.dm_io_virtual_file_stats.database_id, file_id|1:1|  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="examples"></a>Beispiele  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>Ermitteln des in tempdb verfügbaren freien Speicherplatzes  
 Die folgende Abfrage gibt die Gesamtanzahl der freien Seiten und die Gesamtmenge des freien Speicherplatzes in Megabyte (MB verfügbar in allen Dateien in) **Tempdb**.  
  
```sql
USE tempdb;  
GO  
SELECT SUM(unallocated_extent_page_count) AS [free pages],   
(SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]  
FROM sys.dm_db_file_space_usage;  
```  

### <a name="determining-the-amount-of-space-used-by-user-objects"></a>Ermitteln des von Benutzerobjekten belegten Speicherplatzes  
 Die folgende Abfrage gibt die Gesamtzahl der von den Benutzerobjekten in tempdb verwendeten Seiten sowie den von den Benutzerobjekten belegten Gesamtspeicherplatz (in MB) zurück.  
  
```sql  
USE tempdb;  
GO  
SELECT SUM(user_object_reserved_page_count) AS [user object pages used],  
(SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]  
FROM sys.dm_db_file_space_usage;
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
