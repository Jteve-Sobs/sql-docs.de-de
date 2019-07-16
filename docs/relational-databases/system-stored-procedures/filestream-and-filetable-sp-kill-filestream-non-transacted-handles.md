---
title: Sp_kill_filestream_non_transacted_handles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98c986c26c8d0d0cc6e2b8ff3573f0a20d938975
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942267"
---
# <a name="spkillfilestreamnontransactedhandles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Schließt nicht transaktionale Dateihandles für FileTable-Daten.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Argumente  
 *table_name*  
 Der Name der Tabelle, in der nicht transaktionale Handles zu schließen sind.  
  
 Sie können übergeben *Table_name* ohne *Handle_id* schließen Sie alle geöffneten nicht transaktionalen Handles für zu der FileTable.  
  
 Sie können NULL übergeben, für den Wert des *Table_name* schließen Sie alle geöffneten nicht transaktionalen Handles zu für alle FileTables in der aktuellen Datenbank. NULL, ist der Standardwert.  
  
 *handle_id*  
 Die optionale ID des einzelnen Handles, der geschlossen werden soll. Sie erhalten die *Handle_id* aus der [dm_filestream_non_transacted_handles &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) dynamische verwaltungssicht. Jede ID ist in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz eindeutig. Bei Angabe von *Handle_id*, müssen Sie auch einen Wert für *Table_name*.  
  
 Sie können NULL übergeben, für den Wert des *Handle_id* alle geöffneten um zu schließen nicht transaktionalen Handles für die FileTable gemäß *Table_name*. NULL, ist der Standardwert.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-set"></a>Resultset  
 Keine  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Die *Handle_id* erforderlich **Sp_kill_filestream_non_transacted_handles** bezieht sich nicht auf die Sitzungs-ID oder Arbeitseinheit, die in anderen dient **kill** Befehle.  
  
 Weitere Informationen finden Sie unter [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Metadaten  
 Informationen zu geöffneten nicht transaktionalen Dateihandles, Fragen Sie die dynamische verwaltungssicht [dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Sie benötigen **VIEW DATABASE STATE** Berechtigung zum Abrufen von Dateihandles aus der **dm_filestream_non_transacted_handles** dynamische verwaltungssicht und zum Ausführen von **Sp_kill_filestream_non_ Transacted_handles**.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele zeigen das Aufrufen von **Sp_kill_filestream_non_transacted_handles** um nicht transaktionale Dateihandles für FileTable-Daten zu schließen.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
```  
  
 Das folgende Beispiel zeigt, wie Sie mithilfe eines Skripts zum Abrufen einer *Handle_id* und schließen Sie sie.  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md)  
 [FileStream und FileTable: dynamische Verwaltungssichten (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[FileStream und FileTable-Katalogsichten (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[Sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
