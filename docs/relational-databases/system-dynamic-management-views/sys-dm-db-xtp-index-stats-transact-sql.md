---
title: dm_db_xtp_index_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e6370f4cbfcbc38478e562c3b74ff24ffde962f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026836"
---
# <a name="sysdmdbxtpindexstats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Enthält Statistiken, die seit dem letzten Neustart der Datenbank erfasst wurden.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;In-Memory-Optimierung&#41; ](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) und [Richtlinien zum Verwenden von Indizes für Speicheroptimierte Tabellen](https://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b).  

  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|ID des Objekts, zu dem dieser Index gehört.|  
|xtp_object_id|**bigint**|Interne ID, die auf die aktuelle Version des Objekts entspricht.<br /><br /> Hinweis: Gilt für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|index_id|**bigint**|Die ID des Index. Die index_id ist nur innerhalb des Objekts eindeutig.|  
|scans_started|**bigint**|Anzahl der ausgeführten In-Memory OLTP-Indexscans. Jeder Auswähl-, Einfüge-, Update- oder Löschvorgang erfordert einen Indexscan.|  
|scans_retries|**bigint**|Anzahl der Indexscans, die wiederholt werden mussten.|  
|rows_returned|**bigint**|Kumulierte Anzahl der Zeilen, die seit dem Erstellen der Tabelle oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben wurden.|  
|rows_touched|**bigint**|Kumulierte Anzahl der Zeilen, auf die seit dem Erstellen der Tabelle oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugegriffen wurde.|  
|rows_expiring|**bigint**|Nur interne Verwendung.|  
|rows_expired|**bigint**|Nur interne Verwendung.|  
|rows_expired_removed|**bigint**|Nur interne Verwendung.|  
|phantom_scans_started|**bigint**|Nur interne Verwendung.|  
|phantom_scans_retries|**bigint**|Nur interne Verwendung.|  
|phantom_rows_touched|**bigint**|Nur interne Verwendung.|  
|phantom_expiring_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_removed_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_rows_removed|**bigint**|Nur interne Verwendung.|  
|object_address|**varbinary(8)**|Nur interne Verwendung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die aktuelle Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
