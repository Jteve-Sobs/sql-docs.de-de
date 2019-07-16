---
title: Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 1517e17a7b0ecaf9137e3af21e076dacc2fd98f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207057"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
  Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet verschiedene Möglichkeiten zum Ausführen von SQL-Anweisungen in einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank:  
  
-   Direkte Ausführung  
  
-   Die vorbereitete Ausführung  
  
 Direkte Ausführung erfordert die Bildung einer Zeichenfolge Zeichen mit einem [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung und die Übermittlung dieser für die Ausführung mit der **SQLExecDirect** Funktion. Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. Der ersten Phase wird die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) zu analysieren und Kompilieren den Ausführungsplan für die Anweisung in der [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Der zweiten Phase wird die **SQLExecute** Funktion, um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](direct-execution.md)  
  
-   [Vorbereitete Ausführung](prepared-execution.md)  
  
-   [Vorgehensweisen](procedures.md)  
  
-   [Batches von Anweisungen](batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
