---
title: sys.pdw_materialized_view_distribution_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 165e143dd1293520c10596117128566a4197ef29
ms.sourcegitcommit: e4b241fd92689c2aa6e1f5e625874bd0b807dd01
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2019
ms.locfileid: "67566632"
---
# <a name="syspdwmaterializedviewdistributionproperties-transact-sql-preview"></a>sys.pdw_materialized_view_distribution_properties (Transact-SQL) (preview)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Zeigt Informationen über die Verteilung materialisierten Sichten.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------| 
|object_id|**int**|Die ID der materialisierte Sicht für die drei Eigenschaften angegeben wurden.| 
|distribution_policy |**tinyint**|2 = HASH</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar(60)**|HASH, ROUND_ROBIN|  
 
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW DATABASE STATE-Berechtigung.
 
## <a name="see-also"></a>Siehe auch

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[Anweisung ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In Azure SQL Data Warehouse unterstützte Systemsichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[T-SQL-Anweisungen, die in Azure SQL Data Warehouse unterstützt](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
