---
title: MSSQL_ENG014005 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1953a30920c8a1000bd1d3c0e6cefcb8b5ac594e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010973"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14005|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Veröffentlichung konnte nicht gelöscht werden. Es besteht ein Abonnement für sie.|  
  
## <a name="explanation"></a>Erklärung  
 Sie haben versucht, eine Veröffentlichung zu löschen, der ein oder mehrere Abonnements zugeordnet sind. Eine Veröffentlichung kann aber nur gelöscht werden, wenn ihr keine Abonnements zugeordnet sind.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie erst die Abonnements, bevor Sie die Veröffentlichung löschen. Wenn Sie zum Löschen der Veröffentlichung [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, haben Sie die Möglichkeit, vor dem Löschen der Veröffentlichung automatisch alle zugeordneten Abonnements löschen zu lassen. Wenn Sie zum Löschen der Veröffentlichung gespeicherte Prozeduren verwenden, müssen Sie die Abonnements zuerst explizit löschen. Weitere Informationen finden Sie unter [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) und [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Wenn für die Veröffentlichung keine Abonnements vorhanden zu sein scheinen oder wenn dieser Fehler beim Erstellen einer Veröffentlichung angezeigt wird, könnte noch ein vorheriges Abonnement vorhanden sein, das nicht vollständig leer war, bevor versucht wurde, es zu entfernen. Führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) in der Datenbank aus, um alle mit der Replikation zusammenhängenden Objekte und Einstellungen zu entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
