---
title: Umbenennen von Tabellen (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c8a9fd43e62bda03b8f994e2a8639524b4bea645
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016335"
---
# <a name="rename-tables-database-engine"></a>Umbenennen von Tabellen (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Umbenennen einer Tabelle in einer SQL Server- oder Azure SQL-Datenbank

Verwenden Sie die T-SQL-Anweisung [RENAME OBJECT](../../t-sql/statements/rename-transact-sql.md) zum Umbenennen einer Tabelle in Azure SQL Data Warehouse oder Parallel Data Warehouse. 
  
> [!CAUTION]  
>  Das Umbenennen einer Tabelle muss sorgfältig überlegt sein. Alle Abfragen, Sichten, benutzerdefinierten Funktionen, gespeicherten Prozeduren und Programme, die auf diese Tabelle verweisen, werden durch die Namensänderung ungültig.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So benennen Sie eine Tabelle um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Durch Umbenennen einer Tabelle werden die Verweise auf diese Tabelle nicht automatisch umbenannt. Sie müssen Objekte, die auf die umbenannte Tabelle verweisen, manuell ändern. Wenn Sie z. B. eine Tabelle umbenennen und in einem Trigger auf diese Tabelle verwiesen wird, müssen Sie den Trigger ändern, sodass er den neuen Tabellennamen wiedergibt. Verwenden Sie [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) für eine Auflistung der Abhängigkeiten von der Tabelle, bevor Sie sie umbenennen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>So benennen Sie eine Tabelle um  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, die umbenannt werden soll, und wählen Sie im Kontextmenü **Entwerfen** aus.  
  
2.  Wählen Sie im Menü **Ansicht** die Option **Eigenschaften**aus.  
  
3.  Geben Sie im Fenster **Eigenschaften** im Feld **Name** einen neuen Namen für die Tabelle ein.  
  
4.  Wenn Sie diesen Vorgang abbrechen möchten, drücken Sie die ESC-TASTE, bevor Sie das Feld verlassen.  
  
5.  Wählen Sie im Menü **Datei** **Speichern** _Tabellenname_ aus.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-rename-a-table"></a>So benennen Sie eine Tabelle um  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Im folgenden Beispiel wird die `SalesTerritory` -Tabelle im Schema `SalesTerr` in `Sales` umbenannt. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 Weitere Beispiele finden Sie unter [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).  
  
  
