---
title: SqlDataRecord-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlDataRecord object
- custom result sets [CLR integration]
ms.assetid: 2ed667fb-749c-4280-a8fb-650643683c8f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c688d41a1f27c6f3d620e9395d2a908d9b9cddd1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874682"
---
# <a name="sqldatarecord-object"></a>SqlDataRecord-Objekt
  Das `SqlDataRecord`-Objekt stellt eine einzelne Zeile der Daten mit den zugehörigen Metadaten dar.  
  
 Verwaltete gespeicherte Prozeduren können Resultsets an den Client senden, die nicht von `SqlDataReader` stammen. Die `SqlDataRecord`-Klasse ermöglicht zusammen mit den Methoden `SendResultsStart`, `SendResultsRow` und `SendResultsEnd` des `SqlPipe`-Objekts gespeicherten Prozeduren, benutzerdefinierte Resultsets an den Client zu senden.  
  
 Weitere Informationen finden Sie in der Referenz zu der `Microsoft.SqlServer.Server.SqlDataRecord`-Klasse und in der .NET Framework SDK-Dokumentation.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt einen neuen Mitarbeiterdatensatz und gibt ihn an den Aufrufer zurück.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void CreateNewRecordProc()  
{  
    // Variables.         
    SqlDataRecord record;  
  
    // Create a new record with the column metadata.  The constructor   
    // is able to accept a variable number of parameters.  
    record = new SqlDataRecord(new SqlMetaData("EmployeeID", SqlDbType.Int),  
                               new SqlMetaData("Surname", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("GivenName", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("StartDate", SqlDbType.DateTime) );  
  
    // Set the record fields.  
    record.SetInt32(0, 0042);  
    record.SetString(1, "Funk");  
    record.SetString(2, "Don");  
    record.SetDateTime(3, new DateTime(2005, 7, 17));  
  
    // Send the record to the calling program.  
    SqlContext.Pipe.Send(record);  
  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  CreateNewRecordVBProc ()  
    ' Variables.  
    Dim record As SqlDataRecord  
  
    ' Create a new record with the column metadata. The constructor is   
    ' able to accept a variable number of parameters  
  
    record = New SqlDataRecord(New SqlMetaData("EmployeeID", SqlDbType.Int), _  
                           New SqlMetaData("Surname", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("GivenName", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("StartDate", SqlDbType.DateTime))  
  
    ' Set the record fields.  
    record.SetInt32(0, 42)  
    record.SetString(1, "Funk")  
    record.SetString(2, "Don")  
    record.SetDateTime(3, New DateTime(2005, 7, 17))  
  
    ' Send the record to the calling program.  
    SqlContext.Pipe.Send(record)  
  
End Sub  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlPipe-Objekt](sqlpipe-object.md)  
  
  
