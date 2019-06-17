---
title: Ausführen eines geplanten manuellen Failovers einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 386e07bd1be4eaac4c75541665fc6951e2a24fd3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62789294"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>Ausführen eines geplanten manuellen Failovers einer Verfügbarkeitsgruppe (SQL Server)
  In diesem Thema wird beschrieben, wie ein manuelles Failover ohne Datenverlust (ein *geplantes manuelles Failover*) in einer AlwaysOn-Verfügbarkeitsgruppe mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ausgeführt wird. Eine Verfügbarkeitsgruppe führt auf der Ebene eines Verfügbarkeitsreplikats ein Failover aus. Bei einem geplanten manuellen Failover geht wie bei jedem [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Failover ein sekundäres Replikat zur primären Rolle und gleichzeitig das frühere primäre Replikat zur sekundären Rolle über.  
  
 Ein geplantes manuelles Failover, das nur unterstützt wird, wenn das primäre Replikat und das sekundäre Zielreplikat im Modus für synchrone Commits ausgeführt und gerade synchronisiert werden, behält alle Daten in den sekundären Datenbanken bei, die mit der Verfügbarkeitsgruppe im sekundären Zielreplikat verknüpft sind. Sobald das frühere primäre Replikat zur sekundären Rolle übergeht, werden seine Datenbanken sekundäre Datenbanken und starten die Synchronisierung mit den neuen primären Datenbanken. Nach dem Übergang in den Status SYNCHRONIZED kann das neue sekundäre Replikat als Ziel eines künftigen geplanten manuellen Failovers dienen.  
  
> [!NOTE]  
>  Wenn das sekundäre und primäre Replikat für den automatischen Failovermodus konfiguriert sind, kann das sekundäre Replikat nach der Synchronisierung auch als Ziel für ein automatisches Failover dienen. Weitere Informationen finden Sie unter [Verfügbarkeitsmodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](availability-modes-always-on-availability-groups.md).  
  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Ein Failoverbefehl gibt einen Wert zurück, sobald das sekundäre Zielreplikat den Befehl akzeptiert hat. Die Datenbankwiederherstellung tritt jedoch asynchron auf, nachdem die Verfügbarkeitsgruppe aufgehört hat, ein Failover auszuführen.  
  
-   Datenbankübergreifende Konsistenz zwischen Datenbanken innerhalb der Verfügbarkeitsgruppe wird beim Failover nicht beibehalten.  
  
    > [!NOTE]  
    >  Datenbankübergreifende Transaktionen und verteilte Transaktionen werden von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nicht unterstützt. Weitere Informationen finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
###  <a name="Prerequisites"></a> Voraussetzungen und Einschränkungen  
  
-   Das sekundäre Zielreplikat und das primäre Replikat müssen im Verfügbarkeitsmodus für synchrone Commits ausgeführt werden.  
  
-   Das sekundäre Zielreplikat muss gerade mit dem primären Replikat synchronisiert werden. Dies erfordert, dass alle sekundären Datenbanken auf diesem sekundären Replikat mit der Verfügbarkeitsgruppe verknüpft und mit ihren entsprechenden primären Datenbanken synchronisiert sein müssen (das heißt, die lokalen sekundären Datenbanken müssen den Status SYNCHRONIZED aufweisen).  
  
    > [!TIP]  
    >  Um die Failoverbereitschaft eines sekundären Replikats zu ermitteln, fragen Sie die **is_failover_ready**-Spalte in der dynamischen Verwaltungssicht [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) ab, oder überprüfen Sie die Spalte **Failoverbereitschaft** des [AlwaysOn-Gruppendashboards](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
-   Dieser Task wird nur für das sekundäre Zielreplikat unterstützt. Sie müssen mit der Serverinstanz verbunden sein, auf der das sekundäre Zielreplikat gehostet wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 **So führen Sie manuell ein Failover für eine Verfügbarkeitsgruppe aus**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Serverinstanz her, die ein sekundäres Replikat der Verfügbarkeitsgruppe hostet, für die ein Failover ausgeführt werden muss, und erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Verfügbarkeitsgruppe, für die ein Failover ausgeführt werden soll, und wählen Sie den Befehl **Failover** aus.  
  
4.  Dadurch wird der Assistent für das Failover von Verfügbarkeitsgruppen gestartet. Weitere Informationen finden Sie unter [Verwenden des Assistenten für Failover-Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)ausgeführt wird.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So führen Sie manuell ein Failover für eine Verfügbarkeitsgruppe aus**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das sekundäre Zielreplikat hostet.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) -Anweisung wie folgt:  
  
     ALTER AVAILABILITY GROUP *Gruppenname* FAILOVER  
  
     Dabei ist *Gruppenname* der Name der Verfügbarkeitsgruppe.  
  
     Im folgenden Beispiel wird manuell ein Failover der *MyAg* -Verfügbarkeitsgruppe zum verbundenen sekundären Replikat ausgeführt.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **So führen Sie manuell ein Failover für eine Verfügbarkeitsgruppe aus**  
  
1.  Ändern Sie das Verzeichnis (`cd`) in die Serverinstanz, die das sekundäre Zielreplikat hostet.  
  
2.  Verwenden Sie das `Switch-SqlAvailabilityGroup`-Cmdlet.  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
     Im folgenden Beispiel wird manuell ein Failover der *MyAg* -Verfügbarkeitsgruppe zum sekundären Replikat mit dem angegebenen Pfad ausgeführt.  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nachdem Sie manuell ein Failover einer Verfügbarkeitsgruppe  
 Wenn Sie ein Failover außerhalb des [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] der Verfügbarkeitsgruppe ausgeführt haben, passen Sie die Quorumabstimmungen der WSFC-Knoten an die Konfiguration der neuen Verfügbarkeitsgruppe an. Weitere Informationen finden Sie unter [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Ausführen eines erzwungenen manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
  
