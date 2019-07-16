---
title: Sys. fn_trace_getinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 041f651fb34c486cebc589f119f3e5f220314dd2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059233"
---
# <a name="sysfntracegetinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einer angegebene Ablaufverfolgung oder zu alle vorhandenen Ablaufverfolgungen zurück.  
  
> **WICHTIG!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.    
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>Argumente  
 *trace_id*  
 Die ID der Ablaufverfolgung. *Trace_id* ist **Int**.  Gültige Eingaben sind die ID einer Ablaufverfolgung, NULL, 0 oder DEFAULT. NULL, 0 und DEFAULT sind in diesem Kontext gleichwertig. Geben Sie NULL, 0 oder DEFAULT an, wenn Informationen zu allen Ablaufverfolgungen in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben werden sollen.  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|traceid|**int**|ID der Ablaufverfolgung.|  
|property|**int**|Eigenschaft der Ablaufverfolgung:<br /><br /> 1= Ablaufverfolgungsoptionen. Weitere Informationen finden Sie unter @options in [Sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 = Dateiname<br /><br /> 3 = Maximale Größe<br /><br /> 4 = Beendigungszeit<br /><br /> 5 = Aktueller Status der Ablaufverfolgung 0 = beendet. 1 = aktiv|  
|Wert|**sql_variant**|Informationen zur Eigenschaft der angegebenen Ablaufverfolgung.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die ID einer bestimmten Ablaufverfolgung übergeben, gibt Fn_trace_getinfo Informationen zu dieser Ablaufverfolgung zurück. Wird eine ungültige ID übergeben, gibt die Funktion ein leeres Rowset zurück.  
  
 Fn_trace_getinfo Fügt eine TRC-Erweiterung auf den Namen jeder Ablaufverfolgungsdatei, die im Resultset enthalten. Informationen zum Definieren einer Ablaufverfolgung finden Sie unter [Sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). Ähnliche Informationen zu Ablaufverfolgungsfiltern finden Sie [Sys. fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 Ein vollständiges Beispiel der Verwendung der Ablaufverfolgung, die gespeicherten Prozeduren finden Sie unter [erstellen Sie eine Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER TRACE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Informationen zu allen aktiven Ablaufverfolgungen zurück.  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
