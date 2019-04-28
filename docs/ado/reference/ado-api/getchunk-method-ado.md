---
title: GetChunk-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 538ccfd71375521bf0ba035ccfa55746c4d76af9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028047"
---
# <a name="getchunk-method-ado"></a>GetChunk-Methode (ADO)
Gibt alle oder einen Teil des den Inhalt der eine große Text- oder Binärdaten [Feld](../../../ado/reference/ado-api/field-object.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variant**.  
  
#### <a name="parameters"></a>Parameter  
 *Größe*  
 Ein **lange** Ausdruck, der gleich der Anzahl von Bytes oder Zeichen an, die Sie abrufen möchten.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **GetChunk** Methode für eine **Feld** Teils oder aller Daten lange Binär- oder Zeichendatentypen abzurufenden Objekts. In Situationen, in dem Systemspeicher beschränkt ist, können Sie die **GetChunk** Methode, um lange Werte in Teile, sondern in ihrer Gesamtheit zu bearbeiten.  
  
 Die Daten, die eine **GetChunk** Aufruf gibt zugewiesen *Variable*. Wenn *Größe* ist größer als die übrigen Daten, die **GetChunk** Methode gibt nur die verbleibenden Daten ohne Auffüllung *Variable* mit Leerzeichen. Wenn das Feld leer ist, ist die **GetChunk** Methode gibt einen null-Wert zurück.  
  
 Jeder nachfolgende **GetChunk** Aufruf ruft Daten ab, wo die vorherige **GetChunk** Aufruf beendet wurde. Aber wenn Sie Daten aus einem Feld aus, und klicken Sie dann festlegen oder lesen den Wert eines anderen Felds im aktuellen Datensatz abrufen, wird davon ausgegangen ADO, dass Sie das Abrufen von Daten aus dem ersten Feld abgeschlossen haben. Aufrufen der **GetChunk** Methode für das erste Feld in diesem Fall ADO interpretiert den Aufruf als eine neue **GetChunk** Vorgang und Lesen am Anfang der das beginnt. Beim Zugriff auf Felder in anderen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte, die nicht Klonen des ersten **Recordset** Objekt wird nicht unterbrochen. **GetChunk** Vorgänge.  
  
 Wenn die **AdFldLong** bit im der [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft eine **Feld** Objekt nastaven NA hodnotu **"true"**, können Sie die **GetChunk**  Methode für dieses Feld.  
  
 Wenn es kein aktueller Datensatz, ist bei der Verwendung der **GetChunk** Methode für eine **Feld** Objekt Fehler 3021 (kein aktueller Datensatz).  
  
> [!NOTE]
>  Die **GetChunk** Methode führt keine Vorgänge für **Feld** Objekte eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt. Es ist keine Vorgänge ausführen und einen Laufzeitfehler erzeugt.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AppendChunk und GetChunk-Methoden – Beispiel (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk und GetChunk-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk-Methode (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
