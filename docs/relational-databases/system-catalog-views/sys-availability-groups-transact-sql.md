---
title: Sys. availability_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_TSQL
- availability_groups_TSQL
- sys.availability_groups
- availability_groups
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups catalog view
ms.assetid: da7fa55f-c008-45d9-bcfc-3513b02d9e71
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b6992cceb19d0fe39c1e53e36535949a94907295
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942654"
---
# <a name="sysavailabilitygroups-transact-sql"></a>sys.availability_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Verfügbarkeitsgruppe zurück, für die die lokale SQL Server-Instanz ein Verfügbarkeitsreplikat hostet. Jede Zeile enthält eine zwischengespeicherte Kopie der Metadaten der Verfügbarkeitsgruppe.  
   
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Eindeutiger Bezeichner (GUID) der Verfügbarkeitsgruppe.|  
|**name**|**sysname**|Der Name der Verfügbarkeitsgruppe. Dies ist ein vom Benutzer angegebener Name, der innerhalb des Windows Server-Failoverclusters (WSFC) eindeutig sein muss.|  
|**resource_id**|**nvarchar(40)**|Ressourcen-ID für die WSFC-Clusterressource.|  
|**resource_group_id**|**nvarchar(40)**|Ressourcengruppen-ID für die WSFC-Clusterressourcengruppe der Verfügbarkeitsgruppe.|  
|**failure_condition_level**|**int**|Benutzerdefinierte fehlerbedingungsebene unter dem ein automatisches Failover ausgelöst werden, muss eine der Integer-Werte in der Tabelle direkt unterhalb dieser Tabelle dargestellt.<br /><br /> Die Fehlerbedingungsebenen (1–5) reichen von der Ebene 1 mit den wenigsten Einschränkungen bis zur Ebene 5 mit den meisten Einschränkungen. Jede Bedingungsebene umfasst stets auch sämtliche weniger restriktiven Ebenen. Daher schließt die strengste Bedingungsebene 5 die vier Bedingungsebenen mit weniger Einschränkungen (1-4) ein, Ebene 4 schließt die Ebenen 1-3 ein usw.<br /><br /> Um diesen Wert zu ändern, verwenden Sie die FAILURE_CONDITION_LEVEL-Option von der [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**health_check_timeout**|**int**|Wartezeit (in Millisekunden) für die [Sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) gespeicherten Systemprozedur Serverzustand Informationen zurückgegeben werden, bevor die Server-Instanz davon ausgegangen, dass ist langsam oder blockiert werden. Der Standardwert ist 30000 Millisekunden (oder 30 Sekunden).<br /><br /> Um diesen Wert zu ändern, verwenden Sie die HEALTH_CHECK_TIMEOUT-Option von der [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**automated_backup_preference**|**tinyint**|Bevorzugter Speicherort zum Durchführen von Sicherungen auf den Verfügbarkeitsdatenbanken in dieser Verfügbarkeitsgruppe. Im folgenden sind die möglichen Werte und deren Beschreibungen.<br /><br /> <br /><br /> 0: Primäre. Sicherungen sollten immer auf dem primären Replikat erfolgen.<br /><br /> 1: Nur sekundär. Die Durchführung von Sicherungen auf einem sekundären Replikat wird bevorzugt.<br /><br /> 2: Bevorzugen Sie sekundär. Die Durchführung von Sicherungen auf einem sekundären Replikat wird bevorzugt, aber die Durchführung von Sicherungen auf dem primären Replikat wird akzeptiert, wenn kein sekundäres Replikat für Sicherungsvorgänge verfügbar ist. Dies ist das Standardverhalten.<br /><br /> 3: Beliebiges Replikat. Keine Präferenz, ob Sicherungen auf dem primären Replikat oder einem sekundären Replikat durchgeführt werden.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**automated_backup_preference_desc**|**nvarchar(60)**|Beschreibung der **Automated_backup_preference**, eine von:<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> Keine|  
|**version**|**smallint**|Die Version der Metadaten der verfügbarkeitsgruppe im Windows-Failovercluster gespeichert. Diese Versionsnummer wird erhöht, wenn neue Funktionen hinzugefügt werden.|  
|**basic_features**|**bit**|Gibt an, ob es sich um eine Basis-verfügbarkeitsgruppe handelt. Weitere Informationen finden Sie unter [Basis-Verfügbarkeitsgruppen &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).|  
|**dtc_support**|**bit**|Gibt an, ob die DTC-Unterstützung für diese verfügbarkeitsgruppe aktiviert wurde. Die **DTC_SUPPORT** Option **CREATE AVAILABILITY GROUP** diese Einstellung steuert.|  
|**db_failover**|**bit**|Gibt an, ob die verfügbarkeitsgruppe ein Failover für die Integrität der Datenbank unterstützt. Die **"db_failover"** Option **CREATE AVAILABILITY GROUP** diese Einstellung steuert.|  
|**is_distributed**|**bit**|Gibt an, ob dies eine verteilte verfügbarkeitsgruppe ist. Weitere Informationen finden Sie unter [Verteilte Verfügbarkeitsgruppen &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md).|  
  
## <a name="failure-condition-level--values"></a>Fehler-Bedingung Ebenenwerte  
 Die folgende Tabelle beschreibt die möglichen fehlerbedingungsebenen für die **Failure_condition_level** Spalte.  
  
|Wert|Fehlerbedingung|  
|-----------|-----------------------|  
|1|Gibt an, dass in einem der folgenden Fälle ein automatisches Failover initiiert werden muss:<br /><br /> <br /><br /> – Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst ist nicht verfügbar.<br /><br /> – Die Lesedauer der verfügbarkeitsgruppe für die Verbindung mit WSFC-Failovercluster läuft ab, da keine ACK-Meldung von der Serverinstanz empfangen wird. Weitere Informationen finden Sie unter [How It Works: SQL Server Always On Lease Timeout (Funktionsweise: SQL Server Always On-Leasetimeout)](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).|  
|2|Gibt an, dass in einem der folgenden Fälle ein automatisches Failover initiiert werden muss:<br /><br /> <br /><br /> – Die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Verbindung zu Cluster und der vom Benutzer angegebene **Health_check_timeout** -Schwellenwert der verfügbarkeitsgruppe wurde überschritten.<br /><br /> – Das verfügbarkeitsreplikat ist in einem fehlerhaften Zustand.|  
|3|Gibt an, dass ein automatisches Failover bei kritischen internen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern initiiert werden soll, z. B. verwaisten Spinlocks, schwerwiegenden Schreibzugriffsverletzungen oder zu vielen Sicherungen.<br /><br /> Dies ist der Standardwert.|  
|4|Gibt an, dass ein automatisches Failover bei mittelschweren internen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern initiiert werden soll, z. B. bei dauerhaft unzureichendem Arbeitsspeicher im internen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressourcenpool.|  
|5|Gibt an, dass ein automatisches Failover bei sämtlichen qualifizierten Fehlerbedingungen initiiert werden soll, einschließlich:<br /><br /> <br /><br /> – Erschöpfung der SQL Engine-Arbeitsthreads.<br /><br /> – Erkennung eines unlösbaren Deadlocks.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW ANY DEFINITION-Berechtigung für die Serverinstanz.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
