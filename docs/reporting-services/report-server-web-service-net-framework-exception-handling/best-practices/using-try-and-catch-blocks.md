---
title: Verwenden von „Try und Catch“-Blöcken | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine weitere Schutzschicht vor ungültigen Anforderungen bereitstellen, indem Sie angebrachte Ausnahmebehandlung mithilfe von Try/Catch-Blöcken anwenden.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51f6c4d3cbc7751df8e7685835057c4c5e58daa9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216356"
---
# <a name="using-try-and-catch-blocks"></a>Verwenden von „Try und Catch“-Blöcken
  Nachdem Sie ungültige Anforderungen an den Berichtsserver eingeschränkt haben, indem Sie bedingte Anweisungen zum Code hinzugefügt haben, sollten Sie mithilfe von try/catch-Blöcken eine adäquate Ausnahmebehandlung festlegen. Diese Technik stellt eine weitere Stufe des Schutzes gegen ungültige Anforderungen dar. Wenn eine Anforderung an den Berichtsserver in einem try-Block enthalten ist und diese Anforderung dazu führt, dass der Berichtsserver eine Ausnahme auslöst, wird die Ausnahme im catch-Block erfasst. Damit wird ein unerwarteter Abbruch Ihrer Anwendung verhindert. Sobald die Ausnahme erfasst ist, können Sie den Benutzer mit der Ausnahme anweisen, einen anderen Vorgang auszuführen, oder Sie teilen ihm einfach auf freundliche Weise mit, dass ein Fehler aufgetreten ist. Sie können dann einen finally-Block verwenden, um einen Cleanup vorhandener Ressourcen durchzuführen. Idealerweise sollten Sie einen Plan für die allgemeine Ausnahmebehandlung generieren, um eine unnötige Verdoppelung von try/catch-Blöcken zu vermeiden.  
  
 Im folgenden Beispiel werden try/catch-Blöcke verwendet, um die Zuverlässigkeit des Ausnahmebehandlungscodes zu verbessern.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException Class (Reporting Services-SoapException-Klasse)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
