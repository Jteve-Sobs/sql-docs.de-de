---
title: Sys.pdw_nodes_column_store_row_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8604cdc89c755dcd1564e842963f3afa311f1786
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031971"
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu gruppierten columnstore-Indizes auf Segmentbasis um den Administrator, die Systems Management in Entscheidungen unterstützen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. **Sys.pdw_nodes_column_store_row_groups** verfügt über eine Spalte für die Gesamtzahl der physisch gespeicherten Zeilen (einschließlich als gelöscht markierten) und eine Spalte für die Anzahl der Zeilen als gelöscht markiert. Verwendung **sys.pdw_nodes_column_store_row_groups** um zu bestimmen, welche Zeile Gruppen haben einen hohen Prozentsatz gelöschter Zeilen und neu erstellt werden sollen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID der zugrunde liegenden Tabelle. Dies ist der physischen Tabelle auf dem Computeknoten, die nicht dem Objekt-ID für der logischen Tabelle auf dem steuerknoten. Object_id entspricht z. B. nicht mit Object_id in ' sys.Tables '.<br /><br /> Verwenden Sie zum Verknüpfen mit sys.tables sys.pdw_index_mappings.|  
|**index_id**|**int**|ID des gruppierten columnstore-Indexes auf *Object_id* Tabelle.|  
|**partition_number**|**int**|ID der Tabellenpartition, die Zeilengruppe enthält *Row_group_id*. Sie können *Partition_number* Diese DMV mit sys.partitions zu verknüpfen.|  
|**row_group_id**|**int**|ID der dieser Zeilengruppe. Diese ist innerhalb der Partition eindeutig.|  
|**dellta_store_hobt_id**|**bigint**|Die hobt_id für Deltazeilengruppen oder NULL, wenn der Zeilengruppentyp nicht Delta ist. Eine Deltazeilengruppe ist eine Zeilengruppe mit Lese-/Schreibzugriff, die neue Datensätze akzeptiert. Eine deltazeilengruppe hat den **öffnen** Status. Eine Deltazeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.|  
|**state**|**tinyint**|Die der state_description zugeordnete ID.<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Beschreibung des persistenten Status der Zeilengruppe:<br /><br /> GEÖFFNET – eine Zeilengruppe für Lese-/Schreibzugriff, die neue Datensätze akzeptiert. Eine offene Zeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.<br /><br /> GESCHLOSSEN – eine Zeilengruppe, die ausgefüllt wurde, aber vom tupelverschiebungsprozess noch nicht komprimiert.<br /><br /> KOMPRIMIERT: eine Zeilengruppe, die aufgefüllt und komprimiert wurde.|  
|**total_rows**|**bigint**|Gesamtzahl der Zeilen, die in der Zeilengruppe physisch gespeichert sind. Einige wurden u. U. gelöscht, sind aber weiterhin gespeichert. Die maximale Anzahl der Zeilen in einer Zeilengruppe beträgt 1.048.576 (hexadezimal FFFFF).|  
|**deleted_rows**|**bigint**|Anzahl der Zeilen in der Zeilengruppe physisch gespeichert, die zum Löschen markiert sind.<br /><br /> Die Zeile immer 0 für DELTA-Gruppen.|  
|**size_in_bytes**|**int**|Kombinierte Größe in Bytes für alle Seiten in dieser Zeilengruppe. Diese Größe umfasst nicht die Größe, die zum Speichern von Metadaten oder freigegebenen Wörterbüchern erforderlich.|  
|**pdw_node_id**|**int**|Eindeutige Id des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten.|  
|**distribution_id**|**int**|Eindeutige Id der Verteilung.|
  
