---
title: Seek-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 21cb7f8773c0663d584f62bcaaaeab15c7eac108
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711422"
---
# <a name="seek-method"></a>Seek-Methode
Sucht den Index einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , schnell die Zeile, die mit den angegebenen Werten übereinstimmt, und die aktuelle Zeilenposition Zeile ändert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Parameter  
 *KeyValues*  
 Ein Array von **Variant** Werte. Ein Index besteht aus einer oder mehreren Spalten und das Array enthält einen Wert, für jede einzelne Spalte verglichen werden soll.  
  
 *SeekOption*  
 Ein [SeekEnum](../../../ado/reference/ado-api/seekenum.md) Wert, der angibt, den Typ des Vergleichs zwischen den Spalten des Indexes und den entsprechenden erfolgen *KeyValues*.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Seek** -Methode in Verbindung mit der [Index](../../../ado/reference/ado-api/index-property.md) Eigenschaft, wenn der zugrunde liegenden Anbieter Indizes auf unterstützt die **Recordset** Objekt. Verwenden der [unterstützt](../../../ado/reference/ado-api/supports-method.md) **(AdSeek)** Methode, um zu bestimmen, ob der zugrunde liegenden Anbieter unterstützt **Seek**, und die **Supports(adIndex)** Methode, um zu bestimmen, ob der Anbieter Indizes unterstützt. (Z. B. die [OLE DB-Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) unterstützt **Seek** und **Index**.)  
  
 Wenn **Seek** befindet sich nicht gefunden werden der gewünschten Zeile, kein Fehler auftritt, und für die Zeile am Ende der **Recordset**. Legen Sie die **Index** Eigenschaft, um den gewünschten Index vor dem Ausführen dieser Methode.  
  
 Diese Methode wird nur mit serverseitiger Cursor unterstützt. Suche wird nicht unterstützt, wenn die **Recordset** des Objekts [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaftswert ist **AdUseClient**.  
  
 Diese Methode ist nur möglich verwendet werden, wenn die **Recordset** Objekt mit geöffnet wurde eine [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Wert **AdCmdTableDirect**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Seek-Methode und Index-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Seek-Methode und Index-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find-Methode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index-Eigenschaft](../../../ado/reference/ado-api/index-property.md)
