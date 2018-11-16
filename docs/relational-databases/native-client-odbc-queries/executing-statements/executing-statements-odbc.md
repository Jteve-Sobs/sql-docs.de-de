---
title: Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c53532d0331cf098561d874ff32475ea8a31b57d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657230"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet verschiedene Möglichkeiten zum Ausführen von SQL-Anweisungen in einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank:  
  
-   Direkte Ausführung  
  
-   Die vorbereitete Ausführung  
  
 Direkte Ausführung erfordert die Bildung einer Zeichenfolge Zeichen mit einem [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung und die Übermittlung dieser für die Ausführung mit der **SQLExecDirect** Funktion. Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. Der ersten Phase wird die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) zu analysieren und Kompilieren den Ausführungsplan für die Anweisung in der [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Der zweiten Phase wird die **SQLExecute** Funktion, um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Vorbereitete Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Vorgehensweisen](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Batches von Anweisungen](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
