---
title: Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: badfb3afaeba92f366e62fce8dfcb3ec7dae9f29
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63311959"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank (MySQLToSql))
SQL Server Migration Assistant (SSMA) for MySQL ist eine umfassende Umgebung, die Sie schnell MySQL-Datenbanken zu SQL Server oder SQL Azure migriert werden kann. SSMA für MySQL verwenden, können Sie überprüfen von Datenbankobjekten und Daten, Datenbanken für die Migration zu bewerten, Datenbankobjekte in SQL Server oder SQL Azure migrieren und dann Migrieren von Daten in SQL Server oder SQL Azure.  
  
## <a name="recommended-migration-process"></a>Empfohlene Migrationsprozess  
Um erfolgreich Objekte und Daten aus MySQL-Datenbanken zu SQL Server oder SQL Azure zu migrieren, verwenden Sie den folgenden Prozess:  
  
1.  [Arbeiten mit SSMA-Projekten &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    Nachdem Sie das Projekt erstellt haben, können Sie die projektkonvertierung, Migration und Zuordnungsoptionen Typ festlegen. Weitere Informationen zu projekteinstellungen finden Sie unter [Setting Project Options Projektoptionen &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Informationen dazu, wie Sie die replikationsdatentyp-Zuordnungen anpassen, finden Sie unter [Zuordnen von MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Herstellen einer Verbindung mit SQLServer &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Zuordnen von MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  Optional [Bewerten von MySQL-Datenbanken für die Konvertierung &#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) Datenbankobjekte für die Konvertierung zu bewerten und die Konvertierungszeit zu schätzen.  
  
7.  [Konvertieren von MySQL-Datenbanken &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Synchronisierung](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. Dies ist in einem der folgenden Arten möglich:  
  
    -   Speichern Sie ein Skript, und führen Sie sie auf SQL Server oder SQL Azure.  
  
    -   Synchronisieren Sie die Datenbankobjekte.  
  
10. [Migrieren von MySQL-Daten in SQLServer – Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. Bei Bedarf datenbankanwendungen zu aktualisieren.  
  
> [!NOTE]  
> Information_schema und MySQL-Schemas können nicht migriert werden.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Erste Schritte mit SSMA für MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
