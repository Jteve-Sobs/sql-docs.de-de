---
description: sys.server_events (Transact-SQL)
title: sys. server_events (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 32c5057f8bc61cc3e27e0d67b9da6b515cec21e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460558"
---
# <a name="sysserver_events-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jedes Ereignis, für das eine Ereignisbenachrichtigung auf Serverebene oder ein DDL-Trigger auf Serverebene ausgelöst wird. Das Server Ereignis wird durch die Spalten **object_id** und den **Typ** eindeutig identifiziert.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der Ereignisbenachrichtigung auf Serverebene oder auszulösender DDL-Trigger auf Serverebene.|  
|**type**|**int**|Der Ereignistyp, der veranlasst, dass die Ereignisbenachrichtigung oder der DDL-Trigger ausgelöst wird.|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Ereignisses, durch das die Ereignisbenachrichtigung oder der DDL-Trigger ausgelöst wird.|  
|**event_group_type**|**int**|Ereignisgruppe, für die der Trigger oder die Ereignisbenachrichtigung erstellt wurde, bzw. NULL, wenn sie nicht für eine Ereignisgruppe erstellt wurden.|  
|**event_group_type_desc**|**nvarchar(60)**|Beschreibung der Ereignis Gruppe, für die der Auslöserwert oder die Ereignis Benachrichtigung erstellt wird, oder NULL, wenn Sie nicht für eine Ereignis Gruppe erstellt wurden.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
