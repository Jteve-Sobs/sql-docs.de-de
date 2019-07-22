---
title: Position-Methode (Byte, Long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf8cfa3bb6aed74c7689639698715dc24803d46d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976476"
---
# <a name="position-method-byte-long"></a>position-Methode (byte, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die Position eines angegebenen Musters im BLOB auf der Grundlage des angegebenen **Bytearray**-Musters und des Startindexes zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *bPattern*  
  
 Das zu suchende Muster.  
  
 *start*  
  
 Der Startindex, in dem gesucht werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **long** der Position, an der das Muster gefunden wurde oder „-1“, wenn es nicht gefunden wurde.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Positions Methode wird von der Positions Methode in der Java. SQL. BLOB-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Positions Methode &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
