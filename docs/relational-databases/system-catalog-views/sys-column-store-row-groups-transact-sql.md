---
title: column_store_row_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: fff57d41e522ae2e002809982bfeb084c28bbbba
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531658"
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu gruppierten Columnstore-Indizes auf Segmentbasis bereit, um den Administrator bei Fragen zur Systemverwaltung zu unterstützen. **column_store_row_groups** verfügt über eine Spalte für die Gesamtzahl der physisch gespeicherten Zeilen (einschließlich als gelöscht markierten) und eine Spalte für die Anzahl der Zeilen als gelöscht markiert. Verwendung **column_store_row_groups** um zu bestimmen, welche Zeile Gruppen haben einen hohen Prozentsatz gelöschter Zeilen und neu erstellt werden sollen.  
   
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID der Tabelle, in der dieser Index definiert ist.|  
|**index_id**|**int**|ID des Indexes, der diesen columnstore-Index enthält.|  
|**partition_number**|**int**|ID der Tabellenpartition, die die row_group_id der Zeilengruppe enthält. Sie können partition_number verwenden, um diese DMV mit sys.partitions zu verknüpfen.|  
|**row_group_id**|**int**|Die dieser Zeilengruppe zugeordnete Zeilengruppenzahl. Diese ist innerhalb der Partition eindeutig.<br /><br /> -1 = Ende einer in-Memory-Tabelle.|  
|**delta_store_hobt_id**|**bigint**|Die Hobt_id für OPEN-Zeilengruppe im deltaspeicher.<br /><br /> NULL, wenn die Zeilengruppe nicht im deltaspeicher ist.<br /><br /> NULL für das Ende einer in-Memory-Tabelle.|  
|**state**|**tinyint**|Die der state_description zugeordnete ID.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = TOMBSTONE|  
|**state_description**|**nvarchar(60)**|Beschreibung des persistenten Status der Zeilengruppe:<br /><br /> UNSICHTBARE – ein ausgeblendetes komprimiertes Segment gerade aus Daten in einem deltastore erstellt wird. Lesevorgänge nutzen den Deltastore, bis das unsichtbare komprimierte Segment abgeschlossen ist. Anschließend werden das neue Segment sichtbar gemacht und der Quelldeltastore entfernt.<br /><br /> GEÖFFNET – eine Zeilengruppe für Lese-/Schreibzugriff, die neue Datensätze akzeptiert. Eine offene Zeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.<br /><br /> GESCHLOSSEN – eine Zeilengruppe, die ausgefüllt wurde, aber vom tupelverschiebungsprozess noch nicht komprimiert.<br /><br /> KOMPRIMIERT: eine Zeilengruppe, die aufgefüllt und komprimiert wurde.|  
|**total_rows**|**bigint**|Gesamtzahl der Zeilen, die in der Zeilengruppe physisch gespeichert sind. Einige wurden u. U. gelöscht, sind aber weiterhin gespeichert. Die maximale Anzahl der Zeilen in einer Zeilengruppe beträgt 1.048.576 (hexadezimal FFFFF).|  
|**deleted_rows**|**bigint**|Gesamtzahl der Zeilen in der Zeilengruppe, die als gelöscht markiert sind. Dies ist für DELTA-Zeilengruppen immer 0.|  
|**size_in_bytes**|**bigint**|Größe aller Daten (in Bytes) in dieser Zeilengruppe (ausgenommen von Metadaten oder freigegebenen Wörterbüchern) sowohl für DELTA- als auch für COLUMNSTORE-Zeilengruppen.|  
  
## <a name="remarks"></a>Hinweise  
 Gibt eine Zeile für jede columnstore-Zeilengruppe für jede Tabelle zurück, die über einen gruppierten oder nicht gruppierten columnstore-Index verfügt.  
  
 Verwendung **column_store_row_groups** um die Anzahl der in der Zeilengruppe und die Größe der Zeilengruppe enthaltenen Zeilen zu bestimmen.  
  
 Wenn die Anzahl der gelöschten Zeilen in einer Zeilengruppe auf einen hohen Prozentsatz der Gesamtzeilen ansteigt, wird die Tabelle weniger effizient. Erstellen Sie den columnstore-Index neu, um die Tabellengröße zu verringern und die Datenträger-E/A zu reduzieren, die zum Lesen der Tabelle erforderlich ist. Die Verwendung des columnstore-Index neu erstellen. die **neu erstellen** Möglichkeit, die **ALTER INDEX** Anweisung.  
  
 Aktualisierbare Columnstore fügt zunächst neue Daten in eine **öffnen** Zeilengruppe, die im Rowstore-Format und wird manchmal auch als Deltatabelle bezeichnet.  Wenn eine offene Zeilengruppe voll ist, ändert sich der Status **geschlossen**. Eine geschlossene Zeilengruppe im columnstore-Format komprimiert wird, durch die tupelverschiebungsfunktion und ändert sich der Status **COMPRESSED**.  Die Tupelverschiebungsfunktion ist ein Hintergrundprozess, der regelmäßig aktiv wird und überprüft, ob geschlossene Zeilengruppen vorhanden sind, die in eine columnstore-Zeilengruppe komprimiert werden können.  Die Tupelverschiebungsfunktion gibt außerdem alle Zeilengruppen frei, in denen alle Zeilen gelöscht wurden. Freigegebene Zeilengruppen werden als **TOMBSTONE**. Um die tupelverschiebungsfunktion direkt auszuführen, verwenden Sie die **neu organisieren** Möglichkeit, die **ALTER INDEX** Anweisung.  
  
 Wenn eine columnstore-Zeilengruppe aufgefüllt wurde, wird sie komprimiert und akzeptiert keine neuen Zeilen mehr. Wenn aus einer komprimierten Gruppe Zeilen gelöscht werden, verbleiben sie zwar, werden aber als gelöscht gekennzeichnet. Updates einer komprimierten Gruppe werden als Löschvorgang für die komprimierte Gruppe und als Einfügevorgang für eine offene Gruppe implementiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Gibt Informationen für eine Tabelle zurück, wenn der Benutzer hat **SICHTDEFINITION** Berechtigung für die Tabelle.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel verknüpft die **column_store_row_groups** Tabelle mit anderen Systemtabellen, um Informationen über bestimmte Tabellen zurückzugeben. Die berechnete `PercentFull`-Spalte ist eine Schätzung der Effizienz der Zeilengruppe. Nach Informationen zu einer einzelnen Tabelle entfernen Sie die kommentarbindestriche vor der **, in denen** -Klausel und geben Sie einen Tabellennamen an.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)     
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

