---
title: getFetchDirection-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73a507e48b4ecc7f1ead7e33fe6936f5ed73f424
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924838"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Abrufrichtung für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der aktuellen Abrufrichtung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getFetchDirection-Methode wird von der getFetchDirection-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird FETCH_FORWARD für schreibgeschützte Vorwärtscursor zurückgegeben, die letzte Einstellung, die durch einen Aufruf der [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)-Methode für andere Cursortypen vorgenommen wurde. Wenn die setFetchDirection-Methode niemals aufgerufen wurde, wird für diese Cursortypen FETCH_UNKNOWN zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
