---
title: Ziel des ringpufferziels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d042ef49a82d16eb33cb27d80c8083a68ea69092
ms.sourcegitcommit: 4b5ea5fa3253fea028e1adbd46bd18b89f0a115b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905655"
---
# <a name="ring-buffer-target"></a>Ringpufferziel
  Das Ringpufferziel speichert kurzzeitig Ereignisdaten im Arbeitsspeicher. Dieses Ziel kann Ereignisse in einem von zwei Modi verwalten.  
  
-   Bei dem ersten Modus handelt es sich um eine strikte FIFO-Reihenfolge (First-In-First-Out), bei der das älteste Ereignis verworfen wird, wenn der gesamte dem Ziel zugeordnete Arbeitsspeicher verwendet wurde. In diesem Modus (dem Standardmodus) wird die Option "occurrence_number" auf 0 festgelegt.  
  
-   Der zweite Modus ist eine FIFO-Reihenfolge pro Ereignis, bei der eine festgelegte Anzahl von Ereignissen jedes Typs aufbewahrt wird. In diesem Modus werden die ältesten Ereignisse der einzelnen Typen verworfen, wenn der gesamte dem Ziel zugeordnete Arbeitsspeicher verwendet wird. Sie können die Option "occurrence_number" so konfigurieren, dass die Anzahl der für jeden Typ beizubehaltenden Ereignisse angegeben wird.  
  
 In der folgenden Tabelle werden die verfügbaren Optionen für das Konfigurieren des Ringpufferziels beschrieben.  
  
|Option|Zulässige Werte|Description|  
|------------|--------------------|-----------------|  
|max_memory|Eine beliebige 32-Bit-Ganzzahl. Dieser Wert ist optional.|Die Höchstmenge des verfügbaren Arbeitsspeichers in Kilobyte (KB). Vorhandene Ereignisse werden auf Grundlage der Grenze gelöscht, die zuerst erreicht wird: max_event_limit oder max_memory. Der maximale Wert ist 4194303 KB. Ein sorgfältiger Überlegung sollten vorgenommen werden, bevor Sie die Größe des Puffers Ring Grenzwerte im Bereich GB festlegen, wie es anderen speicherverbrauchern im SQL Server auswirken können|  
|max_event_limit|Eine beliebige 32-Bit-Ganzzahl. Dieser Wert ist optional.|Die maximale Anzahl von Ereignissen, die in ring_buffer behalten wurden. Vorhandene Ereignisse werden auf Grundlage der Grenze gelöscht, die zuerst erreicht wird: max_event_limit oder max_memory. Standardeinstellung = 1000.|  
|occurrence_number|Einer der folgenden Werte:<br /><br /> 0 (Standard) = Das älteste Ereignis wird verworfen, wenn der gesamte dem Ziel zugeordnete Arbeitsspeicher verwendet wurde.<br /><br /> Alle 32-Bit-Ganzzahl = die Anzahl von Ereignissen jedes Typs beibehalten werden, bevor Sie eine FIFO-Reihenfolge pro Ereignis verworfen werden.<br /><br /> <br /><br /> Dieser Wert ist optional.|Der zu verwendende FIFO-Modus. Wenn dieser auf einen Wert größer als 0 festgelegt ist, die gewünschte Anzahl von Ereignissen, die für jeden Typ im Puffer gespeichert werden sollen.|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a>Hinzufügen des Ziels zu einer Sitzung  
 Wenn Sie das Ringpufferziel einer Sitzung für erweiterte Ereignisse hinzufügen möchten, müssen Sie beim Erstellen oder Ändern einer Ereignissitzung die folgende Anweisung einschließen:  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a>Überprüfen der Zielausgabe  
 Sie können die Ausgabe des Ringpufferziels mithilfe der folgenden Abfrage überprüfen und dabei *session_name* durch den Namen der Ereignissitzung ersetzen.  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 Im folgenden Beispiel wird das Ausgabeformat des Ringpufferziels veranschaulicht.  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a>Siehe auch

- [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION &#40;Transact-SQL&#41;](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

