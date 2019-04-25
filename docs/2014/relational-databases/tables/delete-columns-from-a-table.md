---
title: Spalten aus einer Tabelle löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 718aeca12c90435b68fd6cedde150dfbdeb3c063
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761653"
---
# <a name="delete-columns-from-a-table"></a>Spalten aus einer Tabelle löschen
  In diesem Thema wird beschrieben, wie Tabellenspalten in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht werden können.  
  
> [!CAUTION]  
>  Wenn Sie eine Spalte aus einer Tabelle löschen, wird die Spalte mit allen darin enthaltenen Daten aus der Datenbank gelöscht. Dieser Vorgang kann nicht rückgängig gemacht werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So entfernen Sie eine Spalte aus der Tabelle mithilfe von:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Sie können keine Spalte löschen, die eine CHECK-Einschränkung hat. Sie müssen zuerst die Einschränkung löschen.  
  
 Eine Spalte, für die PRIMARY KEY- oder FOREIGN KEY-Einschränkungen oder andere Abhängigkeiten bestehen, können Sie nur mit dem Tabellen-Designer löschen. Wenn Sie den Objekt-Explorer oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verwenden, müssen Sie zuerst alle Abhängigkeiten von der Spalte entfernen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a>So löschen Sie Spalten mit dem Objekt-Explorer  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, aus der Sie Spalten löschen möchten, und klicken Sie anschließend auf **Löschen**.  
  
3.  Klicken Sie im Dialogfeld **Objekt löschen** auf **OK**.  
  
 Wenn die Spalte Einschränkungen oder andere Abhängigkeiten enthält, wird eine Fehlermeldung im Dialogfeld **Objekt löschen** angezeigt. Beheben Sie den Fehler, indem Sie die Einschränkungen löschen, auf die verwiesen wird.  
  
#### <a name="to-delete-columns-by-using-table-designer"></a>So löschen Sie Spalten mit dem Tabellen-Designer  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, aus der Sie Spalten löschen möchten, und wählen Sie **Entwurf**aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die zu löschende Spalte, und wählen Sie im Kontextmenü die Option **Spalte löschen** aus.  
  
3.  Wenn die betreffende Spalte in eine Beziehung eingebunden ist (FOREIGN KEY oder PRIMARY KEY), werden Sie in einer Meldung aufgefordert, das Löschen der ausgewählten Spalten und der zugehörigen Beziehungen zu bestätigen. Klicken Sie auf **Ja**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-columns"></a>So löschen Sie Spalten  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 Wenn die Spalte Einschränkungen oder andere Abhängigkeiten enthält, wird eine Fehlermeldung zurückgegeben. Beheben Sie den Fehler, indem Sie die Einschränkungen löschen, auf die verwiesen wird.  
  
 Weitere Beispiele finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
##  <a name="FollowUp"></a>  
