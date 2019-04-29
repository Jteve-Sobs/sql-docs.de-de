---
title: Ausführen von SQL-Abfragen (SQLXML verwaltete Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 80e1574d6cee00e72d9aa421394bc8586e410dbd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127685"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a>Ausführen von SQL-Abfragen (verwaltete SQLXML-Klassen)
  Dieses Beispiel zeigt:  
  
-   Erstellen von Parametern (SqlXmlParameter-Objekte).  
  
-   Zuweisen von Werten an den Eigenschaften der SqlXmlParameter-Objekte (Name und Wert).  
  
 In diesem Beispiel wird eine einfache SQL-Abfrage ausgeführt, um Vornamen, Nachnamen und Geburtsdatum des Mitarbeiters abzufragen, dessen Nachname als Parameterwert übergeben wird. Angeben des Parameters (*"LastName"*), nur die Value-Eigenschaft festgelegt ist. Die Name-Eigenschaft ist nicht festgelegt, da in dieser Abfrage um einen Positionsparameter handelt und kein Name erforderlich ist.  
  
 Die CommandType-Eigenschaft des SqlXmlCommand-Objekt, in der Standardeinstellung ist **Sql**. Deshalb wird die Eigenschaft nicht explizit festgelegt.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
 Dies ist der C#-Code.  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
         }  
  
         return 0;  
   }  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Speichern Sie den in diesem Thema bereitgestellten C#-Code (DocSample.cs) in einem Ordner.  
  
2.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
3.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  
  
 Um das Beispiel zu testen, muss auf dem Computer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installiert sein.  
  
 Statt die SQL-Abfragen als Befehlstext anzugeben, können Sie eine Vorlage festlegen (wie im folgenden Codefragment dargestellt), die ein Updategram ausführt (ebenfalls eine Vorlage), um einen Kundendatensatz einzufügen. Sie können Vorlagen und Updategrams in Dateien angeben und Dateien ausführen. Weitere Informationen finden Sie unter [Ausführen von Vorlagendateien mit der CommandText-Eigenschaft](executing-template-files-by-using-the-commandtext-property.md).  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a>Verwenden von ExecuteToStream  
 Wenn Sie einen vorhandenen Datenstrom haben, können Sie die ExecuteToStream-Methode, statt ein Stream-Objekt erstellt und die Execute-Methode. Der Code aus dem vorherigen Beispiel wird hier überarbeitet, um ExecuteToStream-Methode verwenden:  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  Sie können auch die ExecuteXMLReadermethod verwenden, die ein XmlReader-Objekt zurückgibt. Weitere Informationen finden Sie unter [Ausführen von SQL-Abfragen mithilfe der "ExecuteXMLReader"-Methode](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
  
