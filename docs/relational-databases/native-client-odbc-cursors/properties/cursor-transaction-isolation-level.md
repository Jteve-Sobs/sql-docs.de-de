---
title: Cursor-Transaktionsisolationsstufe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ae4ffc9b3a9c0d8122fb46ae9db215bf1560396
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078845"
---
# <a name="cursor-transaction-isolation-level"></a>Transaktionsisolationsstufen von Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Das komplette Sperrverhalten von Cursorn basiert auf der Interaktion zwischen Parallelitätsattributen und der vom Client festgelegten Transaktionsisolationsstufe. ODBC-Clients legen die Transaktionsisolationsstufe mithilfe der [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION oder SQL_COPT_SS_TXN_ISOLATION-Attribut. Das Transaktionssperrverhalten einer bestimmten Cursorumgebung wird durch die Kombination des Sperrverhaltens der Parallelitätseinstellung mit den Optionen für die Transaktionsisolationsstufen bestimmt.  
  
 Die folgenden cursortransaktionsisolationsstufen werden von unterstützt die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber:  
  
-   Read Committed (SQL_TXN_READ_COMMITTED)  
  
-   Read Uncommitted (SQL_TXN_READ_UNCOMMITTED)  
  
-   Repeatable Read (SQL_TXN_REPEATABLE_READ) lesen Sie  
  
-   Serializable (SQL_TXN_SERIALIZABLE)  
  
-   Momentaufnahme (SQL_TXN_SS_SNAPSHOT)  
  
 Beachten Sie, dass der ODBC-API zusätzliche Transaktionsisolationsstufen gibt, aber diese nicht, indem unterstützt werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
