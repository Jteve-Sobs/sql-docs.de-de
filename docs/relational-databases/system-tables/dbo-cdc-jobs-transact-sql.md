---
title: cdc_jobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c9668c234728dc34952a7095889fe6ba5cfd06a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084704"
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert die Change Data Capture-Konfigurationsparameter für Aufzeichnungs- und Cleanupaufträge. Diese Tabelle befindet sich in **Msdb**.  
  
 
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID der Datenbank, in der der Auftrag ausgeführt wird.|  
|**job_type**|**nvarchar(20)**|Typ des Auftrags, entweder 'capture' oder 'cleanup'.|  
|**job_id**|**uniqueidentifier**|Dem Auftrag zugeordnete eindeutige ID.|  
|**maxtrans**|**int**|Die maximale Anzahl der in jedem Scanzyklus zu verarbeitenden Transaktionen.<br /><br /> **Maxtrans** ist nur für aufzeichnungsaufträge gültig.|  
|**maxscans**|**int**|Die maximale Anzahl der scanzyklen, ausführen, um alle Zeilen aus dem Protokoll zu extrahieren.<br /><br /> **Maxscans** ist nur für aufzeichnungsaufträge gültig.|  
|**fortlaufende**|**bit**|Flag, das angibt, ob der Aufzeichnungsauftrag fortlaufend (1) oder einmalig (0) ausgeführt werden soll. Weitere Informationen finden Sie unter [sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **fortlaufende** ist nur für aufzeichnungsaufträge gültig.|  
|**PollingInterval**|**bigint**|Anzahl der Sekunden zwischen Protokollscanzyklen.<br /><br /> **PollingInterval** ist nur für aufzeichnungsaufträge gültig.|  
|**retention**|**bigint**|Anzahl der Minuten, die Änderungszeilen in Änderungstabellen beibehalten werden sollen.<br /><br /> **Aufbewahrung** ist nur für cleanupaufträge gültig.|  
|**threshold**|**bigint**|Die maximale Anzahl von Einträgen für Löschvorgänge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können.|  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys.sp_cdc_change_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys.sp_cdc_drop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
