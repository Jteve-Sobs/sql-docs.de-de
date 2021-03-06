---
description: sys. pdw_nodes_partitions (Transact-SQL)
title: sys. pdw_nodes_partitions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b13e5da130d7b122f9b79e1996ea3fdb0792e25a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475385"
---
# <a name="syspdw_nodes_partitions-transact-sql"></a>sys. pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält eine Zeile für jede Partition aller Tabellen und die meisten Index Typen in einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Datenbank. Alle Tabellen und Indizes enthalten mindestens eine Partition, unabhängig davon, ob Sie explizit partitioniert sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|die ID der Partition. Ist innerhalb einer Datenbank eindeutig.|  
|object_id|**int**|ID des Objekts, zu dem diese Partition gehört. Jede Tabelle oder Sicht besteht aus mindestens einer Partition.|  
|index_id|**int**|ID des Indexes innerhalb des Objekts, zu dem diese Partition gehört.|  
|partition_number|**int**|Auf 1 basierende Partitionsnummer im besitzenden Index oder Heap. Für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ist der Wert dieser Spalte 1.|  
|hobt_id|**bigint**|Die ID des Data Heap-oder B-Struktur (hubt), das die Zeilen für diese Partition enthält.|  
|rows|**bigint**|Die ungefähre Anzahl der Zeilen in dieser Partition. |  
|data_compression|**int**|Gibt den Status der Komprimierung für jede Partition an:<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|**nvarchar(60)**|Gibt den Status der Komprimierung für jede Partition an. Mögliche Werte sind NONE, ROW und PAGE.|  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knotens.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `CONTROL SERVER`-Berechtigung.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>Beispiel A: Anzeigen von Zeilen in jeder Partition in jeder Verteilung 

**Gilt für:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
Verwenden Sie [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) , um die Anzahl der Zeilen in jeder Partition innerhalb der Verteilung anzuzeigen.

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>Beispiel B: verwendet System Sichten, um Zeilen in jeder Partition jeder Verteilung einer Tabelle anzuzeigen.

**Gilt für:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
Diese Abfrage gibt die Anzahl der Zeilen in jeder Partition jeder Verteilung der Tabelle zurück `myTable` .  
 
```sql  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

