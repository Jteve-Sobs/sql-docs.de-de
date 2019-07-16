---
title: column_store_dictionaries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f675e4d0d40bf9e1db4bf2de6b66b1acfc039873
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140020"
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Wörterbuch, das in speicheroptimierten xVelocity-columnstore-Indizes verwendet wird. Wörterbücher werden zum Codieren bestimmter, aber nicht aller Datentypen verwendet. Daher verfügen nicht alle Spalten in einem columnstore-Index über Wörterbücher. Ein Wörterbuch kann als primäres Wörterbuch (für alle Segmente) und möglicherweise für weitere sekundäre Wörterbücher vorhanden sein, die für eine Teilmenge der Spaltensegmente verwendet werden.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist.|  
|**column_id**|**int**|ID des columnstore-Spalte beginnend mit 1. Die erste Spalte enthält die ID = 1, die zweite Spalte enthält, ID = 2, usw.|  
|**dictionary_id**|**int**|Es können zwei Arten von Wörterbüchern, globale und lokale, ein Spaltensegment zugeordnet sein. Eine Dictionary_id 0 stellt dar, das globale Wörterbuch, das über alle spaltensegmente (eine für jede Zeilengruppe) für diese Spalte gemeinsam verwendet wird.|  
|**version**|**int**|Version des Wörterbuchformats.|  
|**type**|**int**|Wörterbuchtyp:<br /><br /> 1 - Hash Wörterbuch mit **Int** Werte<br /><br /> 2 – nicht verwendet.<br /><br /> 3 – hashwörterbuch, das Zeichenfolgenwerte enthält<br /><br /> 4 - Hash Wörterbuch mit **"float"** Werte<br /><br /> Weitere Informationen zu Wörterbüchern finden Sie unter [Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**int**|Die letzte Daten-ID im Wörterbuch.|  
|**entry_count**|**bigint**|Die Anzahl von Einträgen im Wörterbuch.|  
|**on_disc_size**|**bigint**|Größe des Wörterbuchs in Byte.|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
  
## <a name="permissions"></a>Berechtigungen  
 Alle Spalten erfordern mindestens die VIEW DEFINITION-Berechtigung für die Tabelle. Die folgenden Spalten geben null zurück, es sei denn, der Benutzer auch **wählen** Berechtigung: Last_id, Entry_count, Data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

