---
title: dm_os_memory_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0483d616a8e95662b7501b1d5de74abd6ad3cfef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013295"
---
# <a name="sysdmosmemorypools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jeden Objektspeicher in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zurück. Mit dieser Sicht kann die Cachespeichernutzung überwacht und schlechtes Cacheverhalten identifiziert werden.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_memory_pools**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|Speicheradresse des Eintrags, der für den Speicherpool steht. Lässt keine NULL-Werte zu.|  
|**pool_id**|**int**|ID eines bestimmten Pools in einer Gruppe von Pools. Lässt keine NULL-Werte zu.|  
|**type**|**nvarchar(60)**|Typ des Objektpools. Lässt keine NULL-Werte zu. Weitere Informationen finden Sie unter [Sys. dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|Vom System zugewiesener Name des Speicherobjekts. Lässt keine NULL-Werte zu.|  
|**max_free_entries_count**|**bigint**|Maximale Anzahl freier Einträge, die ein Pool haben kann. Lässt keine NULL-Werte zu.|  
|**free_entries_count**|**bigint**|Anzahl der derzeit im Pool befindlichen freien Einträge. Lässt keine NULL-Werte zu.|  
|**removed_in_all_rounds_count**|**bigint**|Anzahl der seit dem Starten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz aus dem Pool entfernten Einträge. Lässt keine NULL-Werte zu.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="remarks"></a>Hinweise  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten verwenden gelegentlich ein gemeinsames Poolframework zum Zwischenspeichern homogener, statusfreier Datentypen. Das Poolframework ist einfacher als das Cacheframework. Alle Einträge in den Pools werden als gleichwertig betrachtet. Pools sind in interner Hinsicht Arbeitsspeicherclerks und können an den Stellen verwendet werden, an denen Arbeitsspeicherclerks verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 
  [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


