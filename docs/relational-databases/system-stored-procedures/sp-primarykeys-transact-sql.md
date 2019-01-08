---
title: Sp_primarykeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 484890cfe30ace1c65ea45fe2d9e447a6396b52e
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591454"
---
# <a name="spprimarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt für die angegebene Remotetabelle die Primärschlüsselspalten zurück, wobei pro Schlüsselspalte eine Zeile ausgegeben wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@table_server =** ] **"**_Table_server"_  
 Der Name des Verbindungsservers, von dem Primärschlüsselinformationen zurückgegeben werden sollen. *Table_server* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@table_name =** ] **"**_Table_name_**"**  
 Der Name der Tabelle, für die Primärschlüsselinformationen bereitgestellt werden sollen. *TABLE_NAME*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_schema =** ] **"**_Table_schema_**"**  
 Das Tabellenschema. *TABLE_SCHEMA* ist **Sysname**, hat den Standardwert NULL. In der Umgebung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dies dem Tabellenbesitzer.  
  
 [  **@table_catalog =** ] **"**_Table_catalog_**"**  
 Der Name des Katalogs, zu dem das angegebene *Table_name* befindet. In der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Umgebung entspricht dies dem Datenbanknamen. *TABLE_CATALOG* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Der Tabellenkatalog|  
|**NACH "TABLE_SCHEM"**|**sysname**|Tabellenschema|  
|**TABLE_NAME**|**sysname**|Der Name der Tabelle.|  
|**COLUMN_NAME**|**sysname**|Der Name der Spalte.|  
|**KEY_SEQ**|**int**|Die Sequenznummer der Spalte in einem mehrspaltigen Primärschlüssel.|  
|**PK_NAME**|**sysname**|Der Primärschlüsselbezeichner. Gibt NULL zurück, wenn nicht auf die Datenquelle anwendbar|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_primarykeys** wird ausgeführt, indem das PRIMARY_KEYS-Rowset, der die **IDBSchemaRowset** -Schnittstelle des OLE DB-Anbieters für *Table_server*. Die *Table_name*, *Table_schema*, *Table_catalog*, und *Spalte* Parameter werden an dieser Schnittstelle können Sie die Zeilen einschränken übergeben zurückgegeben.  
  
 **Sp_primarykeys** gibt ein leeres Resultset, wenn der OLE DB-Anbieter des angegebenen Verbindungsservers das PRIMARY_KEYS-Rowset nicht unterstützt die **IDBSchemaRowset** Schnittstelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Primärschlüsselspalten vom Server `LONDON1` für die `HumanResources.JobCandidate`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurückgegeben.  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilte Abfragen, gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [Sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [Sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [Sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [Sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [Sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [Sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
