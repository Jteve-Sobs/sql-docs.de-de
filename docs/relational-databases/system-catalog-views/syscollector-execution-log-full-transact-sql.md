---
title: Syscollector_execution_log_full (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_full
- syscollector_execution_log_full_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log_full view
ms.assetid: 6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99ce8003b70ad41be225a7678c97ed44d9f6c7dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62760176"
---
# <a name="syscollectorexecutionlogfull-transact-sql"></a>syscollector_execution_log_full (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen über einen Sammlungssatz oder ein Paket bereit, wenn das Ausführungsprotokoll voll ist.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|Identifiziert jede Sammlungssatzausführung. Wird verwendet, um diese Sicht mit anderen ausführlichen Protokollen zu verknüpfen. Lässt NULL-Werte zu.|  
|parent_log_id|**bigint**|Identifiziert das übergeordnete Paket oder den Sammlungssatz. Lässt keine NULL-Werte zu. Die IDs werden in der Über-/Unterordnungsbeziehung verkettet. Auf diese Weise können Sie bestimmen, welches Paket von welchem Sammlungssatz gestartet wurde. Diese Sicht gruppiert die Protokolleinträge nach ihren über-und untergeordneten Verknüpfungen und rückt die Namen der Pakete, sodass die Aufrufkette übersichtlich angezeigt wird.|  
|NAME|**nvarchar(4000)**|Der Name des Sammlungssatzes oder des Pakets, der bzw. das von diesem Protokolleintrag dargestellt wird. Lässt NULL-Werte zu.|  
|status|**smallint**|Gibt den aktuellen Status des Sammlungssatzes oder des Pakets an. Lässt NULL-Werte zu.<br /><br /> Die Werte sind:<br /><br /> 0 = Wird ausgeführt<br /><br /> 1 = Beendet<br /><br /> 2 = Fehler|  
|runtime_execution_mode|**smallint**|Gibt an, ob die Collection Set-Aktivität wurde das Sammeln von Daten oder Hochladen von Daten. Lässt NULL-Werte zu.|  
|start_time|**datetime**|Die Startzeit für den Sammlungssatz oder das Paket. Lässt NULL-Werte zu.|  
|last_iteration_time|**datetime**|Für kontinuierlich ausgeführte Pakete der letzte Zeitpunkt, zu dem das Paket eine Momentaufnahme aufgezeichnet hat. Lässt NULL-Werte zu.|  
|finish_time|**datetime**|Der Zeitpunkt, zu dem der Testlauf für abgeschlossene Pakete und Sammlungssätze beendet wurde. Lässt NULL-Werte zu.|  
|duration|**int**|Gibt an, wie lange (in Sekunden) das Paket oder der Sammlungssatz ausgeführt wurde. Lässt NULL-Werte zu.|  
|failure_message|**nvarchar(2048)**|Wenn bei einem Sammlungssatz oder einem Paket ein Fehler aufgetreten ist, die aktuelle Fehlermeldung für die jeweilige Komponente. Lässt NULL-Werte zu. Um ausführlichere Fehlerinformationen abzurufen, verwenden die [Fn_syscollector_get_execution_details &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md) Funktion.|  
|Operator|**nvarchar(128)**|Gibt an, wer den Sammlungssatz oder das Paket gestartet hat. Lässt NULL-Werte zu.|  
|package_execution_id|**uniqueidentifier**|Stellt einen Link zur [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Protokolltabelle bereit. Lässt NULL-Werte zu.|  
|collection_set_id|**int**|Stellt einen Link zur Datensammlungs-Konfigurationstabelle in msdb bereit. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT für **dc_operator**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Sichten des Datensammlers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
