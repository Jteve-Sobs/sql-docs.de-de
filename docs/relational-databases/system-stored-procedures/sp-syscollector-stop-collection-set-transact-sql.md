---
title: Sp_syscollector_stop_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_stop_collection_set_TSQL
- sp_syscollector_stop_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_stop_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 4668cfb7-462f-40d0-948c-8f740a792a4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd5c396db88a8377a46bd965b664bc2a667d51de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63001525"
---
# <a name="spsyscollectorstopcollectionset-transact-sql"></a>sp_syscollector_stop_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Beendet einen Sammlungssatz an.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_stop_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @stop_collection_job = ] stop_collection_job ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collection_set_id = ] *collection_set_id*  
 Der eindeutige lokale Bezeichner für den Sammlungssatz. *Collection_set_id* ist **Int** hat den Standardwert NULL. *Collection_set_id* muss einen Wert aufweisen, wenn *Namen* ist NULL.  
  
 [ @name =] '*Namen*"  
 Ist der Name des Sammlungssatzes. *Namen* ist **Sysname** hat den Standardwert NULL. *Namen* muss einen Wert aufweisen, wenn *Collection_set_id* ist NULL.  
  
 [ @stop_collection_job = ] *stop_collection_job*  
 Gibt an, dass der Sammlungsauftrag für den Sammlungssatz beendet wird, falls er ausgeführt wird. *Stop_collection_job* ist **Bit** hat den Standardwert 1.  
  
 *Stop_collection_job* gilt nur für Sammlungssätze, deren Auflistungsmodus auf Zwischenspeicherung festgelegt. Weitere Informationen finden Sie unter [Sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_syscollector_create_collection_set muss im Kontext der msdb-Systemdatenbank ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle Dc_operator (mit EXECUTE-Berechtigung) zum Ausführen dieser Prozedur.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Sammlungssatz mithilfe seines Bezeichners beendet.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
