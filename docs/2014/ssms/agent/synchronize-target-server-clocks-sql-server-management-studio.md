---
title: Synchronisieren von Zielserveruhren (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 769b2b9caba541af3a1ea38e1969d8a6422950be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68188766"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a>Synchronize Target Server Clocks (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie Zielserveruhren in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit der Masterserveruhr mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]synchronisieren können. Das Synchronisieren dieser Systemuhren unterstützt Auftragszeitpläne.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So synchronisieren Sie die Uhren der Zielserver mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>So synchronisieren Sie die Uhren der Zielserver  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie die Zielserveruhren mit der Masterserveruhr synchronisieren möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserververwaltung**, und klicken Sie auf **Zielserver verwalten**.  
  
3.  Klicken Sie im Dialogfeld **Zielserver verwalten** auf **Anweisungen bereitstellen**.  
  
4.  Wählen Sie in der Liste **Anweisungstyp** die Option **Uhren synchronisieren**aus.  
  
5.  Führen Sie unter **Empfänger**eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Alle Zielserver** , um die Uhren aller Zielserver mit der Uhr des Masterservers zu synchronisieren.  
  
    -   Klicken Sie auf **Diese Zielserver** , um bestimmte Serveruhren zu synchronisieren, und wählen Sie dann alle Zielserver aus, deren Uhren mit der Uhr des Masterservers synchronisiert werden sollen.  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>So synchronisieren Sie die Uhren der Zielserver  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_resync_targetserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).  
  
  
