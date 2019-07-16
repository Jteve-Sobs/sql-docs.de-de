---
title: dm_io_pending_io_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4006679f601bbed26ea092f39f8f7b5fb810e99a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900345"
---
# <a name="sysdmiopendingiorequests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede ausstehende E/A-Anforderung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_io_pending_io_requests**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|Arbeitsspeicheradresse der E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_type**|**nvarchar(60)**|Typ der ausstehenden E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_pending_ms_ticks**|**bigint**|Nur interne Verwendung. Lässt keine NULL-Werte zu.| 
|**io_pending**|**int**|Gibt an, ob die E/A-Anforderung ausstehend ist oder von Windows abgeschlossen wurde. Eine E/A-Anforderung kann noch ausstehend sein, selbst wenn Windows die Anforderung abgeschlossen hat, aber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] noch keinen Kontextwechsel ausgeführt hat, bei dem die E/A-Anforderung verarbeitet und aus dieser Liste entfernt würde. Lässt keine NULL-Werte zu.|  
|**io_completion_routine_address**|**varbinary(8)**|Interne Funktion, die nach Abschluss der E/A-Anforderung aufgerufen wird. Lässt NULL-Werte zu.|  
|**io_user_data_address**|**varbinary(8)**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**scheduler_address**|**varbinary(8)**|Das Zeitplanungsmodul, in dem diese E/A-Anforderung ausgestellt wurde. Die E/A-Anforderung wird in der Liste ausstehender E/A-Anforderungen des Zeitplanungsmoduls angezeigt. Weitere Informationen finden Sie unter [DM_OS_SCHEDULERS &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). Lässt keine NULL-Werte zu.|  
|**io_handle**|**varbinary(8)**|Dateihandle der Datei, die in der E/A-Anforderung verwendet wird. Lässt NULL-Werte zu.|  
|**io_offset**|**bigint**|Offset der E/A-Anforderung. Lässt keine NULL-Werte zu.|  
|**io_handle_path**|**nvarchar(256)**| Pfad der Datei, die in der e/a-Anforderung verwendet wird. Lässt NULL-Werte zu.|
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] ist die Berechtigung `VIEW DATABASE STATE` in der Datenbank erforderlich.   
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [E/A im Zusammenhang, dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


