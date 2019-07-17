---
title: dm_os_memory_cache_clock_hands (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 783f985810b44673c6a6566caa6e89ff655670e0
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265791"
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Status der Zeiger für eine bestimmte Cacheclock zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Adresse des Caches, der der Clock zugeordnet ist. Lässt keine NULL-Werte zu.|  
|**name**|**nvarchar(256)**|Name des Caches. Lässt keine NULL-Werte zu.|  
|**type**|**nvarchar(60)**|Typ des Cachespeichers. Es können mehrere Caches desselben Typs vorhanden sein. Lässt keine NULL-Werte zu.|  
|**clock_hand**|**nvarchar(60)**|Zeigertyp. Folgende Werte sind möglich:<br /><br /> Extern<br /><br /> Intern<br /><br /> Lässt keine NULL-Werte zu.|  
|**clock_status**|**nvarchar(60)**|Clockstatus. Folgende Werte sind möglich:<br /><br /> Angehalten<br /><br /> Wird ausgeführt<br /><br /> Lässt keine NULL-Werte zu.|  
|**rounds_count**|**bigint**|Anzahl der Sweeps innerhalb des Caches zum Entfernen von Einträgen. Lässt keine NULL-Werte zu.|  
|**removed_all_rounds_count**|**bigint**|Anzahl der durch alle Sweeps entfernten Einträge. Lässt keine NULL-Werte zu.|  
|**updated_last_round_count**|**bigint**|Anzahl der während des letzten Sweeps aktualisierten Einträge. Lässt keine NULL-Werte zu.|  
|**removed_last_round_count**|**bigint**|Anzahl der während des letzten Sweeps entfernten Einträge. Lässt keine NULL-Werte zu.|  
|**last_tick_time**|**bigint**|Letzter Zeitpunkt, in Millisekunden, zu dem sich der Uhrzeiger bewegt hat. Lässt keine NULL-Werte zu.|  
|**round_start_time**|**bigint**|Zeitpunkt des letzten Sweeps in Millisekunden. Lässt keine NULL-Werte zu.|  
|**last_round_start_time**|**bigint**|Gesamtzeit in Millisekunden, die die Uhr für die letzte Umdrehung benötigt hat. Lässt keine NULL-Werte zu.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.   
  
## <a name="remarks"></a>Hinweise  
 Die Informationen werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Arbeitsspeicher in einer Struktur gespeichert, die als Arbeitsspeichercache bezeichnet wird. Die Informationen im Cache können Daten, Indexeinträge, kompilierte Prozedurpläne und eine Vielzahl anderer Typen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Informationen sein. Damit vermieden wird, dass die Informationen neu erstellt werden müssen, werden diese solange wie möglich im Arbeitsspeichercache beibehalten und erst dann aus dem Cache entfernt, wenn sie zu alt sind, um noch hilfreich zu sein, oder wenn der Arbeitsspeicherplatz für neue Informationen benötigt wird. Der Vorgang, bei dem alte Informationen entfernt werden, wird als Arbeitsspeichersweep bezeichnet. Der Arbeitsspeichersweep ist eine häufige, jedoch keine kontinuierliche Aktivität. Der Sweep des Arbeitsspeichercaches wird von einem Taktalgorithmus gesteuert. Jeder Takt kann mehrere Arbeitsspeichersweeps steuern, die als Zeiger bezeichnet werden. Der Taktzeiger des Arbeitsspeichercaches stellt die aktuelle Position eines der Zeiger eines Arbeitsspeichersweeps dar.  

## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

