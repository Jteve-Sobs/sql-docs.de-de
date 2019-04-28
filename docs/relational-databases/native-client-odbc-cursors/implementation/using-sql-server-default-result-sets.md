---
title: Mithilfe von SQL Server-Standardresultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0491df6a2e653a54370bbc3951b625ef9af0691c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013752"
---
# <a name="using-sql-server-default-result-sets"></a>Verwenden von SQL Server-Standardresultsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Die standardmäßigen ODBC-Cursorattribute sind:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Wenn diese Attribute auf ihre Standardwerte festgelegt sind das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standardresultset. Standardresultsets können für beliebige, von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützte SQL-Anweisungen verwendet werden und stellen die effizienteste Methode für die Übertragung des gesamten Resultsets an den Client dar.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Unterstützung für mehrere aktive Resultsets (MARS); Anwendungen können nun über mehrere verfügen aktive Standardresultsets pro Verbindung festgelegt. MARS ist standardmäßig nicht aktiviert.  
  
 Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] unterstützten Standardresultsets nicht mehrere aktive Anweisungen über die gleiche Verbindung. Nach der Ausführung einer SQL-Anweisung über eine Verbindung akzeptiert der Server keine Befehle vom Client für diese Verbindung (außer der Anforderung zum Abbrechen des restlichen Resultsets), bis alle Zeilen im Resultset verarbeitet wurden. Um die restlichen ein teilweise verarbeitetes Resultset zu löschen, rufen [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit der *fOption* -Parameter auf SQL_CLOSE festgelegt. Rufen Sie ein teilweise verarbeitetes Resultset und den Test auf das Vorhandensein von einem anderen Resultset abschließend [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md). Wenn eine ODBC-Anwendung versucht einen Befehl für ein Verbindungshandle aus, bevor ein Standardresultset vollständig verarbeitet wurde, generiert der Aufruf SQL_ERROR und ein Aufruf von **SQLGetDiagRec** zurückgibt:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
