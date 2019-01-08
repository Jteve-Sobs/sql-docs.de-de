---
title: Sp_tables_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f034b1247f9865b83077ed11f644d6fdbbc4cecd
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589385"
---
# <a name="sptablesex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Tabelleninformationen zu den Tabellen auf dem angegebenen Verbindungsserver zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@table_server=** ] **"**_Table_server_**"**  
 Der Name des Verbindungsservers, für den Tabelleninformationen zurückgegeben werden sollen. *Table_server* ist **Sysname**, hat keinen Standardwert.  
  
 [ **,** [  **@table_name=** ] **"**_Table_name_**"**]  
 Der Name der Tabelle, für die Datentypinformationen zurückgegeben werden sollen. *TABLE_NAME*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_schema=** ] **"**_Table_schema_**"**]  
 Das Tabellenschema. *TABLE_SCHEMA*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_catalog=** ] **"**_Table_catalog_**"**  
 Der Name der Datenbank, in der angegebenen *Table_name* befindet. *TABLE_CATALOG* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_type=** ] **"**_Table_type_**"**  
 Der Typ der zurückzugebenden Tabelle. *TABLE_TYPE* ist **Sysname**, hat den Standardwert NULL und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**ALIAS**|Der Name eines Alias|  
|**GLOBALE TEMPORÄRE**|Der Name einer systemweit verfügbaren temporären Tabelle|  
|**LOKALE TEMPORÄRE**|Der Name einer nur für den aktuellen Auftrag verfügbaren temporären Tabelle|  
|**SYNONYM**|Der Name eines Synonyms|  
|**SYSTEMTABELLE**|Der Name einer Systemtabelle|  
|**SYSTEMSICHT**|Der Name einer Systemsicht|  
|**TABLE**|Der Name einer Benutzertabelle|  
|**VIEW**|Der Name einer Sicht|  
  
 [  **@fUsePattern=** ] **"**_fUsePattern_**"**  
 Bestimmt, ob die Zeichen **_**, **%**, **[**, und **]** als Platzhalterzeichen interpretiert werden. Gültige Werte sind 0 (Mustervergleich ist deaktiviert) und 1 (Mustervergleich ist aktiviert). *fUsePattern* ist vom Datentyp **bit**. Der Standardwert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Name des Qualifizierers Tabelle. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Namensgebung für Tabellen (_Qualifizierer_**.** _Besitzer_**.** _Namen_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. In einigen anderen Produkten stellt sie den Servernamen der datenbankumgebung, von der Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**NACH "TABLE_SCHEM"**|**sysname**|Name des Tabellenbesitzers. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Spalte dar, den Namen des Datenbankbenutzers, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_TYPE**|**varchar(32)**|Tabelle, Systemtabelle oder Sicht.|  
|**"HINWEISE"**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_tables_ex** wird ausgeführt, indem die TABLES-Rowset, der die **IDBSchemaRowset** -Schnittstelle des OLE DB-Anbieters für *Table_server*. Die *Table_name*, *Table_schema*, *Table_catalog*, und *Spalte* Parameter werden an dieser Schnittstelle können Sie die Zeilen einschränken übergeben zurückgegeben.  
  
 **Sp_tables_ex** gibt ein leeres Resultset, wenn der OLE DB-Anbieter des angegebenen Verbindungsservers das TABLES-Rowset nicht unterstützt die **IDBSchemaRowset** Schnittstelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Tabellen zurückgegeben, die sich im `HumanResources`-Schema in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem verknüpften Server `LONDON2` befinden.  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilte Abfragen, gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [Sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [Sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [Sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [Sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [Sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [Sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
