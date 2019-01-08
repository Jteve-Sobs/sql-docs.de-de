---
title: Sys.internal_partitions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0262df2b-5ba7-4715-b17b-3d9ce470a38e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a86c559adeeca787ac0e278eed5fb832b8c00bfd
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537888"
---
# <a name="sysinternalpartitions-transact-sql"></a>Sys.internal_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes Rowset, das interne Daten für columnstore-Indizes für datenträgerbasierte Tabellen nachverfolgt. Diese Rowsets sind intern für columnstore-Indizes und nachverfolgen, die gelöschte Zeilen, Zeilengruppen Zuordnungen und Delta-Zeilengruppen zu speichern. Sie verfolgen die Daten für die einzelnen für jede Tabellenpartition; Jede Tabelle weist mindestens eine Partition. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Rowsets wird neu erstellt jedes Mal, die sie den columnstore-Index neu erstellt.   
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Partitions-ID für diese Partition. Sie ist innerhalb einer Datenbank eindeutig.|  
|object_id|**int**|Objekt-ID für die Tabelle mit der Partition an.|  
|index_id|**int**|Index-ID für den columnstore-Index für die Tabelle definiert.<br /><br /> 1 = gruppierter columnstore-Index<br /><br /> 2 = nicht gruppierter columnstore-Index|  
|partition_number|**int**|Die Nummer der Partition.<br /><br /> 1 = die erste Partition einer partitionierten Tabelle oder die einzelne Partition eine nicht partitionierte Tabelle.<br /><br /> 2 = die zweite Partition, und so weiter.|  
|internal_object_type|**tinyint**|Rowset-Objekte, die zum Nachverfolgen interner Daten für den columnstore-Index.<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP - verfolgt dieser Bitmapindex Zeilen, die als aus dem Columnstore gelöscht markiert sind. Die Bitmap ist für jede Zeilengruppe, da Partitionen Zeilen in mehrere Zeilengruppen enthalten können. Die Zeilen sind, die physisch weiterhin vorhanden und belegt Speicherplatz in den columnstore-Index.<br /><br /> COLUMN_STORE_DELTA_STORE - Stores Gruppen von Zeilen, wird aufgerufen, Zeilengruppen, die nicht in spaltenbasiertem Speicher komprimiert wurden. Jede Tabellenpartition kann NULL oder mehr Zeilengruppen verfügen.<br /><br /> COLUMN_STORE_DELETE_BUFFER – für die Verwaltung von Löschvorgängen an aktualisierbare nicht gruppierte columnstore-Indizes. Wenn eine Abfrage eine Zeile aus der zugrunde liegenden Rowstore-Tabelle gelöscht werden, verfolgt des löschpuffers das Löschen aus dem Columnstore. Wenn die Anzahl der gelöschten Zeilen 1048576 überschreitet, werden sie wieder in die Delete-Bitmap mit Tuple Mover Thread oder durch einen expliziten Reorganize-Befehl zusammengeführt.  Zu jedem Zeitpunkt in der Zeit stellt die Gesamtmenge der die Delete-Bitmap und des löschpuffers alle gelöschte Zeilen.<br /><br /> COLUMN_STORE_MAPPING_INDEX – wird nur verwendet, wenn der gruppierte columnstore-Index einen nicht gruppierten sekundären Index hat. Dadurch wird nicht gruppierte Indexschlüssel die richtigen Zeilengruppe und eine Zeilen-ID in den columnstore-Index zugeordnet. Es speichert nur den Schlüssel für Zeilen, die in einer anderen Zeilengruppe zu verschieben; Dies tritt auf, wenn eine Delta-Zeilengruppe im Columnstore komprimiert wird und ein Merge-Vorgang Zeilen aus zwei verschiedenen Zeilengruppen zusammengeführt.|  
|Row_group_id|**int**|ID für die Deltastore-Zeilengruppe. Jede Tabellenpartition kann NULL oder mehr Zeilengruppen verfügen.|  
|hobt_id|**bigint**|Die ID des Rowsetobjekts, interne. Dies ist eine gute Schlüssel zum Verknüpfen mit anderen DMVs, um weitere Informationen zu den physischen Eigenschaften des internen Rowsets zu erhalten.|  
|rows|**bigint**|Die ungefähre Anzahl der Zeilen in dieser Partition.|  
|data_compression|**tinyint**|Der Status der Komprimierung für das Rowset:<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE|  
|data_compression_desc|**nvarchar(60)**|Der Status der Komprimierung für jede Partition. Mögliche Werte für rowstore-Tabellen sind NONE, ROW und PAGE. Mögliche Werte für columnstore-Tabellen sind COLUMNSTORE und COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neue interne Columnstore-Indizes wird neu erstellt jedes Mal erstellt oder neu erstellt einen columnstore-Index.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. Zeigen Sie alle die intern Rowsets für eine Tabelle  
 In diesem Beispiel gibt alle von der internen columnstore-Rowsets für eine Tabelle zurück. Sie können auch die Hobt_id verwenden, finden Sie weitere Informationen zu bestimmten Rowset.  
  
```  
SELECT i.object_id, i.index_id, i.name, p.hobt_id, p.internal_object_type_id, p.internal_object_type_desc  
FROM sys.internal_partitions AS p  
JOIN sys.indexes AS i  
on i.object_id = p.object_id  
WHERE p.object_id = OBJECT_ID ( '<table name' ) ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
