---
title: MSSQLSERVER_10539 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8334c28865c01c63ae6bcb18c79d4fd88b715175
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68060597"
---
# <a name="mssqlserver_10539"></a>MSSQLSERVER_10539
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10539|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_PLAN_FOR_STMT|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht aus dem Cache erstellt werden, weil kein Abfrageplan für die Anweisung mit dem Startoffset %d verfügbar ist. Dieses Problem kann auftreten, wenn die Anweisung von Datenbankobjekten abhängig ist, die noch nicht erstellt wurden. Stellen Sie sicher, dass alle erforderlichen Datenbankobjekte vorhanden sind, und führen Sie die Anweisung vor dem Erstellen der Planhinweisliste aus.|  
  
## <a name="explanation"></a>Erklärung  
Im Plancache ist kein Abfrageplan für die Anweisung mit dem angegebenen Startoffset vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass alle erforderlichen Datenbankobjekte vorhanden sind, und führen Sie die Anweisung vor dem Erstellen der Planhinweisliste aus.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
