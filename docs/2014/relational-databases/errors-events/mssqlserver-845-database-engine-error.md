---
title: MSSQLSERVER_845 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d98be02727582d4f9201ec7f47c3cdb8db5a56b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761928"
---
# <a name="mssqlserver845"></a>MSSQLSERVER_845
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|845|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BUFLATCH_TIMEOUT|  
|Meldungstext|Timeout beim Warten auf Pufferlatchtyp %d für Seite %S_PGID, Datenbank-ID %d.|  
  
## <a name="explanation"></a>Erklärung  
Ein Prozess hat darauf gewartet, einen Latch abzurufen, doch der Prozess hat so lange gewartet, bis die Zeitgrenze überschritten wurde und kein Latch abgerufen werden konnte. Dies kann auftreten, wenn das Ausführen eines E/A-Vorgangs zu lange dauert, was normalerweise daraus resultiert, dass Systemprozesse durch andere Tasks blockiert werden. In manchen Fällen kann dieser Fehler auch das Ergebnis eines Hardwarefehlers sein.  
  
## <a name="user-action"></a>Benutzeraktion  
Durch folgende Aktionen kann dieser Fehler verhindert werden:  
  
-   Reduzieren Sie die Arbeitsauslastung.  
  
-   Überprüfen Sie, ob zugehörige E/A-Fehler im Fehlerprotokoll oder Ereignisprotokoll vorhanden sind. E/A-Fehler werden typischerweise durch Datenträgerfehler verursacht.  
  
-   Überprüfen Sie das Fehlerprotokoll auf Tasks, die kein Ergebnis bereitstellen, sowie auf andere kritische Fehler.  
  
-   Wenn kritische Fehler, z. B. Assert-Vorgänge, häufig auftreten, beheben Sie diese Probleme.  
  
Wenn der Fehler wiederholt auftritt, wenden Sie sich an den Microsoft-Kundendienst und -Support.  
  
