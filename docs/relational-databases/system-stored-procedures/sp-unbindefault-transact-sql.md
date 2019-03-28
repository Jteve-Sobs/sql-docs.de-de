---
title: Sp_unbindefault (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unbindefault_TSQL
- sp_unbindefault
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindefault
ms.assetid: c96a6c5e-f3ca-4c1e-b64b-0d8ef6986af8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d34b13931151e5b4490cd64292d66ae38756c125
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534942"
---
# <a name="spunbindefault-transact-sql"></a>sp_unbindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt die Bindung eines Standardwerts an eine Spalte oder einen Aliasdatentyp in der aktuellen Datenbank auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Es wird empfohlen, dass Sie Default-Definitionen erstellen, mit dem DEFAULT-Schlüsselwort in der [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) Anweisungen stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unbindefault [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'object_name'` Ist der Name der Tabelle und Spalte oder der Aliasdatentyp, von dem der Standardwert ist, entfernt werden soll. *Object_name* ist **nvarchar(776)**, hat keinen Standardwert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht zuerst, zweiteilige Bezeichner für Spaltennamen aufzulösen, und versucht dann, zweiteilige Bezeichner für Aliasdatentypen aufzulösen.  
  
 Beim Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp wird auch die Bindung für alle Spalten dieses Datentyps, die denselben Standardwert aufweisen, aufgehoben. Spalten dieses Datentyps mit Standardwerten, die direkt an diese gebunden sind, sind nicht betroffen.  
  
> [!NOTE]  
>  *Object_name* können Klammern enthalten **[]** als begrenzungsbezeichnerzeichen. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'` Wird nur beim Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp verwendet. *Futureonly_flag* ist **varchar(15)**, hat den Standardwert NULL. Wenn *Futureonly_flag* ist **Futureonly**, verlieren vorhandene Spalten des Datentyps nicht der angegebene Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie zum Anzeigen der Text des Standards **Sp_helptext** mit dem Namen des Standardwerts als Parameter.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Aufheben der Bindung eines Standardwerts an eine Tabellenspalte ist die ALTER-Berechtigung für die Tabelle erforderlich. Zum Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp ist für den Datentyp die CONTROL-Berechtigung bzw. für das Schema, zu dem der Datentyp gehört, die ALTER-Berechtigung erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-unbinding-a-default-from-a-column"></a>A. Aufheben der Bindung eines Standardwerts an eine Spalte  
 Im folgenden Beispiel wird die Bindung des an die `hiredate`-Spalte der `employees`-Tabelle gebundenen Standardwerts aufgehoben.  
  
```  
EXEC sp_unbindefault 'employees.hiredate';  
```  
  
### <a name="b-unbinding-a-default-from-an-alias-data-type"></a>B. Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp  
 Im folgenden Beispiel wird die Bindung des an den `ssn`-Aliasdatentyp gebundenen Standardwerts aufgehoben. Die Bindungen aller vorhandenen und zukünftigen Spalten dieses Typs werden aufgehoben.  
  
```  
EXEC sp_unbindefault 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>C. Verwenden von futureonly_flag  
 Im folgenden Beispiel wird die Bindung zukünftiger Verwendungen des Aliasdatentyps `ssn` aufgehoben, ohne dass vorhandene `ssn`-Spalten davon betroffen sind.  
  
```  
EXEC sp_unbindefault 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. Verwendung von begrenzungsbezeichnern  
 Das folgende Beispiel zeigt die Verwendung von begrenzungsbezeichnern im *Object_name* Parameter.  
  
```  
CREATE TABLE [t.3] (c1 int); -- Notice the period as part of the table   
-- name.  
CREATE DEFAULT default2 AS 0;  
GO  
EXEC sp_bindefault 'default2', '[t.3].c1' ;  
-- The object contains two periods;  
-- the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
EXEC sp_unbindefault '[t.3].c1';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [DROP DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
