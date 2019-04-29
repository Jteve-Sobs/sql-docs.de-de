---
title: Zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4d4235b86669ad6baff481d9e69166b9f22fcf26
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127636"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a>Zugreifen auf die SQLXML-Funktionalität in der .NET-Umgebung
  In diesem Beispiel wird dargestellt:  
  
-   Gewusst wie: Verwenden Sie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] verwaltete SQLXML-Klassen (Microsoft.Data.SqlXml) auf Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Umgebung.  
  
-   wie DiffGram-Objekte, die in der .NET Framework-Umgebung generiert werden, Datenupdates auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen anwenden können.  
  
 In dieser Anwendung wird eine XPath-Abfrage für ein XSD-Schema ausgeführt. Die Ausführung der XPath-Abfrage gibt ein XML-Dokument, das aus Kontaktdaten besteht (**FirstName**, **"LastName"**). Die Anwendung lädt das XML-Dokument in das Dataset der .NET Framework-Umgebung. Die Daten im Dataset werden bearbeitet: Der Vorname des ersten Kontakts im Dataset wird in "Susan" geändert. Das DiffGram-Objekt wird aus dem Dataset erstellt, und das im DiffGram-Objekt angegebene Update (die Änderung des Vornamens der Mitarbeiterin) auf die Person.Contact-Tabelle angewendet.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
 **So testen Sie das Beispiel:**  
  
 Um das Beispiel zu testen, muss auf dem Computer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installiert sein.  
  
1.  Speichern Sie dieses XSD-Schema (MySchema.xml) in einem Ordner:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Con" sql:relation="Person.Contact" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="FName"    
                         sql:field="FirstName"   
                         type="xsd:string" />   
            <xsd:element name="LName"    
                         sql:field="LastName"    
                         type="xsd:string" />  
         </xsd:sequence>  
         <xsd:attribute name="ContactID" type="xsd:integer" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
2.  Speichern Sie den C#-Code (DocSample.cs) aus dem Beispiel im selben Ordner, in dem das Schema gespeichert ist. (Wenn Sie die Dateien in einem anderen Ordner speichern, müssen Sie den Code bearbeiten und den entsprechenden Verzeichnispfad für das Zuordnungsschema angeben.)  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
 Führen Sie DocSample.exe an der Eingabeaufforderung aus.  
  
  
