---
title: Sys. column_store_segments (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: df7698d222c2c2f0f68138eaa5f6289106b97659
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799876"
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile für jedes Spaltensegment in einen columnstore-Index zurück. Es gibt ein Spaltensegment pro Spalte pro Zeilengruppe. Beispielsweise gibt eine Tabelle mit 10 Zeilengruppen und 34 Spalten 340 Zeilen zurück. 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
|**hobt_id**|**bigint**|ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist.|  
|**column_id**|**int**|ID der columnstore-Spalte.|  
|**segment_id**|**int**|Die ID der Zeilengruppe. Für die Abwärtskompatibilität weiterhin, dass der Spaltenname Segment_id aufgerufen werden, obwohl dies die Rowgroup-ID ist Sie können eindeutig identifizieren, ein typsegment unter Verwendung \<Hobt_id, Partition_id, Column_id >, < Segment_id >.|  
|**version**|**int**|Die Version des Spaltensegmentformats.|  
|**encoding_type**|**int**|Der Typ für dieses Segment verwendete Codierungstyp:<br /><br /> 1 = VALUE_BASED - nicht-/ binäre Zeichenfolge mit kein Wörterbuch (sehr ähnlich wie 4 mit internen Varianten)<br /><br /> 2 = VALUE_HASH_BASED - Zeichenfolge/Binary-Spalte mit Werten im Wörterbuch<br /><br /> 3 = STRING_HASH_BASED - Zeichenfolge/Binary-Spalte mit Werten im Wörterbuch<br /><br /> 4 = STORE_BY_VALUE_BASED - nicht-/ binäre Zeichenfolge mit kein Wörterbuch<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - Zeichenfolge/Binary, kein Wörterbuch<br /><br /> Alle Codierungen nutzen Bit-Packen und führen Sie mit der Länge Codierung Wenn möglich.|  
|**row_count**|**int**|Die Anzahl der Zeilen in der Zeilengruppe.|  
|**has_nulls**|**int**|1, wenn das Spaltensegment NULL-Werte enthält.|  
|**base_id**|**bigint**|Basiswert-Id, wenn der Codierungstyp 1 verwendet wird.  Wenn der Codierungstyp 1 nicht verwendet wird, wird Base_id auf-1 festgelegt.|  
|**magnitude**|**float**|Größe, wenn der Codierungstyp 1 verwendet wird.  Wenn der Codierungstyp 1 nicht verwendet wird, wird Magnitude auf-1 festgelegt.|  
|**primary_dictionary_id**|**int**|Der Wert 0 stellt die globale Wörterbuch dar. Der Wert-1 gibt an, dass keine globalen Wörterbuch für diese Spalte erstellt.|  
|**secondary_dictionary_id**|**int**|Ein Wert ungleich Null zeigt auf dem lokalen Verzeichnis für diese Spalte in das aktuelle Segment (d. h. die Zeilengruppe). Der Wert-1 gibt an, dass keine lokalen Verzeichnis für dieses Segment.|  
|**min_data_id**|**bigint**|Die minimale Daten-ID im Spaltensegment.|  
|**max_data_id**|**bigint**|Die maximale Daten-ID im Spaltensegment.|  
|**null_value**|**bigint**|Ein Wert, der zum Darstellen von NULL-Werten verwendet wird.|  
|**on_disk_size**|**bigint**|Die Größe des Segments in Byte.|  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Abfrage gibt Informationen zu Segmenten eines columnstore-Indexes zurück.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Alle Spalten erfordern mindestens **SICHTDEFINITION** Berechtigung für die Tabelle. Die folgenden Spalten geben null zurück, es sei denn, der Benutzer auch **wählen** Berechtigung: Has_nulls, Base_id, Magnitude, Min_data_id, Max_data_id und Null_value.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

