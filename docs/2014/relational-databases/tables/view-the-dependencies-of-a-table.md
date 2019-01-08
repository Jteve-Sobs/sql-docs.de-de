---
title: Anzeigen der Abhängigkeiten einer Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 111a0664a61a586558dd4792525c7adf2d68646d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772302"
---
# <a name="view-the-dependencies-of-a-table"></a>Anzeigen der Abhängigkeiten einer Tabelle
  Sie können die Abhängigkeiten einer Tabelle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So zeigen Sie die Abhängigkeiten einer Tabelle mit folgenden Elementen an:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die VIEW DEFINITION-Berechtigung für die Datenbank und die SELECT-Berechtigung für sys.sql_expression_dependencies für die Datenbank. Standardmäßig wird die SELECT-Berechtigung nur Mitgliedern der festen Datenbankrolle db_owner gewährt. Wenn einem anderen Benutzer die SELECT-Berechtigung und die VIEW DEFINITION-Berechtigung erteilt werden, kann dieser Berechtigte alle Abhängigkeiten in der Datenbank anzeigen.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-view-the-dependencies-of-a-table"></a>So zeigen Sie die Abhängigkeiten einer Tabelle an  
  
1.  Erweitern Sie im **Objekt-Explorer**den Ordner **Datenbanken**, erweitern Sie eine Datenbank, und erweitern Sie dann **Tabellen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Tabelle, und klicken Sie dann auf **Abhängigkeiten anzeigen**.  
  
3.  Im Dialogfeld **Objektabhängigkeiten**_\<Objektname >_ wählen Sie entweder **Objekte, abhängig von** *\<Objektname>*, oder **Objekte, von denen**_\<Objektname >_**abhängt**.  
  
4.  Wählen Sie im Raster **Abhängigkeiten** ein Objekt aus. Der Objekttyp (z.B. „Trigger“ oder „Gespeicherte Prozedur“) wird im Feld **Typ** angezeigt.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a>So zeigen Sie die Objekte an, die von einer Tabelle abhängen  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a>So zeigen Sie die Objekte an, von denen eine Tabelle abhängt  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Im folgenden Beispiel werden die Objekte, die von der Tabelle `Production.Product`abhängen, zurückgegeben. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql).  
  
  
