---
title: relative-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b2e644feff3cd2787cc6bd80bce54562ad20794
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975782"
---
# <a name="relative-method-sqlserverresultset"></a>relative-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor relativ zur aktuellen Zeile um die angegebene (positive oder negative) Anzahl von Zeilen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Parameter  
 *nRows*  
  
 Ein Wert vom Typ **int**, der die Anzahl der zu verschiebenden Zeilen angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn der Cursor in einer Zeile liegt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese relative-Methode wird von der relative-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Wenn versucht wird, den Cursor über die erste oder letzte Zeile im Resultset hinaus zu verschieben, wird er vor oder hinter der ersten bzw. letzten Reihe positioniert. Der Aufruf von `relative(0)` ist gültig, hat jedoch keine Auswirkungen auf die Position des Cursors.  
  
 Der Aufruf der Methode `relative(1)` ist mit dem Aufruf der [next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)-Methode identisch. Der Aufruf der Methode `relative(-1)` ist mit dem Aufruf der [previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)-Methode identisch.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
