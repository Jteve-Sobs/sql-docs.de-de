---
title: Background Job Error-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5689c86e530fd7bf7f78cb58f3e1e53f9b731bc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690628"
---
# <a name="background-job-error-event-class"></a>Background Job Error-Ereignisklasse
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **Background Job Error** -Ereignisklasse tritt auf, wenn ein Hintergrundauftrag fehlerbedingt beendet wurde. Dieser Zustand erfordert möglicherweise ein Eingreifen des Systemadministrators.  
  
## <a name="background-job-error-event-class-data-columns"></a>Datenspalten der Background Job Error-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID der durch den Auftrag angegebenen Datenbank. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|**Fehler**|**int**|Fehlernummer des letzten Versuchs (nur bei**EventSubClass** 1).|31|Benutzerkontensteuerung|  
|**EventClass**|**int**|Ereignistyp = 193.|27|nein|  
|**EventSequence**|**int**|Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Hintergrundauftrag nach Fehler vorzeitig beendet.<br /><br /> 2 = Hintergrundauftrag gelöscht - Warteschlange voll.<br /><br /> 3 = Hintergrundauftrag hat einen Fehler zurückgegeben.|21|Benutzerkontensteuerung|  
|**IndexID**|**int**|ID für den Index des Objekts, das von dem Ereignis betroffen ist. Sie können die Index-ID für ein Objekt mithilfe der **indid** -Spalte der **sysindexes** -Systemtabelle ermitteln.|24|Benutzerkontensteuerung|  
|**IntegerData**|**int**|Anzahl der Versuche des Auftrags (nur bei**EventSubClass** 1).|25|Benutzerkontensteuerung|  
|**IntegerData2**|**int**|Auftragssequenznummer.|55|Benutzerkontensteuerung|  
|**ObjectID**|**int**|Vom System zugewiesene ID des Objekts.|22|Benutzerkontensteuerung|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt die Windows-Anmeldenamen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] an.|64|Benutzerkontensteuerung|  
|**Severity**|**int**|Der Schweregrad des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).|20|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem der Auftrag erstellt wurde.|14|Benutzerkontensteuerung|  
|**Status**|**int**|Der Status des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).|30|Benutzerkontensteuerung|  
|**TextData**|**ntext**|Die Textbeschreibung des Wertes der Ereignisunterklasse.|1|Benutzerkontensteuerung|  
|**Typ**|**int**|Typ des Auftrags.|57|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Auto Stats-Ereignisklasse](../../relational-databases/event-classes/auto-stats-event-class.md)  
  
  
