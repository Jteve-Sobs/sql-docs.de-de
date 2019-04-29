---
title: sys.pdw_nodes_column_store_segments (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2018
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
author: hirokib
ms.author: elbutter
manager: jrj
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b7bb600d4eda0f91be025baee7c6ecd35f99c9da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62715867"
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Enthält eine Zeile für jede Spalte in einem columnstore-Index.  

| Spaltenname                 | Datentyp  | Description                                                  |
| --------------------------- | ---------- | ------------------------------------------------------------ |
| **partition_id**            | **bigint** | Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.     |
| **hobt_id**                 | **bigint** | ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist. |
| **column_id**               | **int**    | ID der columnstore-Spalte.                                |
| **segment_id**              | **int**    | Die ID des Spaltensegments. Für die Abwärtskompatibilität weiterhin, dass der Spaltenname Segment_id aufgerufen werden, obwohl dies die Rowgroup-ID ist Sie können eindeutig identifizieren, ein Segment, das mit < Hobt_id Partition_id, Column_id >, < Segment_id >. |
| **version**                 | **int**    | Die Version des Spaltensegmentformats.                        |
| **encoding_type**           | **int**    | Der Typ für dieses Segment verwendete Codierungstyp:<br /><br /> 1 = VALUE_BASED - nicht-/ binäre Zeichenfolge mit kein Wörterbuch (vergleichbar mit 4 mit internen Varianten)<br /><br /> 2 = VALUE_HASH_BASED - Zeichenfolge/Binary-Spalte mit Werten im Wörterbuch<br /><br /> 3 = STRING_HASH_BASED - Zeichenfolge/Binary-Spalte mit Werten im Wörterbuch<br /><br /> 4 = STORE_BY_VALUE_BASED - nicht-/ binäre Zeichenfolge mit kein Wörterbuch<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - Zeichenfolge/Binary, kein Wörterbuch<br /><br /> Alle Codierungen nutzen Bit-Packen und führen Sie mit der Länge Codierung Wenn möglich. |
| **row_count**               | **int**    | Die Anzahl der Zeilen in der Zeilengruppe.                             |
| **has_nulls**               | **int**    | 1, wenn das Spaltensegment NULL-Werte enthält.                     |
| **base_id**                 | **bigint** | Basiswert-ID, wenn der Codierungstyp 1 verwendet wird.  Wenn der Codierungstyp 1 nicht verwendet wird, wird Base_id auf 1 festgelegt. |
| **magnitude**               | **float**  | Größe, wenn der Codierungstyp 1 verwendet wird.  Wenn der Codierungstyp 1 nicht verwendet wird, wird Magnitude auf 1 festgelegt. |
| **primary__dictionary_id**  | **int**    | Die ID des primären Wörterbuchs. Ein Wert ungleich Null zeigt auf dem lokalen Verzeichnis für diese Spalte in das aktuelle Segment (d. h. die Zeilengruppe). Der Wert-1 gibt an, dass keine lokalen Verzeichnis für dieses Segment. |
| **secondary_dictionary_id** | **int**    | Die ID des sekundären Wörterbuchs. Ein Wert ungleich Null zeigt auf dem lokalen Verzeichnis für diese Spalte in das aktuelle Segment (d. h. die Zeilengruppe). Der Wert-1 gibt an, dass keine lokalen Verzeichnis für dieses Segment. |
| **min_data_id**             | **bigint** | Mindestdaten-ID im Spaltensegment.                       |
| **max_data_id**             | **bigint** | Maximale Daten-ID im Spaltensegment.                       |
| **null_value**              | **bigint** | Ein Wert, der zum Darstellen von NULL-Werten verwendet wird.                               |
| **on_disk_size**            | **bigint** | Die Größe des Segments in Byte.                                    |
| **pdw_node_id**             | **int**    | Der eindeutige Bezeichner des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten. |

## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  

Verknüpfen Sie sys.pdw_nodes_column_store_segments mit anderen Systemtabellen, um zu bestimmen, die Anzahl der columnstore-Segmente pro logischen Tabelle. 

```sql
SELECT  sm.name           as schema_nm
,       tb.name           as table_nm
,       nc.name           as col_nm
,       nc.column_id
,       COUNT(*)          as segment_count
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb                   ON  sm.[schema_id]          = tb.[schema_id]
JOIN    sys.[pdw_table_mappings] mp       ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt         ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[pdw_nodes_partitions] np     ON  np.[object_id]          = nt.[object_id]
                                          AND np.[pdw_node_id]        = nt.[pdw_node_id]
                                          AND np.[distribution_id]    = nt.[distribution_id]
JOIN    sys.[pdw_nodes_columns] nc        ON  np.[object_id]          = nc.[object_id]
                                          AND np.[pdw_node_id]        = nc.[pdw_node_id]
                                          AND np.[distribution_id]    = nc.[distribution_id]
JOIN    sys.[pdw_nodes_column_store_segments] rg  ON  rg.[partition_id]         = np.[partition_id]
                                                      AND rg.[pdw_node_id]      = np.[pdw_node_id]
                                                      AND rg.[distribution_id]  = np.[distribution_id]
                                                      AND rg.[column_id]        = nc.[column_id]
GROUP BY    sm.name
,           tb.name
,           nc.name
,           nc.column_id  
ORDER BY    table_nm
,           nc.column_id
,           sm.name
```

## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW SERVER STATE**-Berechtigung.  

## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  

  

