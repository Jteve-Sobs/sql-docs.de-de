---
title: SQL:StmtRecompile (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL:StmtRecompile event class
ms.assetid: 3a134751-3e93-4fe8-bf22-1e0561189293
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f04e82e0111f91f419bc21dcdc75b3a157a21ccb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713949"
---
# <a name="sqlstmtrecompile-event-class"></a>SQL:StmtRecompile (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die SQL:StmtRecompile-Ereignisklasse zeigt Neukompilierungen auf Anweisungsebene an, die durch jegliche Arten von Batches, durch gespeicherte Prozeduren, durch Trigger, durch Ad-hoc-Batches sowie durch Abfragen verursacht wurden. Abfragen können über sp_executesql, dynamische SQL-Anweisungen, Prepare-Methoden, Execute-Methoden oder ähnliche Schnittstellen gesendet werden. Die SQL:StmtRecompile-Ereignisklasse sollte anstelle der SP:Recompile-Ereignisklasse verwendet werden.  
  
## <a name="sqlstmtrecompile-event-class-data-columns"></a>Datenspalten der SQL:StmtRecompile-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den von der Anwendung übergebenen Werten und nicht mit dem angezeigten Programmnamen aufgefüllt.|10|Benutzerkontensteuerung|  
|ClientProcessID|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Prozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|DatabaseID|**int**|ID der Datenbank, in der die gespeicherte Prozedur ausgeführt wird. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|**nvarchar**|Name der Datenbank, in der die gespeicherte Prozedur ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventSequence|**int**|Die Sequenz eines Ereignisses innerhalb der Anforderung.|51|nein|  
|EventSubClass|**int**|Beschreibt den Grund für die Neukompilierung:<br /><br /> 1 = Schema geändert<br /><br /> 2 = Statistiken geändert<br /><br /> 3 = Verzögertes Kompilieren<br /><br /> 4 = Festgelegte Option geändert<br /><br /> 5 = Temp. Tabelle geändert<br /><br /> 6 = Remoterowset geändert<br /><br /> 7 = For Browse-Berechtigungen geändert<br /><br /> 8 = Abfragebenachrichtigungsumgebung geändert<br /><br /> 9 = Partitionierte Sicht geändert<br /><br /> 10 = Cursoroptionen geändert<br /><br /> 11 = Option (Neukompilierung) angefordert|21|Benutzerkontensteuerung|  
|GroupID|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|**nvarchar**|Name des Computers, auf dem der Client ausgeführt wird, von dem diese Anweisung gesendet wurde. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IntegerData2|**int**|Endoffset der Anweisung innerhalb der gespeicherten Prozedur oder des Batches, die bzw. der die Neukompilierung verursacht hat. Der Endoffset ist -1, falls die Anweisung die letzte Anweisung im Batch ist.|55|Benutzerkontensteuerung|  
|IsSystem|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.<br /><br /> 1 = System<br /><br /> 0 = Benutzer|60|Benutzerkontensteuerung|  
|LineNumber|**int**|Folgenummer dieser Anweisung innerhalb dieses Batches, falls zutreffend.|5|Benutzerkontensteuerung|  
|LoginName|**nvarchar**|Anmeldename, die diesen Batch gesendet hat.|11|Benutzerkontensteuerung|  
|LoginSid|**image**|Sicherheits-ID (SID) des derzeit angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NestLevel|**int**|Die Schachtelungsebene des Aufrufs der gespeicherten Prozedur. Mit der gespeicherten my_proc_a-Prozedur wird beispielsweise my_proc_b aufgerufen. In diesem Fall weist my_proc_a eine NestLevel von 1 und my_proc_b eine NestLevel von 2 auf.|29|Benutzerkontensteuerung|  
|NTDomainName|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|**nvarchar**|Windows-Benutzername des verbundenen Benutzers.|6|Benutzerkontensteuerung|  
|ObjectID|**int**|Vom System zugewiesener Bezeichner des Objekts mit der Anweisung, die die Neukompilierung verursacht hat. Bei diesem Objekt kann es sich um eine gespeicherte Prozedur, einen Trigger oder eine benutzerdefinierte Funktion handeln. Bei Ad-hoc-Batches oder vorbereitetem SQL-Code geben ObjectID und ObjectName einen NULL-Wert zurück.|22|Benutzerkontensteuerung|  
|ObjectName|**nvarchar**|Name des von ObjectID identifizierten Objekts.|34|Benutzerkontensteuerung|  
|ObjectType|**int**|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Weitere Informationen finden Sie unter [ObjectType Trace Event Column](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Benutzerkontensteuerung|  
|Offset|**int**|Startoffset der Anweisung innerhalb der gespeicherten Prozedur oder des Batches, die bzw. der die Neukompilierung verursacht hat.|61|Benutzerkontensteuerung|  
|RequestID|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|**nvarchar**|Name des Computers mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für den die Ablaufverfolgung vorgenommen wird.|26|nein|  
|SessionLoginName|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|**int**|Serverprozess-ID der Verbindung.|12|Benutzerkontensteuerung|  
|SqlHandle|**varbinary**|64-Bit-Hash, der auf dem Text einer Ad-hoc-Abfrage oder der Datenbank- und Objekt-ID eines SQL-Objekts basiert. Dieser Wert kann an sys.dm_exec_sql_text übergeben werden, um den zugehörigen SQL-Text abzurufen.|63|nein|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|**ntext**|Der Text der Transact-SQL-Anweisung, die neu kompiliert wurde.|1|Benutzerkontensteuerung|  
|TransactionID|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|XactSequence|**bigint**|Das Token, das die aktuelle Transaktion beschreibt.|50|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SP:Recompile-Ereignisklasse](../../relational-databases/event-classes/sp-recompile-event-class.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
