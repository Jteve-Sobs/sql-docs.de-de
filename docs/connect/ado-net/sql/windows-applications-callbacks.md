---
title: Verwenden von Rückrufen in Windows-Anwendungen
description: Bietet ein Beispiel, das zeigt, wie ein asynchroner Befehl sicher ausgeführt werden kann, wobei die Interaktion mit einem Formular und dessen Inhalt von einem separaten Thread ordnungsgemäß verarbeitet wird.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 5c2d46e3f2b26a8106e75f2bb116907e2f27a7b9
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451900"
---
# <a name="windows-applications-using-callbacks"></a>Verwenden von Rückrufen in Windows-Anwendungen

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

In den meisten asynchronen Verarbeitungs Szenarien möchten Sie einen Daten Bank Vorgang starten und die Ausführung anderer Prozesse fortsetzen, ohne darauf zu warten, dass der Daten Bank Vorgang beendet wird. Viele Szenarien erfordern jedoch einen Vorgang, nachdem der Daten Bank Vorgang beendet wurde. In einer Windows-Anwendung können Sie z. b. den Vorgang mit langer Laufzeit an einen Hintergrund Thread delegieren, während der Benutzeroberflächen Thread weiterhin reaktionsfähig bleibt. Wenn der Daten Bank Vorgang jedoch beendet ist, sollten Sie die Ergebnisse verwenden, um das Formular zu füllen. Diese Art von Szenario wird am besten mit einem Rückruf implementiert.  
  
Sie definieren einen Rückruf, indem Sie einen <xref:System.AsyncCallback> Delegaten in der <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>-, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>-oder <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>-Methode angeben. Der Delegat wird aufgerufen, wenn der Vorgang beendet ist. Sie können dem Delegaten einen Verweis auf die <xref:Microsoft.Data.SqlClient.SqlCommand> selbst übergeben, um den Zugriff auf das <xref:Microsoft.Data.SqlClient.SqlCommand> Objekt zu erleichtern und die entsprechende `End` Methode aufzurufen, ohne eine globale Variable verwenden zu müssen.  
  
## <a name="example"></a>Beispiel  
Die folgende Windows-Anwendung veranschaulicht die Verwendung der <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>-Methode, wobei eine Transact-SQL-Anweisung ausgeführt wird, die eine Verzögerung von einigen Sekunden umfasst (emulieren eines Befehls mit langer Ausführungszeit).  
  
In diesem Beispiel werden eine Reihe wichtiger Techniken veranschaulicht, einschließlich des Abrufens einer Methode, die mit dem Formular von einem separaten Thread interagiert. Außerdem wird in diesem Beispiel veranschaulicht, wie Sie Benutzer daran hindern müssen, einen Befehl mehrmals gleichzeitig auszuführen, und wie Sie sicherstellen müssen, dass das Formular nicht geschlossen wird, bevor die Rückruf Prozedur aufgerufen wird.  
  
Um dieses Beispiel einzurichten, erstellen Sie eine neue Windows-Anwendung. Platzieren Sie ein <xref:System.Windows.Forms.Button>-Steuerelement und zwei <xref:System.Windows.Forms.Label>-Steuerelemente auf dem Formular (übernehmen Sie für jedes Steuerelement den Standardnamen). Fügen Sie der Klasse des Formulars den folgenden Code hinzu, und ändern Sie die Verbindungs Zeichenfolge nach Bedarf für Ihre Umgebung.  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on   
// the form's design surface in Visual Studio), and then add   
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus   
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the   
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object   
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,              
    // you can retrieve it from a configuration file.   
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for   
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the   
            // SqlCommand object as the second parameter in the   
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that   
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.   
        DisplayInfoDelegate del =   
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,   
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't   
        // handle it here. You can either log the exception or   
        // invoke a delegate (as in the non-error case in this   
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a   
        // delegate as in the try block here.   
  
        // You can create the delegate instance as you   
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Asynchrone Vorgänge](asynchronous-operations.md)
