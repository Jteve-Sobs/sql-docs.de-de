---
title: Unterstützte Datentypen für In-Memory OLTP | Microsoft-Dokumentation
description: Informieren Sie sich über die Datentypen, die für die In-Memory-OLTP-Features „Speicheroptimierte Tabelle“ und „Nativ kompilierte T-SQL-Module“ nicht unterstützt werden.
ms.custom: ''
ms.date: 06/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 324d9c27608bd5ee3e93a6987cec7b81407f048a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650929"
---
# <a name="supported-data-types-for-in-memory-oltp"></a>Unterstützte Datentypen für In-Memory OLTP
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  In diesem Artikel werden die Datentypen aufgeführt, die keine Unterstützung erhalten für die In-Memory OLTP-Features für:  
  
-   Speicheroptimierte Tabellen  
  
-   Nativ kompilierte T-SQL-Module  
  
## <a name="unsupported-data-types"></a>Nicht unterstützte Datentypen  
 Die folgenden Datentypen werden nicht unterstützt:  
  
||||  
|-|-|-|  
|[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography &#40;Transact-SQL&#41;](../../t-sql/spatial-geography/spatial-types-geography.md)|[geometry &#40;Transact-SQL&#41;](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)|  
|[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)|[xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)|Benutzerdefinierte Typen|erforderlich.|  
  
## <a name="notable-supported-data-types"></a>Wichtige unterstützte Datentypen  
 Die meisten Datentypen werden von den Features von In-Memory OLTP unterstützt. Im folgenden Typen sollten explizit beachtet werden:  
  
|Zeichenfolgen- und Binärtypen|Weitere Informationen finden Sie unter|  
|-----------------------------|--------------------------|  
|binary und varbinary*|[binary und varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char und varchar*|[char und varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar und nvarchar*|[nchar und nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Für die vorhergehenden Zeichenfolgen- und binären Datentypen ab SQL Server 2016:  
  
- Eine einzelne speicheroptimierte Tabelle kann auch mehrere lange Spalten wie `nvarchar(4000)`enthalten, obwohl ihre Länge die physische Zeilengröße von 8060 Bytes überschreiten würde.  
  
- Eine speicheroptimierte Tabelle kann Zeichenfolgen mit maximaler Länge und binären Spalten mit Datentypen wie `varchar(max)`beinhalten.  


### <a name="identify-lobs-and-other-columns-that-are-off-row"></a>Identifizieren von LOBs und anderen Spalten außerhalb von Zeilen

Beginnend mit SQL Server 2016, unterstützen speicheroptimierte Tabellen [Spalten außerhalb von Zeilen](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md), die eine einzelne Tabellenzeile größer sein als 8060 Bytes zu ermöglichen. Die folgende Transact-SQL-SELECT-Anweisung gibt für speicheroptimierte Tabellen alle Spalten zurück, die sich außerhalb von Zeilen befinden. Beachten Sie dabei Folgendes:

- Alle Indexschlüsselspalten werden innerhalb von Zeilen gespeichert.
  - Nicht eindeutige Indexschlüssel in speicheroptimierten Tabellen können auf NULL festlegbare Spalten enthalten.
  - Indizes können in einer speicheroptimierte Tabelle als UNIQUE deklariert werden.
- Alle LOB-Spalten werden außerhalb von Zeilen gespeichert.
- Ein max_length-Wert „-1“ gibt eine Spalte mit großen Objekten (Large Objects, LOBs) an.


```sql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


### <a name="other-data-types"></a>Andere Datentypen


|Andere Typen|Weitere Informationen finden Sie unter|  
|-----------------|--------------------------|  
|Tabellentypen|[Speicheroptimierte Tabellenvariablen](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Unterstützung für In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Implementieren von SQL_VARIANT in einer speicheroptimierten Tabelle](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
 [Tabellen- und Zeilengröße in speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
