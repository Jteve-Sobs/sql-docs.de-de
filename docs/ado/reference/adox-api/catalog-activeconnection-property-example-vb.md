---
title: Katalog ActiveConnection-Eigenschaft – Beispiel (VB) | Microsoft-Dokumentation
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
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c6d30aeeb650525873669ccd175155c7e69cd0b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967117"
---
# <a name="catalog-activeconnection-property-example-vb"></a>Catalog ActiveConnection-Eigenschaft – Beispiel (VB)
Festlegen der [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) Eigenschaft, um eine gültige Verbindung öffnen "geöffnet" des Katalogs. Aus einem Katalog öffnen können Sie die in diesem Katalog enthaltenen Schemaobjekte zugreifen.  
  
```  
' BeginOpenConnectionVB  
Sub Main()  
    On Error GoTo OpenConnectionError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Debug.Print cat.Tables(0).Type  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
OpenConnectionError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndOpenConnectionVB  
```  
  
 Festlegen der **ActiveConnection** Eigenschaft, um eine gültige Verbindungszeichenfolge "öffnet auch" Katalog.  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type-Eigenschaft (Tabelle) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
