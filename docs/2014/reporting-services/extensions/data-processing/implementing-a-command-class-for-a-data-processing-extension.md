---
title: Implementieren einer Command-Klasse für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ed2080a83ff83b6a6b5a5f6739d9c8bf409cdcde
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53361062"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Implementieren einer Command-Klasse für Datenverarbeitungserweiterungen
  Das **Command**-Objekt formuliert eine Anforderung und übergibt sie an die Datenquelle. Der Befehlstext kann viele verschiedene syntaktische Formate haben, einschließlich Text und XML. Wenn Ergebnisse zurückgegeben werden, gibt das **Command**-Objekt die Ergebnisse als **DataReader**-Objekt zurück.  
  
 Um eine **Command**-Klasse zu erstellen, implementieren Sie <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Implementieren Sie die <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>-Methode, um ein Resultset als **DataReader**-Objekt zurückzugeben. Die <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>-Methode Ihrer **Command**-Klasse sollte eine Implementierung enthalten, die eine <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior>-Enumeration als Argument verwendet. Wenn Sie die Datenverarbeitungserweiterungen im Berichts-Designer bereitstellen, geben Sie eine Implementierung an, die einen <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly>-Fall in der Methode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> behandelt. Eine Schema-Only-Implementierung wird verwendet, um dem Berichts-Designer eine Felderliste zur Verfügung zu stellen. Das **DataReader**-Objekt, das von der Methode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> zurückgegeben wurde, muss Typen- und Namensdaten für die Felder oder Spalten in Ihrem Resultset enthalten.  
  
 Optional kann die **Command**-Klasse <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> implementieren. Mithilfe dieser Oberfläche kann eine Implementierungsklasse eine Abfrage analysieren und eine Parameterliste in der Abfrage zurückgeben. Die Funktionen der <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>-Schnittstelle werden nur im Berichts-Designer verwendet. Wenn Sie <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> implementieren, können Benutzer des Berichts-Designers zur Eingabe von Parametern aufgefordert werden, wenn ein Bericht im Vorschaumodus ausgeführt wird. Außerdem können Sie die Parameter im Dialogfeld **Dataset** auf der Registerkarte **Parameter** anzeigen.  
  
> [!NOTE]  
>  Sie sollten <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> nicht implementieren, wenn die benutzerdefinierte Datenverarbeitungserweiterung keine Parameter unterstützt.  
  
 Eine Beispiel-**Command**-Klassenimplementierung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
