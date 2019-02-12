---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 328d949afc548b179f26ba83f06348ccb72cbe1f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025341"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält weitere ausführliche Informationen über die Informationen in [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), Informationen zu laufenden und abgeschlossenen sicherungs- und Wiederherstellungsvorgänge in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und zur laufenden und abgeschlossen, Sicherung, Wiederherstellung und Ladevorgänge in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Die Informationen persistieren über Systemneustarts.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Eindeutiger Bezeichner für eine bestimmte Sicherung oder Wiederherstellung ausgeführt.<br /><br /> bilden den Schlüssel für diese Ansicht, Run_id und Pdw_node_id.||  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines Appliance-Knotens, der die Details dieser Datensatz enthält.<br /><br /> bilden den Schlüssel für diese Ansicht, Run_id und Pdw_node_id.|Finden Sie unter Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|Der aktuelle Status der Ausführung.|'CANCELLED', 'COMPLETED', 'FAILED', 'QUEUED', 'RUNNING'|  
|start_time|**datetime**|Zeitpunkt, an dem der Vorgang auf diesem bestimmten Knoten gestartet wurde.||  
|end_time|**datetime**|Zeit, zu dem der Vorgang auf diesem bestimmten Knoten ggf. beendet wurde.||  
|total_elapsed_time|**int**|Gesamtdauer des Vorgangs auf diesem bestimmten Knoten ausgeführt wurde.|Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen.<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|Wird ausgeführt|**int**|Status des Vorgangs als Prozentsatz ausgedrückt.|0 bis 100|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
