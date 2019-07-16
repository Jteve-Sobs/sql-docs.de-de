---
title: Sys.dm_pdw_lock_waits (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8ef966f8-d14e-40d3-9626-3508ada9b8fb
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 29a82daa2857177200bd76b738f92d65f6b26668
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899376"
---
# <a name="sysdmpdwlockwaits-transact-sql"></a>sys.dm_pdw_lock_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu den Anforderungen, die Sperren warten.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Die Position der Anforderung in der Liste der wartenden.|0-basierte Ordnungszahl. Dies ist in allen Einträgen der Wartevorgang nicht eindeutig.|  
|session_id|**nvarchar(32)**|ID der Sitzung, in der der Wartezustand aufgetreten ist.|Finden Sie unter Sitzungs-ID in [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Typ|**nvarchar(255)**|Der Typ des Wartevorgangs, den dieser Eintrag darstellt.|Mögliche Werte:<br /><br /> Shared<br /><br /> SharedUpdate<br /><br /> ExclusiveUpdate<br /><br /> Exclusive|  
|object_type|**nvarchar(255)**|Der Typ des Objekts, das den Wartevorgang betroffen ist.|Mögliche Werte:<br /><br /> OBJECT<br /><br /> DATABASE<br /><br /> SYSTEM<br /><br /> SCHEMA<br /><br /> APPLICATION|  
|object_name|**nvarchar(386)**|Name oder die GUID des angegebenen Objekts, das von den Wartevorgang betroffen war.|Tabellen und Ansichten werden mit den dreiteiligen Namen angezeigt.<br /><br /> Indizes und Statistiken werden mit vierteiligen Namen angezeigt.<br /><br /> Namen, Prinzipale und Datenbanken sind die Zeichenfolgennamen.|  
|request_id|**nvarchar(32)**|Die ID der Anforderung auf der der Wartezustand aufgetreten ist.|ID der Anforderung.<br /><br /> Dies ist eine GUID für Anforderungen zum Laden.|  
|request_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder eine Ressource angefordert wurde.||  
|acquire_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder die Ressource abgerufen wurde.||  
|state|**nvarchar(50)**|Status des den Wartezustand.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Die Priorität des Elements warten.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
