---
description: Eigenschaften von "AbsolutePosition" und "Cursor Location" (JScript)
title: Eigenschaften von "AbsolutePosition" und "Cursor Location" (JScript) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- AbsolutePosition property [ADO], JScript example
- CursorLocation property [ADO], JScript example
ms.assetid: bff98617-a6ba-4f41-9c5f-915161e3ea31
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e1840f567cf4d1285aa7257081f9dfc9d48a4bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451782"
---
# <a name="absoluteposition-and-cursorlocation-properties-example-jscript"></a>Eigenschaften von "AbsolutePosition" und "Cursor Location" (JScript)
In diesem Beispiel wird veranschaulicht, wie die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) -Eigenschaft den Fortschritt einer Schleife verfolgen kann, in der alle Datensätze eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)aufgelistet werden. Er verwendet die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft, um die **AbsolutePosition** -Eigenschaft zu aktivieren, indem der Cursor auf einen Client Cursor festgelegt wird. Schneiden Sie den folgenden Code aus, und fügen Sie ihn in Editor oder einen anderen Text-Editor ein, und speichern Sie ihn als **AbsolutePositionJS. ASP**.  
  
```  
<!-- BeginAbsolutePositionJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
  
<head>  
<title>AbsolutePosition and CursorLocation Properties Example (JScript)</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>AbsolutePosition and CursorLocation Properties Example (JScript)</h1>  
<%  
    // connection and recordset variables  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsEmployee = Server.CreateObject("ADODB.Recordset");  
        // display string  
    var strMessage;          
  
    try  
    {  
        // Open a recordset on the Employee table using  
        // a client-side cursor to enable AbsolutePosition property.  
        rsEmployee.CursorLocation = adUseClient;  
        rsEmployee.Open("employees", strCnxn, adOpenStatic, adLockOptimistic, adCmdTable);  
  
        // Write beginning of table to the document.  
        Response.Write('<table border="0" align="center">');  
        Response.Write('<tr class="thead2">');  
        Response.Write("<th>AbsolutePosition</th><th>Name</th><th>Hire Date</th></tr>");  
  
        while (!rsEmployee.EOF)  
        {  
            strMessage = "";  
  
            // Start a new table row.  
            strMessage = '<tr class="tbody">';  
  
            // First column in row contains AbsolutePosition value.  
            strMessage += "<td>" + rsEmployee.AbsolutePosition + " of " + rsEmployee.RecordCount + "</td>"  
  
            // First and last name are in first column.  
            strMessage += "<td>" + rsEmployee.Fields("FirstName") + " ";  
            strMessage += rsEmployee.Fields("LastName") + " " + "</td>";  
  
            // Hire date in second column.  
            strMessage += "<td>" + rsEmployee.Fields("HireDate") + "</td>";  
  
            // End the row.  
            strMessage += "</tr>";  
  
            // Write line to document.  
            Response.Write(strMessage);  
  
            // Get next record.  
            rsEmployee.MoveNext;  
        }  
  
        // Finish writing document.  
        Response.Write("</table>");  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // 'clean up  
        if (rsEmployee.State == adStateOpen)  
            rsEmployee.Close;  
        rsEmployee = null;  
    }  
%>  
  
</html>  
<!-- EndAbsolutePositionJS -->  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Cursor Location-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
