---
title: sys.pdw_database_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1a07d8074c4d7de7ebe9fea214f4d00ea25d3a3e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012935"
---
# <a name="syspdwdatabasemappings-transact-sql"></a>sys.pdw_database_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Zuordnungen der **Database_id**s von Datenbanken auf dem physischen Namen auf Compute-Knoten verwendet, und bietet die **Prinzipal-Id** der Besitzer der Datenbank, auf dem System. Join **sys.pdw_database_mappings** zu **sys.databases** und **sys.pdw_nodes_pdw_physical_databases**.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|Der physische Name für die Datenbank auf den Computeknoten.<br /><br /> **Physical_name** und **Database_id** bilden den Schlüssel für diese Sicht.||  
|database_id|**int**|Die Objekt-ID für die Datenbank. Finden Sie unter [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **Physical_name** und **Database_id** bilden den Schlüssel für diese Sicht.||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel verknüpft sys.pdw_database_mappings mit anderen Systemtabellen, um anzuzeigen, wie Datenbanken zugeordnet werden.  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys.pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_nodes_pdw_physical_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

