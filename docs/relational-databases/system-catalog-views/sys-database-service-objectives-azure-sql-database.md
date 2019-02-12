---
title: Sys. database_service_objectives (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/30/2016
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- Pool für elastische Datenbanken
- Pool für elastische Datenbanken, Verwaltung
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7a073dba8a05aa6f098bdf2b2ce1666d4cc324be
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028521"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys. database_service_objectives (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Gibt die Edition (Dienstebene), das dienstziel (Tarif) und die Namen des Pools für elastische Datenbanken, zurück, falls vorhanden, für die Azure SQL-Datenbank oder Azure SQL Data Warehouse. Wenn der master-Datenbank in eine Azure SQL-Datenbank-Server angemeldet, gibt die Informationen für alle Datenbanken zurück. Informationen zu Azure SQL Data Warehouse müssen Sie mit der master-Datenbank verbunden werden.  
  
  
 Weitere Informationen zu den Preisen finden Sie unter [SQL-Datenbankoptionen und-Leistung: SQL-Datenbankpreise](https://azure.microsoft.com/pricing/details/sql-database/) und [SQL Data Warehouse-Preise](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Um die Einstellungen zu ändern, finden Sie unter [ALTER DATABASE (Azure SQL-Datenbank)](../../t-sql/statements/alter-database-azure-sql-database.md) und [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 Die Sicht Sys. database_service_objectives enthält die folgenden Spalten.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|database_id|ssNoversion|Die ID der Datenbank, eindeutig innerhalb einer Instanz von SQL-Datenbankserver. Mit beigetreten [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|-Edition|sysname|Die Dienstebene für die Datenbank oder vorhandenem Data Warehouse: **Grundlegende**, **Standard**, **Premium** oder **-Datawarehouse**.|  
|service_objective|sysname|Der Tarif der Datenbank. Wenn die Datenbank in Pools für elastische Datenbanken ist, gibt **ElasticPool**.<br /><br /> Auf der **grundlegende** -Ebene gibt **grundlegende**.<br /><br /> **Einzeldatenbank in einem standard-Dienstebene** gibt einen der folgenden zurück: S0, S1, S2, S3, S4, S6, S7, S9 und S12.<br /><br /> **Einzeldatenbank in einem Premium-Tarif** gibt Folgendes zurück: P1, P2, P4, P6, P11 oder P15-Datenbank.<br /><br /> **SQL Data Warehouse** DW100 über DW10000c zurückgibt.|  
|elastic_pool_name|sysname|Der Name des der [Pool für elastische Datenbanken](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) , zu der die Datenbank gehört. Gibt **NULL** , wenn die Datenbank eine einzeldatenbank oder eine Warehoue Daten ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert **"DBManager"** -Berechtigung für die master-Datenbank.  Auf Datenbankebene muss der Benutzer der Ersteller oder Besitzer sein.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel kann auf die Masterdatenbank oder Benutzerdatenbanken ausgeführt werden. Die Abfrage gibt den Namen, Dienst und Leistungsinformationen über die Ebene der Datenbank(en).  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
