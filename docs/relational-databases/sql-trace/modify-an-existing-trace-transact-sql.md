---
title: Ändern einer vorhandenen Ablaufverfolgung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69419019aa70731ebba6608d18af8d2d1db56d60
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215320"
---
# <a name="modify-an-existing-trace-transact-sql"></a>Ändern einer vorhandenen Ablaufverfolgung (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie gespeicherte Prozeduren verwendet werden können, um eine vorhandene Ablaufverfolgung zu ändern.  
  
### <a name="to-modify-an-existing-trace"></a>So ändern Sie eine vorhandene Ablaufverfolgung  
  
1.  Wenn die Ablaufverfolgung bereits ausgeführt wird, führen Sie **sp_trace_setstatus** aus, indem Sie mit **@status= 0** angeben, um die Ablaufverfolgung zu beenden.  
  
2.  Um Ablaufverfolgungsereignisse zu ändern, führen Sie **sp_trace_setevent** aus, wobei Sie die Änderungen über die Parameter angeben. Der Reihenfolge nach sortiert stehen die folgenden Parameter zur Verfügung:  
  
    -   **@traceid** (Ablaufverfolgungs-ID)  
  
    -   **@eventid** (Ereignis-ID)  
  
    -   **@columnid** (Spalten-ID)  
  
    -   **@on** (ON)  
  
     Beim Ändern des **@on** -Parameters sollten Sie dessen Interaktion mit dem **@columnid** -Parameter beachten:  
  
    |ON|Column ID|Ergebnis|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|Das Ereignis ist aktiviert. Alle Spalten werden gelöscht.|  
    ||NOT NULL|Die Spalte ist für das angegebene Ereignis aktiviert.|  
    |OFF (**0**)|NULL|Das Ereignis ist deaktiviert. Alle Spalten werden gelöscht.|  
    ||NOT NULL|Die Spalte ist für das angegebene Ereignis deaktiviert.|  
  
> [!IMPORTANT]
>  Im Gegensatz zu regulären gespeicherten Prozeduren werden die Parameter aller gespeicherten Prozeduren von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_* xx***) streng typisiert, und für sie wird keine automatische Datentypkonvertierung unterstützt. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
