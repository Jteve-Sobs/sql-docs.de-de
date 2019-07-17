---
title: Sys. dm_db_index_usage_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 491ec37d96cf6bdb2b074efb42a54406beb1fd20
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264404"
---
# <a name="sysdmdbindexusagestats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die Anzahl verschiedener Arten von Indexvorgängen und den Zeitpunkt zurück, wann die einzelnen Vorgänge zuletzt ausgeführt wurden.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, diese Informationen bereitstellen, wird jede Zeile, die Daten enthält, die zum verbundenen Mandanten gehören nicht herausgefiltert.  
  
> [!NOTE]  
>  **Sys. dm_db_index_usage_stats** gibt keine Informationen zu speicheroptimierten Indizes zurück. Weitere Informationen zu speicheroptimierten Index verwenden, finden Sie unter [dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
> [!NOTE]  
>  Aufrufen von dieser Ansicht vom [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie **sys.dm_pdw_nodes_db_index_usage_stats**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|ID der Datenbank, für die die Tabelle oder Sicht definiert ist.|  
|**object_id**|**int**|ID der Tabelle oder Sicht, für die der Index definiert ist.|  
|**index_id**|**int**|Die ID des Index.|  
|**user_seeks**|**bigint**|Anzahl von Suchvorgängen durch Benutzerabfragen.|  
|**user_scans**|**bigint**|Anzahl von Scanvorgängen durch Benutzerabfragen, die nicht verwendet haben seek""-Prädikat.|  
|**user_lookups**|**bigint**|Anzahl von Lesezeichen-Nachschlagevorgängen durch Benutzerabfragen.|  
|**user_updates**|**bigint**|Anzahl von Updates durch Benutzerabfragen. Dies umfasst die INSERT-, DELETE- und aktualisiert, die Anzahl von Vorgängen, die nicht die tatsächlichen Zeilen betroffen fertig darstellt. Z. B. Wenn Sie 1000 Zeilen in einer einzigen Anweisung zu löschen, erhöht diese Zahl um 1|  
|**last_user_seek**|**datetime**|Zeitpunkt des letzten Suchvorgangs durch den Benutzer|  
|**last_user_scan**|**datetime**|Zeitpunkt des letzten Scanvorgangs durch den Benutzer|  
|**last_user_lookup**|**datetime**|Zeitpunkt des letzten Nachschlagevorgangs durch den Benutzer.|  
|**last_user_update**|**datetime**|Zeitpunkt des letzten Updates durch den Benutzer.|  
|**system_seeks**|**bigint**|Anzahl von Suchvorgängen durch Systemabfragen.|  
|**system_scans**|**bigint**|Anzahl von Scanvorgängen durch Systemabfragen.|  
|**system_lookups**|**bigint**|Anzahl von Nachschlagevorgängen durch Systemabfragen.|  
|**system_updates**|**bigint**|Anzahl von Updates durch Systemabfragen.|  
|**last_system_seek**|**datetime**|Zeitpunkt des letzten Systemsuchvorgangs.|  
|**last_system_scan**|**datetime**|Zeitpunkt des letzten Systemscanvorgangs.|  
|**last_system_lookup**|**datetime**|Zeitpunkt des letzten Systemnachschlagevorgangs.|  
|**last_system_update**|**datetime**|Zeitpunkt des letzten Systemupdates.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="remarks"></a>Hinweise  
 Jeder einzelne Such-, Scan-, Nachschlage- oder Updatevorgang für den angegebenen Index durch eine Abfrageausführung zählt als Verwendung dieses Indexes, und der entsprechende Zähler in dieser Sicht wird inkrementiert. Informationen werden für Vorgänge angezeigt, die durch Benutzerabfragen verursacht werden, und für Vorgänge, die durch intern generierte Abfragen verursacht werden, wie z. B. Scans zum Sammeln von Statistikdaten.  
  
 Die **User_updates** -Leistungsindikator gibt die wartungsebene für den Index, der durch Insert verursacht werden, aktualisieren oder delete-Vorgänge in der zugrunde liegenden Tabelle oder Sicht. Mithilfe dieser Sicht können Sie ermitteln, welche Indizes selten von den Anwendungen verwendet werden. Außerdem können Sie mithilfe dieser Sicht bestimmen, welche Indizes einen hohen Wartungsaufwand erzeugen. Sie können Indizes löschen, die einen hohen Wartungsaufwand erzeugen, aber nicht oder nur selten für Abfragen verwendet werden.  
  
 Die Zähler werden auf 'leer' gesetzt, sobald ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst (MSSQLSERVER) gestartet wird. Außerdem werden jedes Mal, wenn eine Datenbank getrennt oder beendet wird (beispielsweise, weil AUTO_CLOSE auf ON festgelegt ist), alle dieser Datenbank zugehörigen Zeilen entfernt.  
  
 Wenn ein Index verwendet wird, wird eine Zeile hinzugefügt, um **Sys. dm_db_index_usage_stats** , wenn eine Zeile für den Index noch nicht vorhanden ist. Beim Hinzufügen der Zeile sind deren Zähler anfänglich auf 0 festgelegt.  
  
 Während des Upgrades auf [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], oder [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], Einträge in Sys. dm_db_index_usage_stats werden entfernt. Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], Einträge werden beibehalten, wie vor [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].  
  
## <a name="permissions"></a>Berechtigungen  
Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.  
  
## <a name="see-also"></a>Siehe auch  

 [Index Related Dynamic Management Views and Functions (Transact-SQL) (Indexbezogene dynamische Verwaltungssichten und -funktionen (Transact-SQL))](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


