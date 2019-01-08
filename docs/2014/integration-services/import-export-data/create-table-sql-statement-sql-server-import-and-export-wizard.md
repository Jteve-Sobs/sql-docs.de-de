---
title: SQL-Anweisung CREATE TABLE (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fad96ece925ad610f8bd5efc91538ac192a940aa
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764442"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>SQL-Anweisung CREATE TABLE (SQL Server-Import/Export-Assistent)
  Verwenden der **SQL­Anweisung Create Table** im Dialogfeld, um die Anweisung anzuzeigen, die automatisch generiert wurde, oder für Ihre Zwecke ändern. Wenn Sie diese Anweisung ändern, müssen Sie möglicherweise auch entsprechende Änderungen an den Spaltenzuordnungen vornehmen und daher die bearbeitete SQL-Anweisung anschließend manuell warten.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] generiert eine Standard-CREATE TABLE-Anweisung auf Grundlage der verbundenen Datenquelle. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Optionen  
 **SQL-Anweisung**  
 Zeigt die automatisch generierte SQL-Anweisung an, die hier auch bearbeitet werden kann.  
  
> [!NOTE]  
>  Wenn Sie einen Wagenrücklauf in die SQL-Anweisung einfügen möchten, drücken Sie STRG+EINGABETASTE. Wenn Sie nur die EINGABETASTE drücken, wird das Dialogfeld geschlossen.  
  
 **Automatisch generieren**  
 Durch Klicken auf die Schaltfläche **Automatisch generieren** stellen Sie die Standard-SQL-Anweisung nach einer Änderung wieder her.  
  
  
