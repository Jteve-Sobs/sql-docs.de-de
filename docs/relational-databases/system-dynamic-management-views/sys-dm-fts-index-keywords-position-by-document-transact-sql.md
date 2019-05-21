---
title: sys.dm_fts_index_keywords_position_by_document (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document
- sys.dm_fts_index_keywords_position_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords_position_by_document dynamic management view
ms.assetid: 0d70184f-baa2-411b-a32d-a4c5af890edd
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 12c557029b0b479fbb780fdd93ae05faa4c26735
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944337"
---
# <a name="sysdmftsindexkeywordspositionbydocument-transact-sql"></a>sys.dm_fts_index_keywords_position_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Positionsinformationen Schlüsselwort in den indizierten Dokumenten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Argumente  
 db_id('*database_name*')  
 Ein Aufruf der [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID, die die dm_fts_index_keywords_position_by_document verwendet, um die angegebene Datenbank zu suchen.  
  
 object_id('*table_name*')  
 Ein Aufruf der [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spalte|Datentyp|Description|  
|------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**varbinary(128)**|Binäre Zeichenfolge, die das Schlüsselwort darstellt.|  
|display_term|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom internen Format abgeleitet, das im Volltextindex gespeichert ist.|  
|column_id|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|document_id|**bigint**|Die ID des Dokuments bzw. der Zeile für die Volltextindizierung des aktuellen Ausdrucks. Diese ID entspricht dem Volltextschlüsselwert dieses Dokuments bzw. dieser Zeile.|  
|position|**int**|Die Position des Schlüsselworts im Dokument.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die DMV zur Identifizierung des Speicherorts der indizierte Wörter in indizierten Dokumenten. Diese DMV kann verwendet werden, um die Problembehandlung für Probleme bei **dm_fts_index_keywords_by_document** gibt an, die Wörter in den Volltextindex, aber wenn Sie eine Abfrage mit die Wörter ausführen, wird das Dokument wird nicht zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert CREATE FULLTEXT CATALOG-Berechtigungen und die SELECT-Berechtigung für die vom Volltextindex abgedeckten Spalten.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Schlüsselwörter aus dem Volltextindex, der die `Production.Document` Tabelle mit den `AdventureWorks` -Beispieldatenbank.  
  
```  
USE AdventureWorks2012;  
GO   
  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
);   
GO  
```  
  
 Sie können ein Prädikat auf den anderen Columns_id wie die folgende Beispielabfrage, weiter isolieren, die Standorte hinzufügen.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [Verbessern der Leistung von Volltextindizes](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [Volltextsuche und semantischen Suchfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Volltextsuche und semantische Suche von gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
