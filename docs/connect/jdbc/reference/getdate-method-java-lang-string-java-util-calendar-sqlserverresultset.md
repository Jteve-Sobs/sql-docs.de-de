---
title: GetDate-Methode (java.util.Calendar) Spalte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3fa2a72a-7499-44ec-8f76-a8e646e0190c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 13104a29fe8568ade732faf9ed05a05a42b4d093
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66785595"
---
# <a name="getdate-method-javalangstring-javautilcalendar-sqlserverresultset"></a>getDate-Methode (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des Calendar-Objekts den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Date-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Date getDate(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *colName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *cal*  
  
 Ein Kalenderobjekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Date-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getDate-Methode wird von der getDate-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Datumsteil eines datetime- oder smalldatetime-Datentyps von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben. Der Zeitteil ist dabei in der im Kalender angegebenen Zeitzone auf die Java-Baseline 00:00 (Mitternacht) festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getDate-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
