---
title: Sys. dm_fts_index_keywords (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e2b5631443603ea111c3ba154726ec3e6b39e0df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900950"
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum Inhalt eines Volltextindex für die angegebene Tabelle zurück.  
  
 **Sys. dm_fts_index_keywords** ist eine dynamische Verwaltungsfunktion.  
  
> [!NOTE]  
>  Verwenden Sie zum Anzeigen von Informationen für den Volltextindex auf niedrigerer Ebene der [dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md) dynamische Verwaltungsfunktion auf Dokumentebene.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>Argumente  
 db_id('*database_name*')  
 Ein Aufruf der [DB_ID()](../../t-sql/functions/db-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Datenbanknamen und gibt die Datenbank-ID, die **Sys. dm_fts_index_keywords** verwendet, um die angegebene Datenbank zu suchen. Wenn *database_name* nicht angegeben ist, wird die aktuelle Datenbank-ID zurückgegeben.  
  
 object_id('*table_name*')  
 Ein Aufruf der [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md) Funktion. Diese Funktion akzeptiert einen Tabellennamen und gibt die Tabellen-ID der Tabelle zurück, die den zu überprüfenden Volltextindex enthält.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Schlüsselwort**|**nvarchar(4000)**|Die hexadezimale Darstellung des Schlüsselworts in den Volltextindex gespeichert.<br /><br /> Hinweis: OxFF stellt das Sonderzeichen, das das Ende einer Datei oder eines Datasets angegeben.|  
|**display_term**|**nvarchar(4000)**|Die Klartextform des Schlüsselworts. Dieses Format wird vom Hexadezimalformat abgeleitet.<br /><br /> Hinweis: Die **Display_term** -Wert für OxFF ist "END OF FILE".|  
|**column_id**|**int**|Die ID der Spalte für die Volltextindizierung des aktuellen Schlüsselworts.|  
|**document_count**|**int**|Die Anzahl der Dokumente bzw. Zeilen, die den aktuellen Begriff enthalten.|  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebenen Informationen **Sys. dm_fts_index_keywords** eignet sich für die Suche nach der folgenden unter anderem:  
  
-   Ob ein Schlüsselwort ein Teil des Volltextindexes ist  
  
-   Wie viele Dokumente bzw. Zeilen ein gegebenes Schlüsselwort enthalten  
  
-   Das häufigste Schlüsselwort im Volltextindex:  
  
    -   **Document_count** aller *Keyword_value* im Vergleich zur Summe **Document_count**, der Dokumentanzahl von 0xFF.  
  
    -   Häufige oder gemeinsame Schlüsselwörter eignen sich in der Regel für die Deklaration als Stoppwörter.  
  
> [!NOTE]  
>  Die **Document_count** zurückgegebenes **Sys. dm_fts_index_keywords** möglicherweise für ein bestimmtes Dokument weniger genau als die Anzahl von zurückgegebenen **dm_fts_index_keywords_by_document** oder **CONTAINS** Abfrage. Die mögliche Ungenauigkeit liegt bei ca. 1 %. Diese Ungenauigkeit kann auftreten, weil eine **Document_id** gezählt werden kann, zweimal, wenn sie über mehrere Zeilen im indexfragment oder weiterhin Wenn es mehr als einmal in der gleichen Zeile angezeigt wird. Um einen genaueren Zählwert für ein bestimmtes Dokument zu erhalten, verwenden **dm_fts_index_keywords_by_document** oder **CONTAINS** Abfrage.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. Anzeigen des Inhalts eines Volltextindex auf hoher Ebene  
 Im folgenden Beispiel werden Informationen über den Inhalt des Volltextindexes auf hoher Ebene in der `HumanResources.JobCandidate`-Tabelle angezeigt.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
