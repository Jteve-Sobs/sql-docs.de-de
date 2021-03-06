---
description: GetString-Methode (ADO)
title: GetString-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
author: rothja
ms.author: jroth
ms.openlocfilehash: ef3d32e1caae337ecb2a03bba6af8c7b4cd858de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443512"
---
# <a name="getstring-method-ado"></a>GetString-Methode (ADO)
Gibt das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt das **Recordset** als Zeichen folgen Wert **Variante** (BSTR) zurück.  
  
#### <a name="parameters"></a>Parameter  
 *StringFormat*  
 Ein [stringformatenum](../../../ado/reference/ado-api/stringformatenum.md) -Wert, der angibt, wie das **Recordset** in eine Zeichenfolge konvertiert werden soll. Die Parameter " *RowDelimiter*", " *ColumnDelimiter*" und " *nullexpr* " werden nur mit einem *StringFormat* von " **adclipstring**" verwendet.  
  
 *NumRows*  
 Optional. Die Anzahl der Zeilen, die in das **Recordset**konvertiert werden sollen. Wenn *numRows* nicht angegeben wird, oder wenn es größer als die Gesamtzahl der Zeilen im **Recordset**ist, werden alle Zeilen im **Recordset** konvertiert.  
  
 *ColumnDelimiter*  
 Optional. Ein Trennzeichen, das zwischen Spalten verwendet wird, sofern angegeben, andernfalls das Tabulator Zeichen.  
  
 *RowDelimiter*  
 Optional. Ein Trennzeichen, das zwischen Zeilen verwendet wird, sofern angegeben, andernfalls das Wagen Rücklauf Zeichen.  
  
 *Nullexpr*  
 Optional. Ein Ausdruck, der anstelle eines NULL-Werts verwendet wird, sofern angegeben, andernfalls die leere Zeichenfolge.  
  
## <a name="remarks"></a>Bemerkungen  
 Zeilendaten, aber keine Schema Daten, werden in der Zeichenfolge gespeichert. Daher kann ein **Recordset** nicht mit dieser Zeichenfolge erneut geöffnet werden.  
  
 Diese Methode entspricht der RDO **GetClipString** -Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [GetString-Methode – Beispiel (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
