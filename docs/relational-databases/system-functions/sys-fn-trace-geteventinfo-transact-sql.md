---
title: Sys. fn_trace_geteventinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_geteventinfo
- fn_trace_geteventinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- events [SQL Server], status information
- fn_trace_geteventinfo function
- sys.fn_trace_geteventinfo function
- status information [SQL Server], events
ms.assetid: 5b1c858a-ca43-4e2b-9d67-8654daaf0cc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 62296eb8d1ef53969e33f3807bd81f47025a4893
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059278"
---
# <a name="sysfntracegeteventinfo-transact-sql"></a>sys.fn_trace_geteventinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einem Ereignis zurück, für das eine Ablaufverfolgung ausgeführt wird.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_trace_geteventinfo ( trace_id )  
```  
  
## <a name="arguments"></a>Argumente  
 *trace_id*  
 Die ID der Ablaufverfolgung. *Trace_id* ist **Int**, hat keinen Standardwert.  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Ereignis-ID**|**int**|ID des Ereignisses, dessen Ablauf verfolgt wird.|  
|**Spalten-ID**|**int**|Die ID-Nummern aller Spalten, die für jedes Ereignis gesammelt wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die ID einer bestimmten Ablaufverfolgung übergeben **Fn_trace_geteventinfo** gibt Informationen zu dieser Ablaufverfolgung zurück. Wird eine ungültige ID übergeben, gibt die Funktion ein leeres Rowset zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER TRACE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Informationen zur Ablaufverfolgung Nummer 2 zurück.  
  
```  
SELECT * FROM fn_trace_geteventinfo(2) ;  
GO  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)  
  
  
