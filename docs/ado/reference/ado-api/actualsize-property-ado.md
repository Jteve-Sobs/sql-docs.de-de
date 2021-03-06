---
description: ActualSize-Eigenschaft (ADO)
title: ActualSize-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: rothja
ms.author: jroth
ms.openlocfilehash: 53384838d53003f0c4f81ec3b629e987ce2649a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451632"
---
# <a name="actualsize-property-ado"></a>ActualSize-Eigenschaft (ADO)
Gibt die tatsächliche Länge des Werts eines Felds in Bytes an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Gibt einen **Long** -Wert zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **ActualSize** -Eigenschaft, um die tatsächliche Länge des Werts eines [Feld](../../../ado/reference/ado-api/field-object.md) Objekts zurückzugeben. Die **ActualSize** -Eigenschaft ist für alle Felder schreibgeschützt. Wenn ADO die Länge des **Feld** Objekt Werts nicht ermitteln kann, gibt die **ActualSize** -Eigenschaft **adunknown**zurück.  
  
 Die Eigenschaften **ActualSize** und [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) sind unterschiedlich, wie im folgenden Beispiel gezeigt. Ein **Feld** Objekt mit einem deklarierten Typ von **adVarChar** und eine maximale Länge von 50 Zeichen gibt einen **DefinedSize** -Eigenschafts Wert von 50 zurück, aber der Rückgabewert der **ActualSize** -Eigenschaft ist die Länge der Daten, die im Feld für den aktuellen Datensatz gespeichert sind. **Felder** mit einer **DefinedSize** größer als 255 Bytes werden als Spalten variabler Länge behandelt.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActualSize und DefinedSize-Eigenschaften (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Beispiel für ActualSize und DefinedSize-Eigenschaften (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize-Eigenschaft](../../../ado/reference/ado-api/definedsize-property.md)
