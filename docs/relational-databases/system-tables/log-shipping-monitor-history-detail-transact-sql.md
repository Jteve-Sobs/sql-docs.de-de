---
title: Log_shipping_monitor_history_detail (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_history_detail_TSQL
- log_shipping_monitor_history_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_history_detail system table
ms.assetid: 7080c888-323b-4206-a1ab-e6c51f9e2579
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f0a304020b972b29d521bd32da3f98b8d3fdfc9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989995"
---
# <a name="logshippingmonitorhistorydetail-transact-sql"></a>log_shipping_monitor_history_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert Verlaufsdetails für Protokollversandaufträge. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 Die verlaufs- und überwachungsverbundenen Tabellen werden auch auf dem primären und dem sekundären Server verwendet.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|Die primäre ID für Sicherungsvorgänge oder die sekundäre ID für Kopier- oder Wiederherstellungsvorgänge.|  
|**agent_type**|**tinyint**|Der Typ des Protokollversandauftrags.<br /><br /> 0 = Sicherungsauftrag<br /><br /> 1 = Kopierauftrag<br /><br /> 2 = Wiederherstellungsauftrag|  
|**session_id**|**int**|Die Sitzungs-ID für den Sicherungs-/Kopier-/Wiederherstellungsauftrag|  
|**database_name**|**sysname**|Der Name der Datenbank, die diesem Datensatz zugeordnet ist. Die primäre Datenbank für Sicherungsaufträge, die sekundäre Datenbank für Wiederherstellungsaufträge oder eine leere Datenbank für Kopieraufträge.|  
|**session_status**|**tinyint**|Der Status der Sitzung<br /><br /> 0 = Wird gestartet<br /><br /> 1 = Aktiv<br /><br /> 2 = Erfolg<br /><br /> 3 = Fehler<br /><br /> 4 = Warnung|  
|**log_time**|**datetime**|Datum und Uhrzeit der Datensatzerstellung|  
|**log_time_utc**|**datetime**|Datum und Uhrzeit der Datensatzerstellung in UTC (Coordinated Universal Time, Koordinierte Weltzeit)|  
|**Nachricht**|**nvarchar(max)**|Meldungstext.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Tabelle enthält Verlaufsdetails für die Protokollversand-Agents. Zur Identifizierung einer Agentsitzung können Sie die Spalten **agent_id**, **agent_type**und **session_id**verwenden. Zum Anzeigen der Verlaufsdetails für die Agentsitzung sortieren Sie sie nach **log_time**.  
  
 Die Informationen, die sich auf den primären Server beziehen, werden nicht nur auf dem Remoteüberwachungsserver, sondern auch auf dem primären Server selbst in der **log_shipping_monitor_history_detail** -Tabelle gespeichert. Die Informationen, die sich auf einen sekundären Server beziehen, werden auch auf dem sekundären Server in der **log_shipping_monitor_history_detail** -Tabelle gespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [log_shipping_monitor_error_detail &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
  
  
