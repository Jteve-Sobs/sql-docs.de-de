---
title: MSmerge_current_partition_mappings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_current_partition_mappings
- MSmerge_current_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_current_partition_mappings system table
ms.assetid: a3088840-5a30-40f5-8e8a-aa03afc4905f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98d2b2053fae49ae5beb3c9b7ecd0209dd33f56d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791532"
---
# <a name="msmergecurrentpartitionmappings"></a>MSmerge_current_partition_mappings
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_current_partition_mappings** -Tabelle speichert eine Zeile für jede Partitions-Id, die eine bestimmte geänderte Zeile gehört. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Die veröffentlichungsnummer, die in gespeichert ist **Sysmergepublications**.|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilenbezeichner für die angegebene Zeile.|  
|**partition_id**|**int**|Die ID der Partition, zu der die Zeile gehört. Der Wert ist 1, wenn die Änderung der Zeile an alle Abonnenten relevant ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
