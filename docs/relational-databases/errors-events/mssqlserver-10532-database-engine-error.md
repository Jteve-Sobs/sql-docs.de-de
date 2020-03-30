---
title: MSSQLSERVER_10532 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 050f1c4e1c47458e513e02d16eb3ea6dc7e842a8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72005986"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10532|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste '%.\*ls' kann nicht erstellt werden, weil der mit **\@plan_handle** angegebene Batch bzw. das Modul keine geeignete Anweisung für eine Planhinweisliste enthält. Geben Sie einen anderen Wert für **\@plan_handle** an.|  
  
## <a name="explanation"></a>Erklärung  
Der mit **\@plan_handle** angegebene Batch bzw. das Modul enthält keine geeignete Anweisung für eine Planhinweisliste.  
  
## <a name="user-action"></a>Benutzeraktion  
Geben Sie einen anderen Wert für **\@plan_handle** an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Planhinweislisten](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
