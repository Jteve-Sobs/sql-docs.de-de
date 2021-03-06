---
title: sys.sysperfinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
author: rothja
ms.author: jroth
ms.openlocfilehash: a2cdadb112dbceb6a3b031707b8ba8b889bad822
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895851"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Darstellung der internen Leistungsindikatoren, die über den Windows-System Monitor angezeigt werden können.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_name**|**NCHAR (128)**|Der Name des Leistungsobjekts, z. b. **SQLServer: lockmanager** oder **SQLServer: BufferManager**.|  
|**counter_name**|**NCHAR (128)**|Der Name des Leistungs Zählers innerhalb des Objekts, z. b. **angeforderte** **Seiten Anforderungen** oder sperren.|  
|**instance_name**|**NCHAR (128)**|Benannte Instanz des Indikators. Beispielsweise werden für jede Art von Sperre Leistungsindikatoren verwaltet, z. b. **Tabelle**, **Seite**, **Schlüssel**usw. Durch den Instanznamen kann zwischen ähnlichen Indikatoren unterschieden werden.|  
|**cntr_value**|**bigint**|Tatsächlicher Indikatorwert. Häufig ist dies ein konstanter oder monoton wachsender Leistungsindikator, der das Auftreten des Instanzereignisses zählt.|  
|**cntr_type**|**int**|Typ des Leistungsindikators, wie von der Windows-Leistungsarchitektur definiert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
