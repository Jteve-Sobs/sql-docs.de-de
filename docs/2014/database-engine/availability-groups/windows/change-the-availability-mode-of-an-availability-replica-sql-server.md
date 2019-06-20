---
title: Ändern des Verfügbarkeitsmodus eines Verfügbarkeitsreplikats (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1fc60e637f9bf3d2e3b72f8b451c669d81a26207
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62815564"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>Ändern des Verfügbarkeitsmodus eines Verfügbarkeitsreplikats (SQL Server)
  In diesem Thema wird beschrieben, wie der Verfügbarkeitsmodus eines Verfügbarkeitsreplikats in einer AlwaysOn-Verfügbarkeitsgruppe in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell geändert wird. Der Verfügbarkeitsmodus ist eine Replikateigenschaft, die steuert, ob das Replikat einen asynchronen oder synchronen Commit ausführt. Der*asynchrone Commitmodus* maximiert die Leistung auf Kosten der Hochverfügbarkeit und unterstützt nur erzwungene manuelle Failovervorgänge (mit möglichem Datenverlust), in der Regel *erzwungenes Failover*genannt. Der*synchrone Commitmodus* bevorzugt Hochverfügbarkeit gegenüber Leistung und unterstützt, sobald das sekundäre Replikat synchronisiert ist, manuelle Failovervorgänge und optional automatische Failovervorgänge.  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Sie müssen mit der Serverinstanz verbunden sein, die das primäre Replikat hostet.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 **So ändern Sie den Verfügbarkeitsmodus einer Verfügbarkeitsgruppe**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das primäre Verfügbarkeitsreplikat hostet, und erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Klicken Sie auf die Verfügbarkeitsgruppe, deren Replikat geändert werden soll.  
  
4.  Klicken Sie mit der rechten Maustaste auf das Replikat, und klicken Sie auf **Eigenschaften**.  
  
5.  Verwenden Sie im Dialogfeld **Eigenschaften des Verfügbarkeitsreplikats** die Dropdownliste **Verfügbarkeitsmodus** , um den Verfügbarkeitsmodus für dieses Replikat zu ändern.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie den Verfügbarkeitsmodus einer Verfügbarkeitsgruppe**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) -Anweisung wie folgt:  
  
     ALTER AVAILABILITY GROUP *Gruppenname* MODIFY REPLICA ON '*Servername*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     Dabei ist *Gruppenname* der Name der Verfügbarkeitsgruppe und *Servername* der Name der Serverinstanz, die das Replikat hostet, das geändert werden soll.  
  
    > [!NOTE]  
    >  FAILOVER_MODE = AUTOMATIC wird nur unterstützt, wenn Sie auch AVAILABILITY_MODE = SYNCHRONOUS_COMMIT angeben.  
  
     Im folgenden, für das primäre Replikat der `AccountsAG` -Verfügbarkeitsgruppe eingegebenen Beispiel werden der Verfügbarkeitsmodus und der Failovermodus für das von der `INSTANCE09` -Serverinstanz gehostete Replikat in den Modus für synchrone Commits bzw. automatisches Failover geändert.  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **So ändern Sie den Verfügbarkeitsmodus einer Verfügbarkeitsgruppe**  
  
1.  Ändern Sie das Verzeichnis (`cd`) zur Serverinstanz, die das primäre Replikat hostet.  
  
2.  Verwenden Sie das `Set-SqlAvailabilityReplica`-Cmdlet mit dem `AvailabilityMode`-Parameter und optional dem `FailoverMode`-Parameter.  
  
     Beispielsweise wird durch diesen Befehl das Replikat `MyReplica` in der Verfügbarkeitsgruppe `MyAg` so geändert, dass der Verfügbarkeitsmodus für synchrone Commits verwendet und automatische Failover unterstützt werden.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verfügbarkeitsmodi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md)   
 [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
  
  
