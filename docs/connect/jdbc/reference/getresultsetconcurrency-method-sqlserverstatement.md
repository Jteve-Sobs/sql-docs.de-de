---
title: getresultsetparallelcurrency-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 47ef6547-5ec7-4cf5-a4d4-e34cbeec72eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dee62a135b45b0181094aeec8b5edc063f6ffea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980378"
---
# <a name="getresultsetconcurrency-method-sqlserverstatement"></a>getResultSetConcurrency-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Resultsetparallelität für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getResultSetConcurrency()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zur Angabe des Parallelitätstyps des Resultsets.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getresultsetparallelcurrency-Methode wird von der getresultsetparallelcurrency-Methode in der Java. SQL. Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