## <a name="remarks"></a>Hinweise  
 Gibt eine Zeile für jede columnstore-Zeilengruppe für jede Tabelle zurück, die über einen gruppierten oder nicht gruppierten columnstore-Index verfügt.  
  
 Verwendung **sys.pdw_nodes_column_store_row_groups** um die Anzahl der in der Zeilengruppe und die Größe der Zeilengruppe enthaltenen Zeilen zu bestimmen.  
  
 Wenn die Anzahl der gelöschten Zeilen in einer Zeilengruppe auf einen hohen Prozentsatz der Gesamtzeilen ansteigt, wird die Tabelle weniger effizient. Erstellen Sie den columnstore-Index neu, um die Tabellengröße zu verringern und die Datenträger-E/A zu reduzieren, die zum Lesen der Tabelle erforderlich ist. Die Verwendung des columnstore-Index neu erstellen. die **neu erstellen** Möglichkeit, die **ALTER INDEX** Anweisung.  
  
 Aktualisierbare Columnstore fügt zunächst neue Daten in eine **öffnen** Zeilengruppe, die im Rowstore-Format und wird manchmal auch als Deltatabelle bezeichnet.  Wenn eine offene Zeilengruppe voll ist, ändert sich der Status **geschlossen**. Eine geschlossene Zeilengruppe im columnstore-Format komprimiert wird, durch die tupelverschiebungsfunktion und ändert sich der Status **COMPRESSED**.  Die Tupelverschiebungsfunktion ist ein Hintergrundprozess, der regelmäßig aktiv wird und überprüft, ob geschlossene Zeilengruppen vorhanden sind, die in eine columnstore-Zeilengruppe komprimiert werden können.  Die Tupelverschiebungsfunktion gibt außerdem alle Zeilengruppen frei, in denen alle Zeilen gelöscht wurden. Freigegebene Zeilengruppen werden als **veraltet**. Um die tupelverschiebungsfunktion direkt auszuführen, verwenden Sie die **neu organisieren** Möglichkeit, die **ALTER INDEX** Anweisung.  
  
 Wenn eine columnstore-Zeilengruppe aufgefüllt wurde, wird sie komprimiert und akzeptiert keine neuen Zeilen mehr. Wenn aus einer komprimierten Gruppe Zeilen gelöscht werden, verbleiben sie zwar, werden aber als gelöscht gekennzeichnet. Updates einer komprimierten Gruppe werden als Löschvorgang für die komprimierte Gruppe und als Einfügevorgang für eine offene Gruppe implementiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW SERVER STATE**-Berechtigung.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Das folgende Beispiel verknüpft die **sys.pdw_nodes_column_store_row_groups** Tabelle mit anderen Systemtabellen, um Informationen über bestimmte Tabellen zurückzugeben. Die berechnete `PercentFull`-Spalte ist eine Schätzung der Effizienz der Zeilengruppe. Informieren Sie sich auf eine einzelne Tabelle entfernen Kommentar Bindestriche vor der WHERE-Klausel aus, und geben Sie einen Tabellennamen.  
  
```  
SELECT IndexMap.object_id,   
  object_name(IndexMap.object_id) AS LogicalTableName,   
  i.name AS LogicalIndexName, IndexMap.index_id, NI.type_desc,   
  IndexMap.physical_name AS PhyIndexNameFromIMap,   
  CSRowGroups.*,  
  100*(ISNULL(deleted_rows,0))/total_rows AS PercentDeletedRows   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.pdw_index_mappings AS IndexMap  
    ON i.object_id = IndexMap.object_id  
    AND i.index_id = IndexMap.index_id  
JOIN sys.pdw_nodes_indexes AS NI  
    ON IndexMap.physical_name = NI.name  
    AND IndexMap.index_id = NI.index_id  
JOIN sys.pdw_nodes_column_store_row_groups AS CSRowGroups  
    ON CSRowGroups.object_id = NI.object_id   
    AND CSRowGroups.pdw_node_id = NI.pdw_node_id  
AND CSRowGroups.index_id = NI.index_id      
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

Die folgenden [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] Beispiel zählt die Zeilen pro Partition aus, für gruppierte columnstore auch, speichert wie viele Zeilen in Gruppen geöffnet, geschlossen oder komprimierte Zeile sind:  

```
SELECT
    s.name AS [Schema Name]
    ,t.name AS [Table Name]
    ,rg.partition_number AS [Partition Number]
    ,SUM(rg.total_rows) AS [Total Rows]
    ,SUM(CASE WHEN rg.State = 1 THEN rg.Total_rows Else 0 END) AS [Rows in OPEN Row Groups]
    ,SUM(CASE WHEN rg.State = 2 THEN rg.Total_Rows ELSE 0 END) AS [Rows in Closed Row Groups]
    ,SUM(CASE WHEN rg.State = 3 THEN rg.Total_Rows ELSE 0 END) AS [Rows in COMPRESSED Row Groups]
FROM sys.pdw_nodes_column_store_row_groups rg
JOIN sys.pdw_nodes_tables pt
ON rg.object_id = pt.object_id AND rg.pdw_node_id = pt.pdw_node_id AND pt.distribution_id = rg.distribution_id
JOIN sys.pdw_table_mappings tm
ON pt.name = tm.physical_name
INNER JOIN sys.tables t
ON tm.object_id = t.object_id
INNER JOIN sys.schemas s
ON t.schema_id = s.schema_id
GROUP BY s.name, t.name, rg.partition_number
ORDER BY 1, 2
```
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
