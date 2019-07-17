---
title: Verwaltete SQLXML-Klassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 562b75d19715c0cf52cf8eeaf499f142a2b27080
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119609"
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>SQLXML 4.0 .NET Framework-Unterstützung – Verwaltete Klassen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt Funktionen, mit denen Sie Anwendungen schreiben können, um von einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz auf XML-Daten zuzugreifen, um die Daten in die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Umgebung einzubinden, um die Daten zu verarbeiten und um die Aktualisierungen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückzusenden. 
  
  Verwaltete [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML-Klassen machen die Funktionalität von SQLXML 4.0 im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework verfügbar. Mit verwalteten SQLXML-Klassen können Sie eine Anwendung in C# schreiben, um von einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz auf XML-Daten zuzugreifen, die Daten in die .NET Framework-Umgebung einzubinden, die Daten zu verarbeiten und die Updates zur Anwendung als DiffGram an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückzusenden. Beim Anwenden von Updates auf eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank, die verwaltete SQLXML-Klassen verwendet, müssen Sie ein Zuordnungsschema verwenden. Ein Arbeitsbeispiel finden Sie unter [zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Um die verwalteten SQLXML-Klassen mit SQLXML 4.0 zu verwenden, müssen Sie Microsoft Visual Studio installieren.  
  
> [!NOTE]  
>  .NET Framework umfasst den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET-Datenanbieter. Mit diesem Anbieter kann von der .NET-Umgebung auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zugegriffen werden. Allerdings kann er nur herkömmliche SQL-Abfragen verarbeiten (d. h. Abfragen relationaler Datenbanken mit Ausnahme von FOR XML-Abfragen). Sie können weder XML-Vorlagen noch serverseitige XPath-Abfragen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausführen.  

 Informationen zum Zugreifen auf und Ändern von Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] innerhalb der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework sowie Informationen zur Verwendung von DiffGrams zum Aktualisieren von Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabellen finden Sie unter [zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  Sie können außerdem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio-Anwendungen schreiben, um einen Massenladenvorgang für XML-Dokumente mit XML-Massenladen auszuführen. Weitere Informationen finden Sie unter [Ausführen von Massenladen von XML von Daten &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md). Sie müssen einen Verweis auf die XML-Massenladen-DLL (Xblkld4.dll) in der Anwendung hinzufügen. Dies ist eine COM-DLL, für das Visual Studio .NET die Wrapperbibliothek automatisch erstellt.  
  
  Dieser Abschnitt enthält Beispielanwendungen, die veranschaulichen, wie Sie mit der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] verwaltete SQLXML-Klassen:  
 [Ausführen von SQL-Abfragen &#40;verwaltete SQLXML-Klassen&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [Ausführen von SQL-Abfragen mithilfe der „ExecuteXMLReader“-Methode](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [Verarbeitung von XML auf der Clientseite &#40;verwaltete SQLXML-Klassen&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [Ausführen von XPath-Abfragen &#40;verwaltete SQLXML-Klassen&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [Ausführen von XPath-Abfragen mit Namespaces &#40;verwaltete SQLXML-Klassen&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [Ausführen von Vorlagendateien mit der „CommandText“-Eigenschaft](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [Ausführen von Vorlagendateien mit der „CommandStream“-Eigenschaft](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [Anwenden einer XSL-Transformation &#40;verwaltete SQLXML-Klassen&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  
