---
title: Erstellen von und Zugreifen auf tempdb-Tabellen über gespeicherte Prozeduren
description: tempdb unterstützt das Erstellen von und Zugreifen auf Tabellen aus nativ kompilierten gespeicherten Prozeduren nicht. Verwenden Sie speicheroptimierte Tabellen oder Tabellentypen und Tabellenvariablen.
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 60be5a470cffa69ab58251b57c1668ab5213a212
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723353"
---
# <a name="create-and-access-tables-in-tempdb-from-stored-procedures"></a>Erstellen und Zugreifen auf Tabellen in TempDB aus gespeicherten Prozeduren
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Das Erstellen von und Zugreifen auf Tabellen in TempDB aus systemintern kompilierten gespeicherten Prozeduren wird nicht unterstützt. Verwenden Sie stattdessen entweder speicheroptimierte Tabellen mit DURABILITY=SCHEMA_ONLY, oder verwenden Sie Tabellentypen und Tabellenvariablen. 

Weitere Informationen zur Speicheroptimierung temporärer Tabellen und Tabellenvariablenszenarien finden Sie unter: [Schnellere temporäre Tabellen und Tabellenvariablen durch Speicheroptimierung](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md).
  
  Im folgenden Beispiel wird veranschaulicht, wie Sie anstelle einer temporären Tabelle mit drei Spalten (ID, ProductID, Quantity) eine Tabellenvariable **\@OrderQuantityByProduct** des Typs **dbo.OrderQuantityByProduct** verwenden können:  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'ENGLISH'  
)  
  -- declare table variables for the list of orders   
  DECLARE @OrderQuantityByProduct dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @OrderQuantityByProduct SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte.](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
