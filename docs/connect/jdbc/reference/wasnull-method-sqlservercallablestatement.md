---
title: WasNull-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.wasNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a27b2fe-ae12-46a9-9bca-2c5ca66b9eb3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4e92dd2dc10566961dd037b182c9b33f2c564ca6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802517"
---
# <a name="wasnull-method-sqlservercallablestatement"></a>wasNull-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob der letzte gelesene OUT-Parameter den Wert "SQL NULL" besaß.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean wasNull()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn der letzte Parameter schreibgeschützt war null. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese wasNull-Methode wird von der wasNull-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
