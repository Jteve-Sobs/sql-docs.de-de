---
title: Wiedergeben von Ablaufverfolgungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69956f6a24ec6f373343cebb4e60fa4ad9fea320
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62740465"
---
# <a name="replay-traces"></a>Wiedergeben von Ablaufverfolgungen
  Bei der Wiedergabe handelt es sich um die Fähigkeit, Aktivitäten zu reproduzieren, die in einer Ablaufverfolgung aufgezeichnet wurden. Wenn Sie eine Ablaufverfolgung erstellen oder bearbeiten, können Sie sie in einer Datei speichern, um sie zu einem späteren Zeitpunkt wiederzugeben. Sie können mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Ablaufverfolgungsaktivitäten von einem einzelnen Computer wiedergeben. Verwenden Sie für große Arbeitsauslastungen das Distributed Replay Utility, um Ablaufverfolgungsdaten von mehreren Computern wiederzugeben.  
  
 In diesem Abschnitt wird die Verwendung der Wiedergabefunktionen von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]beschrieben. Weitere Informationen zum Distributed Replay Utility finden Sie unter [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verfügt über eine Multithread-Wiedergabe-Engine, die Benutzerverbindungen und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung simulieren kann. Die Wiedergabe ist nützlich für die Behandlung von Anwendungs- oder Prozessproblemen. Wenn Sie das Problem identifiziert und Korrekturen implementiert haben, sollten Sie die Ablaufverfolgung, in der das mögliche Problem aufgetreten ist, für die korrigierte Anwendung bzw. den korrigierten Prozess ausführen. Geben Sie anschließend die ursprüngliche Ablaufverfolgung wieder, und vergleichen Sie die Ergebnisse.  
  
 Bei der Wiedergabe von Ablaufverfolgungen wird das Debuggen mithilfe der Optionen **Breakpoint ein/aus** und **Ausführen bis Cursorposition** im Menü [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Wiedergeben** unterstützt. Diese Optionen verbessern vor allem die Analyse von langen Skripts, weil sie die Wiedergabe der Ablaufverfolgung in kleine Segmente unterteilen können, damit sie schrittweise analysiert werden können.  
  
 Informationen zu den Berechtigungen, die zum Wiedergeben einer Ablaufverfolgung erforderlich sind, finden Sie unter [Erforderliche Berechtigungen zum Ausführen von SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Anforderungen für die Wiedergabe](replay-requirements.md)|Beschreibt die Ereignisse, die in einer Ablaufverfolgungsdefinition vorhanden sein müssen, damit die Ablaufverfolgung mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]wiedergegeben werden kann.|  
|[Wiedergabeoptionen &#40;SQL Server Profiler&#41;](replay-options-sql-server-profiler.md)|Beschreibt die Optionen, die Sie im Dialogfeld **Wiedergabekonfiguration** von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]festlegen können.|  
|[Überlegungen zum Wiedergeben von Ablaufverfolgungen &#40;SQL Server Profiler&#41;](considerations-for-replaying-traces-sql-server-profiler.md)|Beschreibt Ablaufverfolgungsereignisse, die nicht mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] wiedergegeben werden können, und die Auswirkungen der Wiedergabe von Ablaufverfolgungen auf die Serverleistung.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)  
  
  
