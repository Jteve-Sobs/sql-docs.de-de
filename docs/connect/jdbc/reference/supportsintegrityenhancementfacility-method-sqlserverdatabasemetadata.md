---
title: SupportsIntegrityEnhancementFacility-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsIntegrityEnhancementFacility
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: edee084b-9a8c-4167-9e13-66fc3ed1ecaa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1e841d3b6999d6852dc9b792fb55ffdd94195e3a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764286"
---
# <a name="supportsintegrityenhancementfacility-method-sqlserverdatabasemetadata"></a>supportsIntegrityEnhancementFacility-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank die SQL-Integritätserweiterungsfunktion unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsIntegrityEnhancementFacility()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SupportsIntegrityEnhancementFacility-Methode wird von der SupportsIntegrityEnhancementFacility-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
