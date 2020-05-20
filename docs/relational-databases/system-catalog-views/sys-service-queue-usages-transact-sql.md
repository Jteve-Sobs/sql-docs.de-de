---
title: sys. service_queue_usages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.service_queue_usages
- sys.service_queue_usages_TSQL
- service_queue_usages
- service_queue_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queue_usages catalog view
ms.assetid: d58dcdaf-f82d-43d9-941b-f520581442bf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: da3fa2b141714dc4efce5977719c08332538a506
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831353"
---
# <a name="sysservice_queue_usages-transact-sql"></a>sys.service_queue_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Katalogsicht gibt eine Zeile für jeden Verweis zwischen Dienst und Dienstwarteschlange zurück. Ein Dienst kann immer nur einer Warteschlange zugeordnet sein. Eine Warteschlange kann mehreren Diensten zugeordnet sein.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|Bezeichner des Diensts. Ist innerhalb der Datenbank eindeutig. Lässt keine NULL-Werte zu.|  
|**service_queue_id**|**int**|Bezeichner der Dienstwarteschlange, die von diesem Dienst verwendet wird. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. Services &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)  
  
  
