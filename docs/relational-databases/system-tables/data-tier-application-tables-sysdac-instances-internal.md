---
title: "\"sysdac_instances_internal\" (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1e30db7b31a0a29a5e78e7fc5876f43764d66a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471115"
---
# <a name="data-tier-application-tables---sysdacinstancesinternal"></a>Tabellen von Datenschichtanwendung: sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt eine Zeile für jede Instanz der Datenebenenanwendung (DAC) an, die für eine [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz bereitgestellt wird. Diese Tabelle wird im Dbo-Schema in der Msdb-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|Der Bezeichner der DAC-Instanz.|  
|instance_name|**sysname**|Der Name der DAC-Instanz, die bei der Bereitstellung der Instanz angegeben wurde.|  
|type_name|**sysname**|Der Name der DAC, die bei der Erstellung des DAC-Pakets angegeben wurde.|  
|type_version|**nvarchar(64)**|Die Version der DAC, die bei der Erstellung des DAC-Pakets angegeben wurde.|  
|description|**nvarchar(4000)**|Eine Beschreibung der DAC, die bei der Erstellung des DAC-Pakets geschrieben wurde.|  
|type_stream|**varbinary(max)**|Ein Bitdatenstrom, der die codierte Darstellung der in der DAC enthaltenen logischen Objekte, z. B. Tabellen und Sichten, enthält.|  
|date_created|**datetime**|Datum und Uhrzeit der Erstellung der DAC-Instanz.|  
|created_by|**sysname**|Der Anmeldename, unter dem die DAC-Instanz erstellt wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Nur-Lese Zugriff auf diese Sicht ist für alle Benutzer mit Berechtigungen zum Verbinden mit der master-Datenbank verfügbar.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
