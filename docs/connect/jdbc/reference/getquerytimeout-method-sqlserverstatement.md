---
title: getquerytimeout-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fd4d7b32c9480fec28e20a9dcbc9c22530eb4a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980642"
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>getQueryTimeout-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Anzahl von Sekunden ab, die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] auf die Ausführung dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts gewartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, der die Wartezeit des JDBC-Treibers in Sekunden angibt, oder „0“, wenn kein Limit vorhanden ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getquerytimeout-Methode wird von der getquerytimeout-Methode in der Java. SQL. Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
