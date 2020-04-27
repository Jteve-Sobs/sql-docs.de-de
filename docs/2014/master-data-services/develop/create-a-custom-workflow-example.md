---
title: Beispiel für einen benutzerdefinierten Workflow (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 84e4dccb97b045e5077d75c4280cee066a154d5b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483053"
---
# <a name="custom-workflow-example-master-data-services"></a>Beispiel für einen benutzerdefinierten Workflow (Master Data Services)
  Bei der Erstellung einer Klassenbibliothek für einen benutzerdefinierten Workflow in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] erstellen Sie eine Klasse, die die <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>-Schnittstelle implementiert. Diese Schnittstelle beinhaltet eine Methode, <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, die beim Start eines Workflows vom SQL Server MDS Workflow Integration Service aufgerufen wird. Die <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>-Methode enthält zwei Parameter: *workflowType* enthält den Text, den Sie in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in das Textfeld **Workflowtyp** eingegeben haben, und *dataElement* enthält Metadaten sowie Elementdaten für das Element, das die Workflowgeschäftsregel ausgelöst hat.  
  
## <a name="custom-workflow-example"></a>Beispiel für einen benutzerdefinierten Workflow  
 Das folgende Codebeispiel veranschaulicht die Implementierung der <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>-Methode zum Extrahieren der Namens-, Code- und LastChgUserName-Attribute von den XML-Daten für das Element, das die Workflowgeschäftsregel ausgelöst hat. Zudem erfahren Sie, wie eine gespeicherte Prozedur zum Einfügen der Attribute in eine andere Datenbank aufgerufen wird. Ein Beispiel für die Elementdaten-XML und eine Erläuterung der enthaltenen Tags finden Sie unter [Benutzerdefinierte Workflow-XML-Beschreibung &#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Workflows &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md)  
  
  
