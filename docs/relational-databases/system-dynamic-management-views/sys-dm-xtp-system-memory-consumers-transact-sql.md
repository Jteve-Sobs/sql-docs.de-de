---
title: dm_xtp_system_memory_consumers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_system_memory_consumers
- sys.dm_xtp_system_memory_consumers_TSQL
- sys.dm_xtp_system_memory_consumers
- dm_xtp_system_memory_consumers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_system_memory_consumers dynamic management view
ms.assetid: 9eb0dd82-7920-42e0-9e50-7ce6e7ecee8b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebc5947611129086952394f157c6173a3b4efcf0
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826304"
---
# <a name="sysdmxtpsystemmemoryconsumers-transact-sql"></a>sys.dm_xtp_system_memory_consumers (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Meldet Arbeitsspeicherconsumer auf Systemebene für [!INCLUDE[hek_2](../../includes/hek-2-md.md)]. Der Arbeitsspeicher für diese Consumer stammt entweder aus dem Standardpool (wenn die Zuordnung im Kontext eines Benutzerthreads ist) oder dem internen Pool (wenn die Zuordnung im Kontext eines Systemthreads ist).  
  
```  
-- system memory consumers @ instance  
select * from sys.dm_xtp_system_memory_consumers  
```  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|Typ|Description|  
|-----------------|----------|-----------------|  
|memory_consumer_id|**bigint**|Interne ID für Arbeitsspeicherconsumer.|  
|memory_consumer_type|**int**|Eine ganze Zahl, die den Typ des arbeitsspeicherconsumers mit einem der folgenden Werte darstellt:<br /><br /> 0 – sollte es nicht angezeigt werden. Aggregiert die Speichernutzung von zwei oder mehreren Consumern.<br /><br /> 1 – LOOKASIDE: Verfolgt die arbeitsspeichernutzung für ein systemlookaside nach.<br /><br /> 2: VARHEAP: Verfolgt die arbeitsspeichernutzung für einen Heap variabler Länge.<br /><br /> 4 – e/a-Seitenpool: Verfolgt die arbeitsspeichernutzung für einen systemseitenpool für e/a-Vorgänge verwendet.|  
|memory_consumer_type_desc|**nvarchar(16)**|Die Beschreibung des Typs des Arbeitsspeicherconsumers:<br /><br /> 0 – sollte es nicht angezeigt werden.<br /><br /> 1 – LOOKASIDE<br /><br /> 2 - VARHEAP<br /><br /> 4 - PGPOOL|  
|memory_consumer_desc|**nvarchar(64)**|Die Beschreibung der Arbeitsspeicherconsumer-Instanz:<br /><br /> VARHEAP: <br />Der Systemheap. Allgemein. Wird derzeit nur verwendet, um Arbeitselemente der Garbage Collection zuzuordnen.<br />-oder-<br />Der Lookasideheap. Wird von Lookasides verwendet, wenn die Anzahl der in der Lookasideliste enthaltenen Elemente einen vordefinierten Grenzwert (normalerweise etwa 5.000 Elemente) erreicht.<br /><br /> PGPOOL: Für e/a-System sind Systempools gibt es drei unterschiedliche Größen: System-4-KB-Seitenpool System 64 KB-Seitenpool und System-256-KB Seite Pool.|  
|lookaside_id|**bigint**|Die ID des threadlokalen Nebenarbeitsspeicheranbieters.|  
|pagepool_id|**bigint**|Die ID des threadlokalen Seitenpool-Arbeitsspeicheranbieters.|  
|allocated_bytes|**bigint**|Anzahl der für den Consumer reservierten Bytes.|  
|used_bytes|**bigint**|Die von diesem Consumer verwendeten Bytes. Gilt nur für varheap-Arbeitsspeicherconsumer.|  
|allocation_count|**int**|Anzahl der Zuordnungen.|  
|partition_count|**int**|Nur interne Verwendung.|  
|sizeclass_count|**int**|Nur interne Verwendung.|  
|min_sizeclass|**int**|Nur interne Verwendung.|  
|max_sizeclass|**int**|Nur interne Verwendung.|  
|memory_consumer_address|**varbinary**|Interne Adresse des Consumers.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert VIEW SERVER STATE-Berechtigungen auf dem Server.  
  
## <a name="user-scenario"></a>Benutzerszenario  
  
```  
-- system memory consumers @ instance  
selectmemory_consumer_type_desc,   
allocated_bytes/1024 as allocated_bytes_kb,   
used_bytes/1024 as used_bytes_kb, allocation_count  
from sys.dm_xtp_system_memory_consumers  
```  
  
 In der Ausgabe werden alle Arbeitsspeicherconsumer auf Systemebene angezeigt. Beispielsweise gibt es Consumer für das Transaktionslookaside.  
  
```  
memory_consumer_type_name           memory_consumer_desc                           allocated_bytes_kb   used_bytes_kb        allocation_count  
-------------------------------          ---------------------                          -------------------  --------------        ----------------  
VARHEAP                                  Lookaside heap                                 0                    0                    0  
VARHEAP                                  System heap                                    768                  0                    2  
LOOKASIDE                                GC transaction map entry                       64                   64                   910  
LOOKASIDE                                Redo transaction map entry                     128                  128                  1260  
LOOKASIDE                                Recovery table cache entry                     448                  448                  8192  
LOOKASIDE                                Transaction recent rows                        3264                 3264                 4444  
LOOKASIDE                                Range cursor                                   0                    0                    0  
LOOKASIDE                                Hash cursor                                    3200                 3200                 11070  
LOOKASIDE                                Transaction save-point set entry               0                    0                    0  
LOOKASIDE                                Transaction partially-inserted rows set        704                  704                  1287  
LOOKASIDE                                Transaction constraint set                     576                  576                  1940  
LOOKASIDE                                Transaction save-point set                     0                    0                    0  
LOOKASIDE                                Transaction write set                          704                  704                  672  
LOOKASIDE                                Transaction scan set                           320                  320                  156  
LOOKASIDE                                Transaction read set                           704                  704                  343  
LOOKASIDE                                Transaction                                    4288                 4288                 1459  
PGPOOL                                   System 256K page pool                          5120                 5120                 20  
PGPOOL                                   System 64K page pool                           0                    0                    0  
PGPOOL                                   System 4K page pool                            24                   24                   6  
```  
  
 So zeigen Sie den durch Systemzuordnungen belegten Gesamtarbeitsspeicher an  
  
```  
select sum(allocated_bytes)/(1024*1024) as total_allocated_MB, sum(used_bytes)/(1024*1024) as total_used_MB   
from sys.dm_xtp_system_memory_consumers  
  
total_allocated_MB   total_used_MB  
-------------------- --------------------  
2                    2  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
