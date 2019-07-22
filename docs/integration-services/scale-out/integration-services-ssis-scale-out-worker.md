---
title: SSIS Scale Out-Worker (SQL Server Integration Services) | Microsoft-Dokumentation
description: In diesem Artikel wird die Scale Out-Masterkomponente von SSIS Scale Out beschrieben.
ms.custom: performance
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: 1f2be60ff216b65afbb50c0e97da4edfb4239aec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082072"
---
# <a name="integration-services-ssis-scale-out-worker"></a>Worker für horizontales Hochskalieren von Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Der Scale Out-Worker führt den Scale Out-Workerdienst aus, um Ausführungsaufgaben aus dem Scale Out-Master zu entfernen. Daraufhin führt der Worker die Pakete lokal mit `ISServerExec.exe` aus.

## <a name="configure-the-scale-out-worker-service"></a>Konfigurieren des Scale Out-Workerdiensts
Sie können den Scale Out-Workerdienst mithilfe der `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config`-Datei konfigurieren. Der Dienst muss nach dem Aktualisieren der Konfigurationsdatei neu gestartet werden.

|Konfiguration  |und Beschreibung  |Standardwert|
|---------|---------|---------|
|DisplayName|Der Anzeigename des Workers für horizontales Hochskalieren. **Wird NICHT in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 verwendet.**|Computername|
|und Beschreibung|Die Beschreibung des Workers für horizontales Hochskalieren. **Wird NICHT in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 verwendet.**|Empty|
|MasterEndpoint|Der Endpunkt zum Herstellen einer Verbindung mit Master für horizontales Hochskalieren|Der Endpunkt, der während der Installation des Workers für horizontales Hochskalieren festgelegt wurde|
|MasterHttpsCertThumbprint|Der Fingerabdruck des Client-SSL-Zertifikats, mit dem Master für horizontales Hochskalieren authentifiziert wird|Der Fingerabdruck des Clientzertifikats, das bei der Installation von Worker für horizontales Hochskalieren angegeben wurde|
|WorkerHttpsCertThumbprint|Der Fingerabdruck des Zertifikats, das für den Master für horizontales Hochskalieren verwendet wird, um den Worker für horizontales Hochskalieren zu authentifizieren|Der Fingerabdruck eines Zertifikats, das bei der Installation von Worker für horizontales Hochskalieren automatisch erstellt und installiert wurde|
|StoreLocation|Der Speicherort des Workerzertifikats|LocalMachine|
|StoreName|Der Name des Speichers, in dem sich das Workerzertifikat befindet|My|
|AgentHeartbeatInterval|Das Zeitintervall für den Takt für Worker für horizontales Hochskalieren|00:01:00|
|TaskHeartbeatInterval|Das Zeitintervall für den Status des Berichtstasks für Worker für horizontales Hochskalieren|00:00:10|
|HeartbeatErrorTolerance|Nach diesem Zeitraum ab dem letzten erfolgreichen Tasktakt wird der Task beendet, wenn eine Fehlerantwort des Takts empfangen wird.|00:10:00|
|TaskRequestMaxCPU|Die Obergrenze bezüglich CPU für Worker für horizontales Hochskalieren, um Tasks anzufordern.|70.0|
|TaskRequestMinMemory|Die Mindestmenge von Arbeitsspeicher in MB für Worker für horizontales Hochskalieren, um Tasks anzufordern.|100.0|
|MaxTaskCount|Die maximale Anzahl von Tasks, die der Worker für horizontales Hochskalieren aufnehmen kann|10|
|LeaseInterval|Das Leaseintervall einer Taskaufbewahrung durch den Worker für horizontales Hochskalieren|00:01:00|
|TasksRootFolder|Der Ordner für die Taskprotokolle. Wenn der Wert leer ist, wird der Ordnerpfad `\<drive\>:\Users\[account]\AppData\Local\SSIS\Cluster\Tasks` verwendet. [Konto] ist das Konto, unter dem der Dienst für Worker für horizontales Hochskalieren ausgeführt wird. Standardmäßig ist dies das Konto SSISScaleOutWorker140.|Empty|
|TaskLogLevel|Die Taskprotokollebene für den Worker für horizontales Hochskalieren. (Ausführlich 0x01, Informationen 0x02, Warnung 0x04, Fehler 0x08, Status 0x10, schwerwiegender Fehler 0x20, Überwachung 0x40)|126 (Informationen, Warnung, Fehler, Status, schwerwiegender Fehler, Überwachung)|
|TaskLogSegment|Die Zeitspanne einer Taskprotokolldatei|00:00:00|
|TaskLogEnabled|Gibt an, ob das Taskprotokoll aktiviert ist.|true|
|ExecutionLogCacheFolder|Der Ordner, in dem das Paketausführungsprotokoll zwischengespeichert wird. Wenn der Wert leer ist, wird der Ordnerpfad `\<drive\>:\Users\[account]\AppData\Local\SSIS\Cluster\Agent\ELogCache` verwendet. [Konto] ist das Konto, unter dem der Dienst für Worker für horizontales Hochskalieren ausgeführt wird. Standardmäßig ist dies das Konto SSISScaleOutWorker140.|Empty|
|ExecutionLogMaxBufferLogCount|Die maximale Anzahl von Ausführungsprotokollen, die in einem Ausführungsprotokollpuffer im Arbeitsspeicher zwischengespeichert werden|10000|
|ExecutionLogMaxInMemoryBufferCount|Die maximale Anzahl von Ausführungsprotokollpuffern im Arbeitsspeicher für Ausführungsprotokolle|10|
|ExecutionLogRetryCount|Die Anzahl von Wiederholungsversuchen, wenn bei der Ausführungsprotokollierung ein Fehler auftritt|3|
|ExecutionLogRetryTimeout|Die Anzahl von Wiederholungsversuchen, wenn bei der Ausführungsprotokollierung ein Fehler auftritt. i\ Wenn ExecutionLogRetryCount erreicht wird, wird ExecutionLogRetryTimeout ignoriert. |7.00:00:00 (7 Tage)|
|AgentId|Worker-Agent-ID des Scale Out-Workers|Wird automatisch generiert|
||||    

## <a name="view-the-scale-out-worker-log"></a>Anzeigen des Protokolls des Scale Out-Workers
Die Protokolldatei des Scale Out-Workerdiensts befindet sich im Ordner `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Agent`.

Der Speicherort jeder einzelnen Aufgabe wird in der `WorkerSettings.config`-Datei im Ordner `TasksRootFolder` konfiguriert. Wenn kein Wert angegeben ist, befindet sich das Protokoll im Ordner `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Tasks`. 

Bei dem Parameter *[Konto]* handelt es sich um das Konto, unter dem der Scale Out-Workerdienst ausgeführt wird. Standardmäßig lautet das Konto `SSISScaleOutWorker140`.

## <a name="next-steps"></a>Nächste Schritte
[Scale Out-Master von Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
