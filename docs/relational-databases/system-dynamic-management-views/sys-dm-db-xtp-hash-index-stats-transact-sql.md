---
title: Sys. dm_db_xtp_hash_index_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_hash_index_stats
- sys.dm_db_xtp_hash_index_stats_TSQL
- dm_db_xtp_hash_index_stats
- dm_db_xtp_hash_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_hash_index_stats (dynamic management view)
ms.assetid: 45969884-cd61-48e8-aee5-c725c78e3e4c
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2bbaaaa6770c5644da227c7e64a9ff9e0fc2c13
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026843"
---
# <a name="sysdmdbxtphashindexstats-transact-sql"></a>sys.dm_db_xtp_hash_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Diese Statistik ist für das Verständnis und die Optimierung der Bucketanzahl hilfreich. Sie kann auch verwendet werden, um Fälle zu erkennen, in denen der Indexschlüssel viele Duplikate aufweist.  
  
 Eine große durchschnittliche Kettenlänge weist darauf hin, dass viele Zeilen demselben Hashbucket hinzugefügt werden. Dies könnte folgende Ursachen haben:  
  
-   Wenn die Anzahl der leeren Buckets niedrig ist oder die durchschnittliche und die maximale Kettenlänge ähnlich sind, besteht die Wahrscheinlichkeit, dass die Bucketgesamtanzahl zu niedrig ist. Dies führt dazu, dass viele verschiedene Indexschlüssel demselben Hashbucket hinzugefügt werden.  
  
-   Wenn die Anzahl der leeren Buckets hoch oder die maximale Kettenlänge relativ zur durchschnittlichen Kettenlänge hoch ist, besteht die Wahrscheinlichkeit, dass viele Zeilen mit doppelten Indexschlüsselwerten vorliegen oder dass die Schlüsselwerte verzerrt sind. Alle Zeilen mit demselben Indexschlüsselwert werden demselben Hashbucket hinzugefügt. Daher weist dieser Bucket eine große Kettenlänge auf.  
  
Hohe Kettenlängen können die Leistung aller DML-Vorgänge für einzelne Zeilen, einschließlich von SELECT oder INSERT, deutlich beeinträchtigen. Kurze Kettenlängen in Kombination mit einer hohen Anzahl von leeren Buckets weisen auf eine zu hohe Bucketanzahl hin. Dadurch wird die Leistung von Indexscans verringert.  
  
> [!WARNING]
> **Sys. dm_db_xtp_hash_index_stats** überprüft die gesamte Tabelle. Wenn große Tabellen in der Datenbank vorhanden sind also **Sys. dm_db_xtp_hash_index_stats** dauert sehr lange ausgeführt.  
  
Weitere Informationen finden Sie unter [Hashindizes für Speicheroptimierte Tabellen](../../relational-databases/sql-server-index-design-guide.md#hash_index).  
  
|Spaltenname|Typ|Beschreibung|  
|-----------------|----------|-----------------|  
|object_id|**int**|Die Objekt-ID der übergeordneten Tabelle.|  
|xtp_object_id|**bigint**|ID der speicheroptimierten Tabelle.|  
|index_id|**int**|Die Index-ID.|  
|total_bucket_count|**bigint**|Die Gesamtanzahl der Hashbuckets im Index.|  
|empty_bucket_count|**bigint**|Die Anzahl der leeren Hashbuckets im Index.|  
|avg_chain_length|**bigint**|Die durchschnittliche Länge der Zeilenketten für alle Hashbuckets im Index.|  
|max_chain_length|**bigint**|Die maximale Länge der Zeilenketten in den Hashbuckets.|  
|xtp_object_id|**bigint**|Die in-Memory-OLTP Objekt-ID, die in der speicheroptimierten Tabelle entspricht.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  

## <a name="examples"></a>Beispiele  
  
### <a name="a-troubleshooting-hash-index-bucket-count"></a>A. Problembehandlung bei Hashindex-Bucketanzahl

Die folgende Abfrage kann verwendet werden, um den Hashindex-Bucketanzahl von einer vorhandenen Tabelle zu beheben. Die Abfrage gibt Statistiken zu den Prozentsatz der leeren Buckets und kettenlänge für alle Hash-Indizes für Benutzertabellen.

```sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [table],   
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
    FLOOR((  
      CAST(h.empty_bucket_count as float) /  
        h.total_bucket_count) * 100)  
                             as [empty_bucket_percent],  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM sys.dm_db_xtp_hash_index_stats as h   
  INNER JOIN sys.indexes as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    INNER JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    INNER JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type=1
  ORDER BY [table], [index];  
``` 

Weitere Informationen zum Interpretieren der Ergebnisse dieser Abfrage finden Sie unter [zur Problembehandlung von Hashindizes für Speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) .  

### <a name="b-hash-index-statistics-for-internal-tables"></a>B. Hashindexstatistik für interne Tabellen

Bestimmte Funktionen verwenden Sie interne Tabellen, die Hash-Indizes, z. B. columnstore-Indizes für Speicheroptimierte Tabellen zu nutzen. Die folgende Abfrage gibt Statistiken für Hashindizes für interne Tabellen, die an Benutzertabellen verknüpft sind.

```sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [user_table],
    ia.type_desc as [internal_table_type],
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM sys.dm_db_xtp_hash_index_stats as h   
  INNER JOIN sys.indexes as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    INNER JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    INNER JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type!=1
  ORDER BY [user_table], [internal_table_type], [index]; 
```

Beachten Sie, dass der bucket_count-Wert des Index für die internen Tabellen können nicht geändert werden, daher die Ausgabe dieser Abfrage angesehen werden informative nur. Keine Aktion erforderlich.  

Diese Abfrage wird nicht erwartet, alle Zeilen zurückgegeben, wenn Sie eine Funktion verwenden, die Hash-Indizes für interne Tabellen nutzt. In der folgende speicheroptimierten Tabelle enthält einen columnstore-Index. Nach dem Erstellen dieser Tabelle, wird der Hash-Indizes für interne Tabellen angezeigt werden.

```sql
  CREATE TABLE dbo.table_columnstore
  (
    c1 INT NOT NULL PRIMARY KEY NONCLUSTERED,
    INDEX ix_columnstore CLUSTERED COLUMNSTORE
  ) WITH (MEMORY_OPTIMIZED=ON)
```

## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
