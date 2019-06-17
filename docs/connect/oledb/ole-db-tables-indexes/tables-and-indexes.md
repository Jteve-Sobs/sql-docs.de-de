---
title: Tabellen und Indizes | Microsoft-Dokumentation
description: Erstellen, ändern und Droping Tabellen und Indizes, die mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 8fd98f67a35985474d73225db7991aeeafb9119e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801586"
---
# <a name="tables-and-indexes"></a>Tabellen und Indizes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server stellt die Schnittstellen **IIndexDefinition** und **ITableDefinition** zur Verfügung und ermöglicht es Consumern, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen und -Indizes zu erstellen, zu ändern und zu löschen. Gültige Tabellen- und Indexdefinitionen hängen von der Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab.  
  
 Die Möglichkeit, Tabellen und Indizes zu erstellen oder zu löschen, hängt von den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Zugriffsrechten des Benutzers der Consumeranwendung ab. Das Löschen einer Tabelle kann durch das Vorhandensein von Beschränkungen der deklarativen referenziellen Integrität oder anderer Faktoren weiter eingeschränkt sein.  
  
 Die meisten Anwendungen, die für die Zielplattform [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden Sie SQL-DMO statt dieser OLE DB-Treiber für SQL Server-Schnittstellen. SQL-DMO steht für eine Auflistung von OLE-Automatisierungsobjekten, die alle administrativen Funktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützen. Anwendungen, die auf mehrere OLE DB-Anbieter ausgerichtet sind, verwenden diese generischen OLE DB-Schnittstellen, die von den verschiedenen OLE DB-Anbietern unterstützt werden.  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERCOLUMN definiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die folgende Eigenschaft.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Typ: VT_BSTR<br /><br /> R/W: Schreiben<br /><br /> Default: NULL<br /><br /> Beschreibung: Diese Eigenschaft wird nur in **ITableDefinition** verwendet. Die in dieser Eigenschaft angegebene Zeichenfolge wird beim Erstellen einer [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md)-Anweisung verwendet.<br /><br /> verwendet.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen von SQL Server-Tabellen](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Hinzufügen einer Spalte zu einer SQL Server-Tabelle](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Entfernen einer Spalte aus einer SQL Server-Tabelle](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Löschen einer SQL Server-Tabelle](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Erstellen von SQL Server-Indizes](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Löschen eines SQL Server-Index](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB Driver for SQL Server Programming (OLE DB-Treiber für SQL Server-Programmierung)](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
