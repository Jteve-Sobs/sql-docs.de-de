---
title: Befehlszeilenoptionen für das Verwaltungstool (Distributed Replay-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f53c456832e89aa96c0f7c9a1decd9fabbe96360
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815962"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Befehlszeilenoptionen für das Verwaltungstool (Distributed Replay Utility)
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Verwaltungstool, `DReplay.exe`, ist ein Befehlszeilentool, das Sie für die Kommunikation mit distributed Replay Controller verwenden können. Mit dem Verwaltungstool können Sie Vorgänge auf dem Controller initiieren, überwachen und abbrechen.  
  
 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Topic link icon") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a>Hinweise  
 Sie können mit `DReplay.exe` die folgenden Befehlszeilenoptionen ausgeben:  
  
 **preprocess**  
 Initiiert die Vorverarbeitungsphase. Der Controller bereitet die Eingabedaten der Ablaufverfolgung, die Sie aus der Produktionsumgebung aufgezeichnet haben, für die Wiedergabe anhand des Zielservers vor.  
  
 **Wiedergabe (replay)**  
 Initiiert die Ereigniswiedergabephase. Der Controller leitet Wiedergabedaten an die angegebenen Clients weiter, startet die verteilte Wiedergabe und synchronisiert die Clients. Optional zeichnet jeder ausgewählte Client die Wiedergabeaktivität auf und speichert Ergebnisdateien der Ablaufverfolgung lokal.  
  
 **status**  
 Fragt den Controller ab und zeigt den aktuellen Status an.  
  
 **cancel**  
 Bricht den Vorgang ab, der derzeit auf dem Controller ausgeführt wird.  
  
 Ausführliche Informationen zur Syntax, einschließlich Befehlsargumenten und Beispielen, finden Sie in den folgenden Themen:  
  
-   [Vorverarbeitungsoption &#40;Verwaltungstool „Distributed Replay“&#41;](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Wiedergabeoption &#40;Verwaltungstool „Distributed Replay“&#41;](replay-option-distributed-replay-administration-tool.md)  
  
-   [Statusoption &#40;Verwaltungstool „Distributed Replay“&#41;](status-option-distributed-replay-administration-tool.md)  
  
-   [Option zum Abbrechen &#40;Verwaltungstool „Distributed Replay“&#41;](cancel-option-distributed-replay-administration-tool.md)  
  
 RPCs werden als RPCs wiedergegeben und nicht als Sprachereignisse.  
  
## <a name="permissions"></a>Berechtigungen  
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
