---
title: Schnelle Vorwärtscursor (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cc07980dfe78bb22c6281b19d8684d846f8a8db1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67902439"
---
# <a name="fast-forward-only-cursors-odbc"></a>Schnelle Vorwärtscursor (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt leistungsoptimierungen für Vorwärtscursor und schreibgeschützte Cursor. Schnelle Vorwärtscursor werden vom Treiber und Server intern auf ganz ähnliche Weise implementiert wie Standardresultsets. Neben einer hohen Leistungsfähigkeit besitzen schnelle Vorwärtscursor auch folgende Eigenschaften:  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt. Die Resultsetspalten müssen an Programmvariablen gebunden sein.  
  
-   Wenn der Server auf das Ende des Cursors stößt, wird der Cursor automatisch geschlossen. Die Anwendung muss trotzdem aufrufen [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), aber der Treiber muss nicht die schließende-Anforderung an den Server gesendet. Damit wird ein Roundtrip durch das Netzwerk zum Server eingespart.  
  
 Anwendungen fordern mit dem treiberspezifischen Anweisungsattribut SQL_SOPT_SS_CURSOR_OPTIONS schnelle Vorwärtscursor an. Wenn dieses auf SQL_CO_FFO festgelegt wird, werden schnelle Vorwärtscursor ohne die automatische Abrufoption aktiviert. Wenn es auf SQL_CO_FFO_AF festgelegt wird, wird auch die automatische Abrufoption aktiviert. Weitere Informationen zur automatischen Abrufoption finden Sie unter [Using Autofetch mit ODBC-Cursorn](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md).  
  
 Schnelle Vorwärtscursor mit automatischer Abrufoption können eingesetzt werden, um kleine Resultsets mit nur einem Roundtrip zum Server abzurufen. In den folgenden Schritten *n* ist die Anzahl der zurückzugebenden Zeilen an:  
  
1.  Legen Sie SQL_SOPT_SS_CURSOR_OPTIONS auf SQL_CO_FFO_AF fest.  
  
2.  Legen Sie SQL_ATTR_ROW_ARRAY_SIZE auf *n* + 1.  
  
3.  Binden Sie die Ergebnisspalten an Arrays von *n* + 1 Elementen (um sicherzugehen Wenn *n* + 1 Zeilen tatsächlich abgerufen werden).  
  
4.  Öffnen Sie den Cursor entweder mit **SQLExecDirect** oder **SQLExecute**.  
  
5.  Wenn der Rückgabestatus SQL_SUCCESS lautet, rufen Sie **SQLFreeStmt** oder **SQLCloseCursor** Schließen des Cursors. Alle Daten für die Zeilen sind in den gebundenen Programmvariablen enthalten.  
  
 Mit diesen Schritten die **SQLExecDirect** oder **SQLExecute** sendet eine Cursor-öffnen-Anforderung mit die automatische Abrufoption aktiviert. Auf diese einzelne Anforderung vom Client, führt der Server Folgendes aus:  
  
-   Er öffnet den Cursor.  
  
-   Er erstellt das Resultset und sendet die Zeilen an den Client.  
  
-   Weil die Rowsetgröße auf einen Wert festgelegt wurde, der um 1 größer als die Anzahl der Resultsetzeilen ist, erkennt der Server das Ende des Cursors und schließt den Cursor.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zur Programmierung von Cursor &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
