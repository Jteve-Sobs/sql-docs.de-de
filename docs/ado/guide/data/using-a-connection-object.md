---
description: Verwenden eines Connection-Objekts
title: Verwenden eines Verbindungs Objekts | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3041abc535557f9f92e3a994d536fb07abde8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452622"
---
# <a name="using-a-connection-object"></a>Verwenden eines Connection-Objekts
Vor dem Öffnen eines **Verbindungs** Objekts müssen Sie bestimmte Informationen über die Datenquelle und den Verbindungstyp definieren. Die meisten dieser Informationen werden durch den *ConnectionString* -Parameter der [Open-Methode](../../../ado/reference/ado-api/open-method-ado-connection.md) für das **Verbindungs** Objekt oder durch die [ConnectionString-Eigenschaft](../../../ado/reference/ado-api/connectionstring-property-ado.md) des **Connection** -Objekts gespeichert. Eine Verbindungs Zeichenfolge besteht aus einer Liste von Argument/Wert-Paaren, die durch Semikolons getrennt sind, wobei die Werte in einfache Anführungszeichen eingeschlossen sind. Beispiel:  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Sie können auch einen ODBC-Datenquellen Namen (DSN) oder eine Daten Verknüpfungs Datei (UDL-Datei) in einer Verbindungs Zeichenfolge angeben. Weitere Informationen zu DSNs finden Sie unter [Verwalten von Datenquellen](../../../odbc/admin/managing-data-sources.md) in der ODBC Programmer es Reference. Weitere Informationen zu UDLs finden Sie unter [Übersicht über die Daten Link-API](https://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc) in der OLE DB Programmierer-Referenz.  
  
 In der Regel stellen Sie eine Verbindung her, indem Sie die **Connection. Open** -Methode mit einer entsprechenden *Verbindungs Zeichenfolge* als Parameter aufrufen. Ein Beispiel finden Sie im folgenden Visual Basic-Code Ausschnitt:  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Hier übernimmt " **ORS. Open** " eine " **Connection** Object"-Variable (*oconn*) als Wert Ihres *ActiveConnection* -Parameters. Außerdem wird von der **Connection. Cursor Location** -Eigenschaft der Standardwert **AD-eServer**angenommen. Vergleichen Sie dies mit dem [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) -Beispiel im vorherigen Abschnitt. Die folgende Anweisung würde zu Laufzeitfehlern führen.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
