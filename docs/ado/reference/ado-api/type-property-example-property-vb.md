---
description: Type-Eigenschaft – Beispiel (Property) (VB)
title: Typeigenschafts Beispiel (Eigenschaft) (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Type property [property] [ADO], Visual Basic example
ms.assetid: 2ee8e4c5-1d66-4a77-8892-6dad7e07e611
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9c49ba9456af1f602fa5d2f399fc5172a5f1a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441692"
---
# <a name="type-property-example-property-vb"></a>Type-Eigenschaft – Beispiel (Property) (VB)
In diesem Beispiel wird die [Type](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft veranschaulicht. Es handelt sich um ein Modell eines Hilfsprogramms zum Auflisten der Namen und Typen einer Auflistung, wie z. b. [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md), [Felder](../../../ado/reference/ado-api/fields-collection-ado.md)usw.  
  
 Das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) muss nicht geöffnet werden, um auf seine **Properties** -Auflistung zuzugreifen. Sie sind vorhanden, wenn das **Recordset** -Objekt instanziiert wird. Wenn Sie jedoch die Eigenschaft " [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) " auf " **adUseClient** " festlegen, werden der **Eigenschaften** Auflistung des **Recordset** -Objekts verschiedene dynamische Eigenschaften hinzugefügt, sodass das Beispiel etwas interessanter wird. Zur Veranschaulichung verwenden wir explizit die [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft, um auf die einzelnen [Eigenschaften](../../../ado/reference/ado-api/property-object-ado.md) Objekte zuzugreifen.  
  
```  
'BeginTypePropertyVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' recordset variables  
    Dim rst As ADODB.Recordset  
    Dim prop As ADODB.Property  
     ' property variables  
    Dim ix As Integer  
    Dim strMsg As String  
  
     ' create client-side recordset  
    Set rst = New ADODB.Recordset  
    rst.CursorLocation = adUseClient  
     ' enumerate property types  
    For ix = 0 To rst.Properties.Count - 1  
        Set prop = rst.Properties.Item(ix)  
        Select Case prop.Type  
           Case adBigInt  
              strMsg = "adBigInt"  
           Case adBinary  
              strMsg = "adBinary"  
           Case adBoolean  
              strMsg = "adBoolean"  
           Case adBSTR  
              strMsg = "adBSTR"  
           Case adChapter  
              strMsg = "adChapter"  
           Case adChar  
              strMsg = "adChar"  
           Case adCurrency  
              strMsg = "adCurrency"  
           Case adDate  
              strMsg = "adDate"  
           Case adDBDate  
              strMsg = "adDBDate"  
           Case adDBTime  
              strMsg = "adDBTime"  
           Case adDBTimeStamp  
              strMsg = "adDBTimeStamp"  
           Case adDecimal  
              strMsg = "adDecimal"  
           Case adDouble  
              strMsg = "adDouble"  
           Case adEmpty  
              strMsg = "adEmpty"  
           Case adError  
              strMsg = "adError"  
           Case adFileTime  
              strMsg = "adFileTime"  
           Case adGUID  
              strMsg = "adGUID"  
           Case adIDispatch  
              strMsg = "adIDispatch"  
           Case adInteger  
              strMsg = "adInteger"  
           Case adIUnknown  
              strMsg = "adIUnknown"  
           Case adLongVarBinary  
              strMsg = "adLongVarBinary"  
           Case adLongVarChar  
              strMsg = "adLongVarChar"  
           Case adLongVarWChar  
              strMsg = "adLongVarWChar"  
           Case adNumeric  
              strMsg = "adNumeric"  
           Case adPropVariant  
              strMsg = "adPropVariant"  
           Case adSingle  
              strMsg = "adSingle"  
           Case adSmallInt  
              strMsg = "adSmallInt"  
           Case adTinyInt  
              strMsg = "adTinyInt"  
           Case adUnsignedBigInt  
              strMsg = "adUnsignedBigInt"  
           Case adUnsignedInt  
              strMsg = "adUnsignedInt"  
           Case adUnsignedSmallInt  
              strMsg = "adUnsignedSmallInt"  
           Case adUnsignedTinyInt  
              strMsg = "adUnsignedTinyInt"  
           Case adUserDefined  
              strMsg = "adUserDefined"  
           Case adVarBinary  
              strMsg = "adVarBinary"  
           Case adVarChar  
              strMsg = "adVarChar"  
           Case adVariant  
              strMsg = "adVariant"  
           Case adVarNumeric  
              strMsg = "adVarNumeric"  
           Case adVarWChar  
              strMsg = "adVarWChar"  
           Case adWChar  
              strMsg = "adWChar"  
           Case Else  
              strMsg = "*UNKNOWN*"  
        End Select  
            'show results  
        Debug.Print "Property " & ix & ": " & prop.Name & _  
                    ", Type = " & strMsg  
    Next ix  
  
    ' clean up  
    Set rst = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    Set rst = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndTypePropertyVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)   
 [Type-Eigenschaft (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
