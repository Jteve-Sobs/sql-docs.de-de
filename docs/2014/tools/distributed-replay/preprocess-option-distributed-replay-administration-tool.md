---
title: Option „preprocess“ (Distributed Replay-Verwaltungstool) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f5f4492dc18a93ab1fea9d34287eb90703bc3d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149904"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a>Vorverarbeitungsoption (Verwaltungstool "Distributed Replay")
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Verwaltungstool, `DReplay.exe`, ist ein Befehlszeilentool, das Sie für die Kommunikation mit distributed Replay Controller verwenden können. In diesem Thema werden die Befehlszeilenoption **preprocess** und die entsprechende Syntax beschrieben.  
  
 Die **preprocess** -Option initiiert die Vorverarbeitungsphase. In dieser Phase bereitet der Controller die Eingabedaten der Ablaufverfolgung für die Wiedergabe anhand des Zielservers vor.  
  
 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Topic link icon") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
```  
  
#### <a name="parameters"></a>Parameter  
 **-m** *Controller*  
 Gibt den Computernamen des Controllers an. Sie können mit "`localhost`" oder "`.`" auf den lokalen Computer verweisen.  
  
 Wenn der **-m** -Parameter nicht angegeben ist, wird der lokale Computer verwendet.  
  
 **-i** *input_trace_file*  
 Gibt den vollständigen Pfad der Eingabedatei der Ablaufverfolgung auf dem Controller an, z. B. `D:\Mytrace.trc`. Der **-i** -Parameter ist erforderlich.  
  
 Wenn Rolloverdateien im gleichen Verzeichnis vorhanden sind, werden sie geladen und automatisch verwendet. Die Dateien müssen der Dateirollover-Benennungskonvention folgen, z.B.: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.  
  
> [!NOTE]  
>  Wenn Sie das Verwaltungstool auf einem anderen Computer als dem Controller verwenden, müssen Sie die Eingabedateien der Ablaufverfolgung auf den Controller kopieren, damit ein lokaler Pfad für diesen Parameter verwendet werden kann.  
  
 **-d** *controller_working_dir*  
 Gibt das Verzeichnis auf dem Controller an, in dem die Zwischendatei gespeichert wird. Der **-d** -Parameter ist erforderlich.  
  
 Es gelten die folgenden Anforderungen:  
  
-   Das Verzeichnis muss sich auf dem Controller befinden.  
  
-   Sie müssen den vollständigen Pfad angeben, der mit einem Laufwerkbuchstaben beginnen muss (z. B. `c:\WorkingDir`).  
  
-   Der Pfad darf nicht mit einem umgekehrten Schrägstrich ("`\`") enden.  
  
-   UNC-Pfade werden nicht unterstützt.  
  
 **-c** *config_file*  
 Der vollständige Pfad der Vorverarbeitungskonfigurationsdatei. Mit ihm wird der Speicherort der Vorverarbeitungskonfigurationsdatei angegeben, wenn sie an einem anderen Speicherort gespeichert wird. Dieser Parameter kann ein UNC-Pfad sein oder ein lokales Verzeichnis auf dem Computer angeben, auf dem Sie das Verwaltungstool ausführen.  
  
 Der **-c** -Parameter ist nicht erforderlich, wenn keine Filterung benötigt wird oder wenn Sie die maximale Leerlaufzeit nicht ändern möchten.  
  
 Ohne den **-c** -Parameter wird die Standardkonfigurationsdatei für die Vorverarbeitung verwendet: `DReplay.exe.preprocess.config`.  
  
 **-f** *Statusintervall*  
 Gibt die Häufigkeit (in Sekunden) für die Anzeige von Statusmeldungen an.  
  
 Wenn **-f** nicht angegeben wird, beträgt das Standardintervall 30 Sekunden.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Vorverarbeitungsphase mit allen Standardeinstellungen initiiert. Der Wert `localhost` gibt an, dass der Controllerdienst auf demselben Computer wie das Verwaltungstool ausgeführt wird. Der *input_trace_file* -Parameter gibt den Speicherort der Eingabedaten der Ablaufverfolgung an: `c:\mytrace.trc`. Da keine Filterung der Ablaufverfolgungsdatei erfolgt, muss der **-c** -Parameter angegeben werden.  
  
```  
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir  
```  
  
 In diesem Beispiel wird die Vorverarbeitungsphase initiiert, und es wird eine geänderte Vorverarbeitungskonfigurationsdatei angegeben. Im Gegensatz zum vorherigen Beispiel wird der **-c** -Parameter verwendet, um auf die geänderte Konfigurationsdatei zu zeigen, wenn Sie diese an einem anderen Speicherort gespeichert haben. Zum Beispiel:  
  
```  
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config  
```  
  
 Der geänderten Vorverarbeitungskonfigurationsdatei wird eine Filterbedingung hinzugefügt, die während der verteilten Wiedergabe Systemsitzungen herausfiltert. Der Filter wird durch Ändern des `<PreprocessModifiers>` -Elements in der Vorverarbeitungskonfigurationsdatei `DReplay.exe.preprocess.config`hinzugefügt.  
  
 Im folgenden Beispiel wird die geänderte Konfigurationsdatei gezeigt:  
  
```  
<?xml version='1.0'?>  
<Options>  
    <PreprocessModifiers>  
        <IncSystemSession>No</IncSystemSession>  
        <MaxIdleTime>-1</MaxIdleTime>  
    </PreprocessModifiers>  
</Options>  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorbereiten der Eingabedaten für die Ablaufverfolgung](prepare-the-input-trace-data.md)   
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)   
 [Konfigurieren von Distributed Replay](configure-distributed-replay.md)  
  
  
