---
title: Wiedergabe bis zu einer Cursorposition (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7c4c4b9d2e2e07c53f850fe545d803fa411dbbc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795822"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>Wiedergeben bis zu einer Cursorposition (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Ablaufverfolgungsdateien oder -tabellen mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]so wiedergegeben werden können, dass sie anhalten, wenn sie eine Cursorposition erreichen. Durch das Anhalten von Ablaufverfolgungen an Cursorpositionen wird das Debugging erleichtert, da lange Ablaufverfolgungsskripts in kürzere Segmente unterteilt und inkrementell analysiert werden können.  
  
### <a name="to-replay-to-the-cursor"></a>So geben Sie bis zur Cursorposition wieder  
  
1.  Öffnen Sie die Ablaufverfolgungsdatei oder -tabelle, die Sie wiedergeben möchten. Weitere Informationen finden Sie unter [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) oder den Optimierungsratgeber von [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)die richtigen Ereignisse und Spalten aufgezeichnet werden.  
  
     Stellen Sie sicher, dass die geöffnete Ablaufverfolgungsdatei oder -tabelle die Ereignisklassen enthält, die für die Wiedergabe erforderlich sind. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
2.  Klicken Sie im Ablaufverfolgungsfenster auf ein Ereignis.  
  
3.  Klicken Sie im Menü **Wiedergeben** auf **Ausführen bis Cursorposition**, und stellen Sie eine Verbindung zu dem Server her, auf dem Sie die Ablaufverfolgung wiedergeben möchten.  
  
4.  Überprüfen Sie im Dialogfeld **Wiedergabekonfiguration** die Einstellungen, und klicken Sie dann auf **OK**.  
  
     Die Wiedergabe beginnt; sie hält an, wenn sie die erste Cursorposition erreicht.  
  
5.  Drücken Sie F5, um die Ablaufverfolgung fortzusetzen.  
  
6.  Wiederholen Sie Schritt 5 bis zum Ende der Ablaufverfolgung.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiedergeben bis zu einem Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
