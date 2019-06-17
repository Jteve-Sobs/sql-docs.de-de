---
title: MSSQLSERVER_5235 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d6cbfac91613c2374e42da5b33e75ed5cade2bcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62913757"
---
# <a name="mssqlserver5235"></a>MSSQLSERVER_5235
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5235|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|Meldungstext|[EMERGENCY] DBCC DBCC_COMMAND_DETAILS wurde von USER_NAME ausgeführt, wurde jedoch fehlerbedingt mit dem Fehlerzustand ERROR_STATE beendet. Verstrichene Zeit: Stunden, MINUTES Minuten, SECONDS Sekunden.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist die Zusammenfassungsmeldung, die von DBCC an das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll ausgegeben wird, wenn während der Ausführung des Befehls eine unerwartete Beendigung auftritt. Mit dem Fehlerzustand, der in der Meldung angegeben wird, wird der Typ der unerwarteten Beendigung definiert.  
  
 In der folgenden Tabelle werden die Fehlerzustände aufgeführt und definiert.  
  
|Fehlerzustand|Definition|  
|-----------------|----------------|  
|Status 0|Die Anweisung wurde aufgrund einer schwerwiegenden Beschädigung der Metadaten beendet. Diese Meldung wird von mindestens einer Instanz des Fehlers 8930 begleitet.|  
|Status 1|Die Anweisung wurde aufgrund eines internen Überprüfungsfehlers beendet. Diese Meldung wird von mindestens einer Instanz des Fehlers 8967 begleitet.|  
|Status 2|Bei den grundlegenden Systemtabellenüberprüfungen der zentralen Speicher-Engine-Systemtabellen ist ein Fehler aufgetreten. Diese Meldung wird von mindestens einer Instanz des Fehlers [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md), oder [7988](mssqlserver-7988-database-engine-error.md) begleitet.|  
|Status 3|Bei der DBCC-Reparatur im Notfallmodus ist ein Fehler aufgetreten, da die Datenbank nach der erneuten Erstellung des Transaktionsprotokolls nicht gestartet werden konnte. Diese Meldung wird von Fehler 7909 begleitet.|  
|Status 4|Während der Ausführung des Befehls ist ein Fehler bei der Assertion oder eine Zugriffsverletzung aufgetreten.|  
|Status 5|Ein unbekannter Fehler ist aufgetreten, durch den der DBCC-Befehl unerwartet beendet wurde.|  
  
## <a name="user-action"></a>Benutzeraktion  
 In der folgenden Tabelle wird die Benutzeraktion angegeben, die für den angegebenen Fehlerzustand angemessen ist.  
  
|Fehlerzustand|Benutzeraktion|  
|-----------------|-----------------|  
|Status 0|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 1|Wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|Status 2|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 3|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 4|Wenden Sie sich an den Kundenservice und -support.|  
|Status 5|Führen Sie den Befehl erneut aus. Wenden Sie sich an den Kundenservice und -support, wenn das Problem weiterhin auftritt.|  
  
## <a name="see-also"></a>Siehe auch  
 [DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
