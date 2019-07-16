---
title: DataSource-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd677e29631e53eeb71c43e8174baff553defc85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933249"
---
# <a name="datasource-property-ado"></a>DataSource-Eigenschaft (ADO)
Gibt ein Objekt, das Daten als dargestellt werden enthält eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft wird verwendet, um datengebundene Steuerelemente mit der Data-Umgebung zu erstellen. Die Data-Umgebung verwaltet, Auflistungen von Daten (Datenquellen), enthält benannte Objekte (Datenmember), die als dargestellt werden ein **Recordset** Objekt.  
  
 Die [DataMember](../../../ado/reference/ado-api/datamember-property.md) und **DataSource** Eigenschaften müssen zusammen verwendet werden.  
  
 Das referenzierte Objekt implementieren muss die **IDataSource** -Schnittstelle und enthalten eine **IRowset** Schnittstelle.  
  
## <a name="usage"></a>Verwendung  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataMember-Eigenschaft](../../../ado/reference/ado-api/datamember-property.md)
