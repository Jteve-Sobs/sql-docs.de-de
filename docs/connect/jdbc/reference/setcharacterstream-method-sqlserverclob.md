---
title: setCharacterStream-Methode (SQLServerClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b4edd69c4712c1842163bcb48797edc154cc5cf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929022"
---
# <a name="setcharacterstream-method-sqlserverclob"></a>setCharacterStream-Methode (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Datenstrom zurück, der verwendet wird, um ab der angegebenenPosition einen Unicode-Zeichendatenstrom in das CLOB zu schreiben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Die Position, an der Daten in das CLOB-Objekt geschrieben werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Datenstrom, in den Unicode-codierte Zeichen geschrieben werden können.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCharacterStream-Methode wird von der setCharacterStream-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
 Zeichendaten im CLOB werden beginnend mit der angegebenen Position vom Schreiber überschrieben, und sie können die ursprüngliche Länge des CLOB übersteigen. Durch Angeben eines Werts vom Typ Position+1 werden Zeichen angefügt. Durch Angeben eines Werts vom Typ Position+2 oder größer (oder null oder weniger) wird ein Positionsfehler ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
