---
title: Sysarticlecolumns (Systemsicht) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ffa8c9c45e1810fb4a81deed34f7c6c2e4a0ca0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756544"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (Systemsicht) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **Sysarticlecolumns** -Sicht macht zusätzliche Informationen zu Spalten in veröffentlichten Artikeln verfügbar. Diese Sicht wird in der distribution-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifiziert einen Artikel.|  
|**colid**|**int**|Identifiziert eine Spalte in einem Artikel.|  
|**is_udt**|**int**|Zeigt an, ob die Spalte dem benutzerdefinierten Datentyp (UDT) zugehört. Der Wert **1** eine UDT-Spalte angibt.|  
|**is_xml**|**int**|Wenn die Spalte ist eine **Xml** Spalte. Der Wert **1** gibt ein **Xml** Spalte.|  
|**is_max**|**int**|Ist die Spalte ist eine große werttypspalten für Daten (**varchar(max)**, **nvarchar(max)** oder **'varbinary(max)'**). Der Wert **1** gibt eine Spalte mit umfangreichen Werten.|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
