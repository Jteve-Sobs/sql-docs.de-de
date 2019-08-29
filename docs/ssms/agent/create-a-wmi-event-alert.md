---
title: Erstellen einer WMI-Ereigniswarnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f1f092ba4facfe166c8be67a21e6f20d414466e5
ms.sourcegitcommit: cbbb210c0315f9e2be2b9cd68db888ac53429814
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69890926"
---
# <a name="create-a-wmi-event-alert"></a>Erstellen einer WMI-Ereigniswarnung
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine Warnung des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Agents erstellen, die beim Auftreten eines bestimmten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Ereignisses ausgelöst wird, das vom WMI-Anbieter für Serverereignisse überwacht wird.  
  
Informationen zur Verwendung der WMI-Anbieter zum Überwachen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignissen finden Sie unter [Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md). Informationen zu den Berechtigungen, die erforderlich sind, um Benachrichtigungen zu WMI-Ereigniswarnungen zu erhalten, finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md). Weitere Informationen zu WQL finden Sie unter [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Restrictions"></a>Einschränkungen  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lässt sich das gesamte Warnungssystem auf einfache Weise mit einer grafischen Oberfläche verwalten. Dies ist die empfohlene Vorgehensweise, um eine Warnungsinfrastruktur zu konfigurieren.  
  
-   Ereignisse, die mit **xp_logevent** generiert werden, treten in der master-Datenbank auf. Daher wird von **xp_logevent** erst dann eine Warnung ausgelöst, wenn der **\@database_name**-Wert für die Warnung den Wert **'master'** oder NULL aufweist.  
  
-   Es werden nur WMI-Namespaces auf dem Computer unterstützt, auf dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird.  
  
### <a name="Security"></a>Sicherheit  
  
#### <a name="Permissions"></a>Berechtigungen  
Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** die Prozedur **sp_add_alert**ausführen.  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-wmi-event-alert"></a>So erstellen Sie eine WMI-Ereigniswarnung  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine WMI-Ereigniswarnung erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Warnungen** , und wählen Sie **Neue Warnung**aus.  
  
4.  Geben Sie im Dialogfeld **Neue Warnung** einen **Namen** für diese Warnung ein.  
  
5.  Aktivieren Sie das Kontrollkästchen **Aktivieren** , um die Ausführung der Warnung zu ermöglichen. Standardmäßig ist **Aktivieren** aktiviert.  
  
6.  Klicken Sie in der Liste **Typ** auf **WMI-Ereigniswarnung**.  
  
7.  Geben Sie unter **WMI-Ereigniswarnungsdefinition**im Feld **Namespace** den WMI-Namespace für die WQL-Anweisung (WMI Query Language) an, die das WMI-Ereignis identifiziert, welches diese Warnung auslöst.  
  
8.  Geben Sie im Feld **Abfrage** die WQL-Anweisung an, die das Ereignis identifiziert, auf das diese Warnung reagiert.  
  
9. Klicken Sie auf **OK**.  
  
## <a name="TsqlProcedure"></a>Verwenden von Transact-SQL  
  
#### <a name="to-create-a-wmi-event-alert"></a>So erstellen Sie eine WMI-Ereigniswarnung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database.',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_add_alert (Transact-SQL)](https://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
