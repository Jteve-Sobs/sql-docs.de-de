---
title: MSrepl_identity_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38f5037598e240585333d246a99c29c5fd8f40fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079160"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSrepl_identity_range** Tabelle stellt Unterstützung für die identitätsbereichsverwaltung bereit. Diese Tabelle wird in den Datenbanken publication, distribution und subscription gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**Tabellenname**|**sysname**|Der Name der Tabelle.|  
|**identity_support**|**int**|Gibt an, ob die automatische Behandlung der Identitätsbereiche aktiviert ist. 0 gibt an, dass die automatische Behandlung der Identitätsbereiche nicht aktiviert ist.|  
|**next_seed**|**bigint**|Wenn die automatische Behandlung der Identitätsbereiche aktiviert ist, zeigt dieser Wert den Anfangspunkt des nächsten Bereichs an.|  
|**pub_range**|**bigint**|Die Größe des Identitätsbereichs für den Verleger.|  
|**range**|**bigint**|Die Bereichsgröße der aufeinander folgenden Identitätswerte, die Abonnenten bei einer Anpassung zugewiesen würden.|  
|**max_identity**|**bigint**|Die obere Grenze des Identitätsbereichs.|  
|**threshold**|**int**|Als Prozentsatz angegebener Schwellenwert für den Identitätsbereich.|  
|**current_max**|**bigint**|Der aktuelle maximale Wert, der zugewiesen werden kann, aber nicht notwendigerweise zugewiesen werden muss.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
