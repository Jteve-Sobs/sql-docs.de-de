---
description: sys. dm_exec_dms_workers (Transact-SQL)
title: sys. dm_exec_dms_workers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b1dd32f2bd3a810e01dc7bf50347b0a23a884796
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88398616"
---
# <a name="sysdm_exec_dms_workers-transact-sql"></a>sys. dm_exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Workern, die DMS-Schritte abschließen.  
  
 In dieser Ansicht werden die Daten für die letzten 1000 Anforderungen und aktiven Anforderungen angezeigt. für aktive Anforderungen sind die Daten in dieser Sicht immer vorhanden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Abfrage, zu der dieser DMS-Worker gehört. request_id, step_index und dms_step_index bilden den Schlüssel für diese Sicht.||  
|step_index|`int`|Abfrage Schritt, zu dem dieser DMS-Worker gehört.|Weitere Informationen finden Sie unter Step Index in [sys. dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|`int`|Schritt in den DMS-Plan, den dieser Worker ausgeführt wird.|Siehe [sys. dm_exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|`int`|Knoten, auf dem der Worker ausgeführt wird.|Weitere Informationen finden Sie unter [sys. dm_exec_compute_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|`int`|||  
|type|`nvarcha(32)`|||  
|status|`nvarchar(32)`|Status dieses Schritts|"Pending", "Running", "Complete", "failed", "undofailed", "stodingcancel", "abgebrochen", "Undone", "abgebrochen", "abgebrochen"|  
|bytes_per_sec|`bigint`|||  
|bytes_processed|`bigint`|||  
|rows_processed|`bigint`|||  
|start_time|`datetime`|Zeitpunkt, zu dem die Ausführung des Schritts gestartet wurde|Kleiner oder gleich der aktuellen Zeit und größer oder gleich end_compile_time der Abfrage, zu der dieser Schritt gehört.|  
|end_time|`datetime`|Der Zeitpunkt, zu dem dieser Schritt die Ausführung abgeschlossen hat, abgebrochen wurde oder fehlgeschlagen ist.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich start_time, auf NULL für Schritte festgelegt, die gerade ausgeführt werden oder in die Warteschlange eingereiht werden.|  
|total_elapsed_time|`int`|Gesamtzeit Spanne, für die der Abfrage Schritt ausgeführt wurde (in Millisekunden)|Zwischen 0 und dem Unterschied zwischen end_time und start_time. 0 für Schritte in der Warteschlange.|  
|cpu_time|`bigint`|||  
|query_time|`int`|||  
|buffers_available|`int`|||  
|dms_cpid|`int`|||  
|sql_spid|`int`|||  
|error_id|`nvarchar(36)`|||  
|source_info|`nvarchar(4000)`|||  
|destination_info|`nvarchar(4000)`|||  
|command|`nvarchar(4000)`|||
|compute_pool_id|`int`|Eindeutiger Bezeichner für den Pool.|

## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
