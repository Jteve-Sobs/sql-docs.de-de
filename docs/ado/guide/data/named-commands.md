---
description: Benannte Befehle
title: Benannte Befehle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO]
ms.assetid: 5a0ec8f9-5ba3-4f9f-b80d-2073aa049586
author: rothja
ms.author: jroth
ms.openlocfilehash: 607142ec89a1032fe42bab87c0dfad0f2a276387
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453152"
---
# <a name="named-commands"></a>Benannte Befehle
Beim [Erstellen und Ausführen eines einfachen Befehls](../../../ado/guide/data/creating-and-executing-a-simple-command.md) wird eine Möglichkeit zum Ausführen eines Befehls angezeigt. Es gibt eine weitere Möglichkeit: Sie können einen benannten Befehl erstellen und dann den benannten Befehl direkt für das **Verbindungs** Objekt (zugewiesen an die **ActiveConnection** -Eigenschaft des **Command** -Objekts) aufzurufen. Das Benennen eines Befehls bedeutet, dass der **Name** -Eigenschaft eines **Befehls** Objekts ein Name zugewiesen wird. Beispiel:  
  
```  
objCmd.Name = "GetCustomers"  
objCmd.ActiveConnection = objConn  
objConn.GetCustomers objRs  
```  
  
 Der benannte Befehl verhält sich wie eine "benutzerdefinierte Methode" für das **Verbindungs** Objekt. Das Ergebnis des Befehls wird als out-Parameter dieser "benutzerdefinierten Methode" zurückgegeben.  
  
 Dieses Feature wird im folgenden Beispiel veranschaulicht.  
  
```  
'BeginNamedCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objRs As New ADODB.Recordset  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
  
    objCmd.CommandText = "SELECT CustomerID, CompanyName FROM Customers"  
    objCmd.CommandType = adCmdText  
  
    'Name the command.  
    objCmd.Name = "GetCustomers"  
  
    objCmd.ActiveConnection = objConn  
  
    ' Execute using Command.Name from the Connection.  
    objConn.GetCustomers objRs  
  
    ' Display.  
    Do While Not objRs.EOF  
        Debug.Print objRs(0) & vbTab & objRs(1)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndNamedCmd  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
