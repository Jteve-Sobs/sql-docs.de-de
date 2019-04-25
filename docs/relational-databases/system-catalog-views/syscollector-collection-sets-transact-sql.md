---
title: Syscollector_collection_sets (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collection_sets_TSQL
- syscollector_collection_sets
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collection_sets view
ms.assetid: db0def92-f25b-45da-9709-eab972b33800
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dcc027ad80d4bbe1142a9e17add52f8a42d7d404
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760200"
---
# <a name="syscollectorcollectionsets-transact-sql"></a>syscollector_collection_sets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu einem Sammlungssatz bereit, einschließlich Zeitplan, Sammlungsmodus und Status.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|collection_set_id|**int**|Der lokale Bezeichner für den Sammlungssatz. Lässt keine NULL-Werte zu.|  
|collection_set_uid|**uniqueidentifier**|Der GUID (Globally Unique Identifier) für den Sammlungssatz. Lässt keine NULL-Werte zu.|  
|NAME|**nvarchar(4000)**|Der Name des Sammlungssatzes. Lässt NULL-Werte zu.|  
|target|**nvarchar(max)**|Identifiziert das Ziel für den Sammlungssatz. Lässt NULL-Werte zu.|  
|is_system|**bit**|Aktiviert (1) oder deaktiviert (0), um anzugeben, ob der Sammlungssatz im Datensammler enthalten war oder später von dc_admin hinzugefügt wurde. Dies könnte ein benutzerdefinierter Sammlungssatz sein, der intern oder durch einen Drittanbieter entwickelt wurde. Lässt keine NULL-Werte zu.|  
|is_running|**bit**|Gibt an, ob der Sammlungssatz ausgeführt wird oder nicht. Lässt keine NULL-Werte zu.|  
|collection_mode|**smallint**|Gibt den Sammlungsmodus für den Sammlungssatz an. Lässt keine NULL-Werte zu.<br /><br /> Der Sammlungsmodus ist eines der folgenden Elemente:<br /><br /> 0 - Modus mit Zwischenspeicherung. Für Datensammlung und -upload werden separate Zeitpläne verwendet.<br /><br /> 1 - Modus ohne Zwischenspeicherung. Datensammlung und -upload basieren auf dem gleichen Zeitplan.|  
|proxy_id|**int**|Identifiziert den Proxy, der verwendet wird, um den Auftragsschritt des Sammlungssatz auszuführen. Lässt NULL-Werte zu.|  
|schedule_uid|**uniqueidentifier**|Stellt einen Zeiger auf den Zeitplan für den Sammlungssatz bereit. Lässt NULL-Werte zu.|  
|collection_job_id|**uniqueidentifier**|Identifiziert den Sammlungsauftrag. Lässt NULL-Werte zu.|  
|upload_job_id|**uniqueidentifier**|Identifiziert den Uploadauftrag für die Sammlung. Lässt NULL-Werte zu.|  
|logging_level|**smallint**|Gibt den Protokolliergrad (0, 1 oder 2) an. Lässt keine NULL-Werte zu.|  
|days_until_expiration|**smallint**|Die Anzahl der Tage, an denen die gesammelten Daten im Verwaltungs-Data Warehouse gespeichert werden. Lässt keine NULL-Werte zu.|  
|description|**nvarchar(4000)**|Beschreibt den Sammlungssatz. Lässt NULL-Werte zu.|  
|dump_on_any_error|**bit**|Aktiviert (1) oder deaktiviert (0), der angibt, ob zum Erstellen einer [!INCLUDE[ssIS](../../includes/ssis-md.md)] Dumpdatei bei jedem Fehler. Lässt keine NULL-Werte zu.|  
|dump_on_codes|**nvarchar(max)**|Enthält die Liste mit [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Fehlercodes, die verwendet werden, um die Erstellung der Dumpdatei auszulösen. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT für dc_operator, dc_proxy.  
  
## <a name="remarks"></a>Hinweise  
 Die Datensammler-API ermöglicht Ihnen nur, die von Ihnen erstellten Sammlungssätze zu ändern oder zu löschen. Die vom System bereitgestellten Sammlungssätze können weder geändert noch gelöscht werden. Sie können jedoch nach wie vor einen Systemsammlungssatz aktivieren oder deaktivieren und dessen Konfiguration ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Sichten des Datensammlers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
