---
title: JScript-Codebeispiel zum Zurückgeben eines Recordsets | Microsoft-Dokumentation
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
- Recordset [ADO]
ms.assetid: 74aad8a6-06cc-4a2c-811a-d78f9b741d84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dc86d8f454b67c00073508a4ed6d7e8fc0d033e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161459"
---
# <a name="jscript-code-example-to-return-a-recordset"></a>JScript-Codebeispiel zum Zurückgeben eines Recordsets
## <a name="jscript-code-rsjs"></a>JScript-Code (rs.js)  
  
```  
main();  
  
function main()  
{  
  DP = "SQLOLEDB";  
  DS = "MySQLServer";  
  DB = "NORTHWIND";  
  
  adOpenForwardOnly = 0;  
  adLockReadOnly = 1;  
  adCmdText = 1;  
  try   
  {  
    var objRs = new ActiveXObject("ADODB.Recordset");  
  }  
  catch (e)  
  {  
    alert("ADODB namespace not found.");  
    exit(0);  
  }  
  
  strConn =  "Provider="         +DP+  
            ";Initial Catalog="  +DB+  
            ";Data Source="      +DS+  
            ";Integrated Security=SSPI;"  
  strComm = "SELECT ProductID,ProductName,UnitPrice "+  
            "FROM Products " +   
            "WHERE CategoryID = 7"  // select Produce  
  
  objRs.open(strComm,   
             strConn,   
             adOpenForwardOnly,  
             adLockReadOnly,  
             adCmdText);  
  
  objRs.MoveFirst();  
  while (objRs.EOF != true)   
  {  
    alert(objRs("ProductID")+"\t"  
         +objRs("ProductName")+"\t"  
         +objRs("UnitPrice"));  
    objRs.MoveNext();  
  }  
  
  objRs.Close  
  objRs = null;  
}  
  
function alert(str)  
{  
  WScript.Echo(str);  
}  
```  
  
#### <a name="try-it"></a>Versuch es!  
  
1.  Speichern Sie den Code oben in eine Textdatei ein. Speichern Sie die Datei als rs.js.  
  
2.  Öffnen Sie eine Eingabeaufforderung und die cd in das Verzeichnis, in dem Sie die JScript-Datei (rs.js) gespeichert haben.  
  
3.  Typ `CScript rs.js` von der Befehlszeile aus.
