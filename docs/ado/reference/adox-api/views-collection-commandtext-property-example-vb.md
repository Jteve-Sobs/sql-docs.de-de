---
title: Zeigt die Auflistung, die CommandText-Eigenschaft – Beispiel (VB) | Microsoft-Dokumentation
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
- CommandText property [ADOX]
- Views collection [ADOX], Visual Basic example
ms.assetid: a05a0190-352d-44ff-9488-0c94e9fb656e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13dc0a46daa2636dc56cf84f91ad8d014c4a3bdb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281355"
---
# <a name="views-collection-commandtext-property-example-vb"></a>Views-Collection, CommandText-Eigenschaft – Beispiel (VB)
Der folgende Code veranschaulicht, wie die [Befehl](../../../ado/reference/adox-api/command-property-adox.md) Eigenschaft, um den Text einer Ansicht zu aktualisieren.  
  
```  
' BeginViewsCollectionVB  
Sub Main()  
    On Error GoTo ViewTextError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim cmd As New ADODB.Command  
  
    ' Open the connection.  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Open the catalog.  
    Set cat.ActiveConnection = cnn  
  
    ' Get the command.  
    Set cmd = cat.Views("AllCustomers").Command  
  
    ' Update the CommandText of the command.  
    cmd.CommandText = _  
    "Select CustomerId, CompanyName, ContactName From Customers"  
  
    ' Update the view.  
    Set cat.Views("AllCustomers").Command = cmd  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ViewTextError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndViewsCollectionVB  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Command-Eigenschaft (ADOX)](../../../ado/reference/adox-api/command-property-adox.md)   
 [Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
