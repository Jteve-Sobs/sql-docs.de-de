---
title: SQL-Anweisung CREATE TABLE (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c73c9df155d1e09552fbf5774ac4599bf9cdbdf9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65779159"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>SQL-Anweisung CREATE TABLE (SQL Server-Import/Export-Assistent)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Wenn Sie die Option **Zieltabelle erstellen** und anschließend **SQL bearbeiten** im Dialogfeld **Spaltenzuordnungen** auswählen, zeigt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import/Export-Assistent das Dialogfeld **SQL-Anweisung CREATE TABLE** an. Auf dieser Seite überprüfen Sie den Befehl **CREATE TABLE**, den der Assistent zum Erstellen der neuen Zieltabelle ausführt, und passen ihn optional an.
  
> [!NOTE]
> Wenn Sie Informationen zur [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE-Anweisung und nicht zum Dialogfeld **SQL-Anweisung CREATE TABLE** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten suchen, gehen Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>Screenshot der Seite mit der SQL-Anweisung „Create Table“  
 Der folgende Screenshot zeigt das Dialogfeld **SQL-Anweisung CREATE TABLE** des Assistenten an.
 
In diesem Beispiel enthält das Feld **SQL-Anweisung** die vom Assistenten generierte Standardanweisung **CREATE TABLE** . Diese Anweisung erstellt eine neue Zieltabelle namens **Person.AddressNew**, die eine Kopie der Quelltabelle **Person.Address** darstellt. 
  
 ![Seite „Tabelle erstellen“ des Import/Export-Assistenten](../../integration-services/import-export-data/media/create-table.png "Seite „Tabelle erstellen“ des Import/Export-Assistenten")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>Überprüfen oder generieren Sie erneut die Anweisung CREATE TABLE  
 **SQL-Anweisung**  
Zeigt die automatisch generierte SQL-Anweisung an, und lässt Sie diese bearbeiten.
 
Wenn Sie den Standardbefehl CREATE TABLE ändern, müssen Sie möglicherweise auch Änderungen an den zugehörigen Spaltenzuordnungen vornehmen, wenn Sie zum Dialogfeld **Spaltenzuordnungen** zurückkehren.  
  
Drücken Sie STRG+EINGABETASTE, um einen Wagenrücklauf in den Text der SQL-Anweisung einzufügen. Wenn Sie nur die EINGABETASTE drücken, wird das Dialogfeld geschlossen.  
  
Weitere Informationen über die CREATE TABLE-Anweisung und die Syntax, finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).   
  
 **Automatisch generieren**  
 Durch Klicken auf die Schaltfläche **Automatisch generieren** stellen Sie die Standard-SQL-Anweisung nach einer Änderung wieder her.  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>Erstellen Sie eine Tabelle mit einer FILESTREAM-Spalte  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import/Export-Assistent erstellt eine CREATE TABLE-Standardanweisung basierend auf der verbundenen Datenquelle. Diese CREATE TABLE-Standardanweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine FILESTREAM-Spalte enthält.
 1.  Implementieren Sie zunächst FILESTREAM-Speicher in der Zieldatenbank, um eine FILESTREAM-Spalte mithilfe des Assistenten zu kopieren.
 2.  Fügen Sie dann manuell das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **SQL-Anweisung CREATE TABLE** hinzu.  

Weitere Informationen zur Syntax finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). Weitere Informationen zu FILESTREAM finden Sie unter [Binary Large Object &#40;Blob&#41;-Daten &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
## <a name="whats-next"></a>Wie geht es weiter?  
 Nachdem Sie den CREATE TABLE-Befehl überprüft und angepasst haben und auf **OK**geklickt haben, leitet Sie das Dialogfeld **SQL Anweisung CREATE TABLE** zum Dialogfeld **Spaltenzuordnungen** zurück. Weitere Informationen finden Sie unter [Spaltenzuordnungen](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>Siehe auch
[Erste Schritte mit diesem einfachen Beispiel des Import/Export-Assistenten](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


