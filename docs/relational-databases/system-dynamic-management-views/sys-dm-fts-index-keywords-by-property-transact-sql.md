---
title: sys.dm_fts_index_keywords_by_property (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords_by_property
- dm_fts_index_keywords_by_property_TSQL
- sys.dm_fts_index_keywords_by_property
- sys.dm_fts_index_keywords_by_property_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- search property lists [SQL Server], viewing keywords by property
- full-text search [SQL Server], viewing keywords
- sys.dm_fts_index_keywords_by_property dynamic management view
ms.assetid: fa41e052-a79a-4194-9b1a-2885f7828500
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: ed8d04f571deb231f3dbea4d840ee69e3ea1b140
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944343"
---
# <a name="sysdmftsindexkeywordsbyproperty-transact-sql"></a>sys.dm_fts_index_keywords_by_property (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt alle eigenschaftsbezogenen Inhalte im Volltextindex einer angegebenen Tabelle zurück. Dies schließt alle Daten ein, die zu Eigenschaften gehören, die von der diesem Volltextindex zugeordneten Sucheigenschaftenliste registriert wurden.  
  
 dm_fts_index_keywords_by_property ist eine dynamische Verwaltungsfunktion, die Ihnen ermöglicht, finden Sie unter registrierten Eigenschaften von IFilters zur indexzeit als auch den genauen Inhalt aller Eigenschaften in den indizierten Dokumenten ausgegeben wurden.  
  
 **Zum Anzeigen von allen auf Dokumentebene Inhalt (einschließlich eigenschaftsbezogenen Inhalte)**  
  
-   [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
 **Auf höherer Ebene Volltextindex-Informationen anzeigen**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
> [!NOTE]  
>  Weitere Informationen zu sucheigenschaftenlisten finden Sie unter [Search Document Properties with Search Property Lists](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_fts_index_keywords_by_property  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>Argumente  
 db_id('*database_name*')  
 Ein Aufruf der [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID, die die dm_fts_index_keywords_by_property verwendet, um die angegebene Datenbank zu suchen. Wenn *database_name* nicht angegeben ist, wird die aktuelle Datenbank-ID zurückgegeben.  
  
 object_id('*table_name*')  
 Ein Aufruf der [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spalte|Datentyp|Description|  
|------------|---------------|-----------------|  
|Schlüsselwort (keyword)|**nvarchar(4000)**|Die hexadezimale Darstellung des Schlüsselworts, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen, das das Ende einer Datei oder eines Datasets angegeben.|  
|display_term|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom internen Format abgeleitet, das im Volltextindex gespeichert ist.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen, das das Ende einer Datei oder eines Datasets angegeben.|  
|column_id|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|document_id|**int**|Die ID des Dokuments bzw. der Zeile für die Volltextindizierung des aktuellen Ausdrucks. Diese ID entspricht dem Volltextschlüsselwert dieses Dokuments bzw. dieser Zeile.|  
|property_id|**int**|Interne Eigenschaften-ID der Sucheigenschaft im Volltextindex der Tabelle, die Sie im OBJECT_ID angegeben ("*Table_name*") Parameters.<br /><br /> Wenn einer Sucheigenschaftenliste eine angegebene Eigenschaft hinzugefügt wird, registriert die Volltext-Engine die Eigenschaft und weist ihr eine interne Eigenschaften-ID zu, die für diese Eigenschaftenliste spezifisch ist. Die interne Eigenschaften-ID stellt eine ganze Zahl dar und ist für eine bestimmte Sucheigenschaftenliste eindeutig. Wenn eine bestimmte Eigenschaft für mehrere Sucheigenschaftenlisten registriert wird, kann für jede Sucheigenschaftenliste eine andere interne Eigenschaften-ID zugewiesen werden.<br /><br /> Hinweis: Die interne Eigenschaften-ID unterscheidet sich von den Eigenschaftsbezeichner für die ganze Zahl, der angegeben wird, wenn Sie die Eigenschaft der sucheigenschaftenliste eine Eigenschaft hinzufügen. Weitere Informationen finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> So zeigen Sie die Zuordnung zwischen Property_id und dem Eigenschaftsnamen an<br />                    [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)|  
  
## <a name="remarks"></a>Hinweise  
 Diese dynamische verwaltungssicht kann beispielsweise folgende Fragen beantworten:  
  
-   Welcher Inhalt wird in einer angegebenen Eigenschaft für eine angegebene DocID gespeichert?  
  
-   Wie gängig ist eine angegebene Eigenschaft im Hinblick auf indizierte Dokumente?  
  
-   Welche Dokumente enthalten eigentlich eine angegebene Eigenschaft? Dies ist nützlich, wenn die Abfrage in einer angegebenen Sucheigenschaft nicht wie erwartet ein Dokument zurückgibt.  
  
 Wenn die Volltextschlüsselspalte wie empfohlen mit dem integer-Datentyp definiert ist, kann die document_id direkt dem Volltextschlüsselwert in der Basistabelle zugeordnet werden.  
  
 Wenn als Datentyp für die Volltextschlüsselspalte jedoch ein anderer Typ als Integer festgelegt ist, stellt document_id nicht den Volltextschlüsselwert in der Basistabelle dar. In diesem Fall um die Zeile in der Basistabelle zu identifizieren, die von ' dm_fts_index_keywords_by_property ' zurückgegeben wird, Sie müssen in dieser Ansicht mit den von zurückgegebenen Ergebnissen verknüpfen [Sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md). Speichern Sie jedoch zuvor die Ausgabe der gespeicherten Prozedur in eine temporäre Tabelle. Klicken Sie dann können Sie die Spalte Document_id von ' dm_fts_index_keywords_by_property ' mit der Spalte DocId verknüpfen, die von dieser gespeicherten Prozedur zurückgegeben wird. Beachten Sie, dass eine **Zeitstempel** Spalte kann nicht empfangen, Werte zum Zeitpunkt des Einfügens, da von automatisch generierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Aus diesem Grund die **Zeitstempel** Spalte konvertiert werden muss, um **varbinary(8)** Spalten. Das folgende Beispiel zeigt die erforderlichen Schritte: In diesem Beispiel *Table_id* ist die ID der Tabelle, *Database_name* ist der Name der Datenbank und *Table_name* ist der Name der Tabelle.  
  
```  
USE database_name;  
GO  
CREATE TABLE #MyTempTable   
   (  
      docid INT PRIMARY KEY ,  
      [key] INT NOT NULL  
   );  
DECLARE @db_id int = db_id(N'database_name');  
DECLARE @table_id int = OBJECT_ID(N'table_name');  
INSERT INTO #MyTempTable EXEC sp_fulltext_keymappings @table_id;  
SELECT * FROM sys.dm_fts_index_keywords_by_property   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert CREATE FULLTEXT CATALOG-Berechtigungen und die SELECT-Berechtigung für die vom Volltextindex abgedeckten Spalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Schlüsselwörter in der `Author`-Eigenschaft im Volltextindex der `Production.Document`-Tabelle der `AdventureWorks`-Beispieldatenbank zurückgegeben. Im Beispiel wird den Alias `KWBPOP` für die Tabelle, die vom **dm_fts_index_keywords_by_property**. Das Beispiel mithilfe von inneren Joins kombiniert Spalten von [Sys. registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) und [Sys. fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
```  
-- Once the full-text index is configured to support property searching  
-- on the Author property, return any keywords indexed for this property.  
USE AdventureWorks2012;  
GO   
SELECT KWBPOP.* FROM   
   sys.dm_fts_index_keywords_by_property( DB_ID(),   
   object_id('Production.Document') ) AS KWBPOP  
   INNER JOIN  
      sys.registered_search_properties AS RSP ON(   
         (KWBPOP.property_id = RSP.property_id)   
         AND (RSP.property_name = 'Author') )  
   INNER JOIN  
      sys.fulltext_indexes AS FTI ON(   
         (FTI.[object_id] = object_id('Production.Document'))   
         AND (RSP.property_list_id = FTI.property_list_id) );  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [Verbessern der Leistung von Volltextindizes](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [sp_fulltext_keymappings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)   
 [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
