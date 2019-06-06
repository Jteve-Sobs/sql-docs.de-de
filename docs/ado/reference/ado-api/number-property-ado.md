---
title: Number-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4ef1665bf96688fba5fc7d157b73d2df2fcd2c68
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705608"
---
# <a name="number-property-ado"></a>Number-Eigenschaft (ADO)
Gibt die Anzahl, die eindeutig eine [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** -Wert, der auf einen der entsprechen unter Umständen die [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) Konstanten.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Anzahl** Eigenschaft, um zu bestimmen, welcher Fehler aufgetreten ist. Der Wert der Eigenschaft ist eine eindeutige Zahl, die die fehlerbedingung entspricht.  
  
 Die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung gibt ein HRESULT zurück, im hexadezimalen Format (z. B. 0 x 80004005) oder long-Wert (z. B. 2147467259). Diese HRESULTs können von zugrunde liegenden Komponenten, z. B. OLE DB oder sogar OLE selbst ausgelöst werden. Weitere Informationen zu diesen Zahlen finden Sie unter [Fehler (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) in die [OLE DB-Programmierreferenz](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) *.*  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description-Eigenschaft](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext-und HelpFile-Eigenschaft](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
