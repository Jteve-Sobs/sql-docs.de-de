---
title: Sys. availability_replicas (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_replicas_TSQL
- availability_replicas
- sys.availability_replicas
- sys.availability_replicas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_replicas catalog view
ms.assetid: 0a06e9b6-a1e4-4293-867b-5c3f5a8ff62c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6623d6b95dfe0ebd4e45b13d190d8176bcab1a3c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942617"
---
# <a name="sysavailabilityreplicas-transact-sql"></a>sys.availability_replicas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile für jedes Verfügbarkeitsreplikat zurück, das zu einer Always On-Verfügbarkeitsgruppe im WSFC-Failovercluster gehört.  
  
Wenn die lokale Serverinstanz nicht mit dem WSFC-Failovercluster kommunizieren kann, beispielsweise beim Ausfall des Clusters oder im Fall eines verlorenen Quorums, werden nur Zielen für lokale Verfügbarkeitsreplikate zurückgegeben. Diese Zeilen enthalten nur die Spalten der Daten, die in Metadaten lokal zwischengespeichert sind.  
  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Eindeutige ID des Replikats.|  
|**group_id**|**uniqueidentifier**|Eindeutige ID der Verfügbarkeitsgruppe, zu der das Replikat gehört.|  
|**replica_metadata_id**|**int**|ID für das lokale Metadatenobjekt für Verfügbarkeitsreplikate in der Datenbank-Engine.|  
|**replica_server_name**|**nvarchar(256)**|Entspricht dem Servernamen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die dieses Replikat hostet, sowie bei einer nicht standardmäßigen Instanz dem Instanznamen.|  
|**owner_sid**|**varbinary(85)**|Sicherheits-ID (SID), die bei dieser Serverinstanz für den externen Eigentümer dieses Verfügbarkeitsreplikats registriert ist.<br /><br /> NULL für nicht lokale Verfügbarkeitsreplikate.|  
|**endpoint_url**|**nvarchar(128)**|Entspricht der Zeichenfolgendarstellung des vom Benutzer angegebenen Datenbankspiegelungs-Endpunkts, der von Verbindungen zwischen primären und sekundären Replikaten für die Datensynchronisierung verwendet wird. Informationen zur Syntax von Endpunkt-URLs finden Sie unter [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).<br /><br /> NULL = Kommunikation mit dem WSFC-Failovercluster ist nicht möglich.<br /><br /> Um diesen Endpunkt zu ändern, verwenden Sie die ENDPOINT_URL-Option von [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**availability_mode**|**tinyint**|Der Verfügbarkeitsmodus des Replikats. Folgende Werte sind möglich:<br /><br /> 0 &#124; asynchroner Commit. Das primäre Replikat kann einen Commit für Transaktionen ausführen, ohne das Schreiben des Protokolls auf den Datenträger durch das sekundäre Replikat abzuwarten.<br /><br /> 1 &#124; synchroner Commit. Das primäre Replikat wartet mit dem Ausführen des Commits für eine bestimmte Transaktion, bis das sekundäre Replikat die Transaktion auf den Datenträger geschrieben hat.<br /><br />4 &#124; nur Konfiguration. Das primäre Replikat sendet die Konfigurationsmetadaten von Verfügbarkeitsgruppen synchron mit dem Replikat. Daten des Benutzers werden nicht an das Replikat übertragen. In SQL Server 2017 CU1 und höher verfügbar.<br /><br /> Weitere Informationen finden Sie unter [Verfügbarkeitsmodi &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)ausgetauscht werden.|  
|**availability_mode_desc**|**nvarchar(60)**|Beschreibung der **Verfügbarkeit\_Modus**, eine von:<br /><br /> ASYNCHRONE\_COMMIT<br /><br /> SYNCHRONE\_COMMIT<br /><br /> KONFIGURATION\_NUR<br /><br /> Verwenden Sie zum Ändern des Verfügbarkeitsmodus eines verfügbarkeitsreplikats die AVAILABILITY_MODE-Option von [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.<br/><br>Sie können nicht zur Konfiguration des Verfügbarkeitsmodus eines Replikats ändern\_nur. Sie können eine Konfiguration nicht ändern\_ONLY-Replikat zu einem sekundären oder primären Replikat. |  
|**Failover\_Modus**|**tinyint**|Die [Failovermodus](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md) des eines verfügbarkeitsreplikats:<br /><br /> 0 &#124; Automatisches Failover. Das Replikat ist ein potenzielles Ziel für automatische Failovers.  Automatisches Failover wird nur unterstützt, wenn der Verfügbarkeitsmodus auf synchrone Commits festgelegt wird (**Verfügbarkeit\_Modus** = 1) und das verfügbarkeitsgruppe das verfügbarkeitsreplikat gerade synchronisiert wird.<br /><br /> 1 &#124; Manuelles Failover. Ein Failover zu einem sekundären Replikat, für das ein manuelles Failover festgelegt ist, muss vom Datenbankadministrator manuell initiiert werden. Der Failovertyp, der ausgeführt wird, hängt davon ab, ob das sekundäre Replikat wie folgt synchronisiert wird:<br /><br /> Wenn das Verfügbarkeitsreplikat nicht synchronisiert oder die Synchronisierung noch durchgeführt wird, kann nur ein erzwungenes Failover auftreten (mit möglichem Datenverlust).<br /><br /> Wenn der Verfügbarkeitsmodus auf synchrone Commits festgelegt wird (**Verfügbarkeit\_Modus** = 1) und das verfügbarkeitsreplikat ist derzeit synchronisiert, Manuelles Failover ohne Datenverlust auftreten kann.<br /><br /> Um ein Rollup der datenbanksynchronisierungsstatus jeder verfügbarkeitsdatenbank in einem verfügbarkeitsreplikat anzuzeigen, verwenden die **Synchronisierung\_Integrität** und **Synchronisierung\_Integrität\_Desc** Spalten der [Sys. dm_hadr_availability_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md) dynamische verwaltungssicht. Der Rollup berücksichtigt den Synchronisierungsstatus jeder Verfügbarkeitsdatenbank und den Verfügbarkeitsmodus ihres Verfügbarkeitsreplikats.<br /><br /> **Hinweis**: Um den Synchronisierungsstatus einer gegebenen verfügbarkeitsdatenbank anzuzeigen, Fragen Sie die **Synchronisierung\_Zustand** und **Synchronisierung\_Integrität** Spalten von der [Sys. dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) dynamische verwaltungssicht.|  
|**Failover\_Modus\_Desc**|**nvarchar(60)**|Beschreibung der **Failover\_Modus**, eine von:<br /><br /> MANUAL<br /><br /> AUTOMATIC<br /><br /> Um den Failovermodus zu ändern, verwenden Sie das FAILOVER\_Modus Option [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**session\_timeout**|**int**|Der Timeoutzeitraum in Sekunden. Der Timeoutzeitraum ist die maximale Zeit, die das Replikat für den Empfang einer Meldung von einem anderen Replikat abwartet, bevor die Verbindung zwischen dem primären und sekundären Replikat als fehlgeschlagen betrachtet wird. Das Sitzungstimeout erkennt, ob sekundäre Replikate mit dem primären Replikat verbunden sind.<br /><br /> Bei der Erkennung einer fehlgeschlagenen Verbindungs mit einem sekundären Replikat betrachtet das primäre Replikat das sekundäre Replikat nicht\_synchronisiert. Ein sekundäres Replikat versucht einfach, erneut eine Verbindung herzustellen, wenn eine fehlgeschlagene Verbindung mit dem primären Replikat erkannt wird.<br /><br /> **Hinweis**: Sitzungstimeouts verursachen keine automatischen Failovers.<br /><br /> Um diesen Wert zu ändern, verwenden Sie die SESSION_TIMEOUT-Option der [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**primäre\_Rolle\_ermöglichen\_Verbindungen**|**tinyint**|Gibt an, ob die Verfügbarkeit alle Verbindungen oder nur Verbindungen mit Lese-/Schreibzugriff zulässt. Folgende Werte sind möglich:<br /><br /> 2 = Alle (Standard)<br /><br /> 3 = Lesen/Schreiben|  
|**primary\_role\_allow\_connections\_desc**|**nvarchar(60)**|Beschreibung der **primären\_Rolle\_ermöglichen\_Verbindungen**, eine von:<br /><br /> ALL<br /><br /> LESEN SIE\_SCHREIBEN|  
|**sekundäre\_Rolle\_ermöglichen\_Verbindungen**|**tinyint**|Gibt an, ob ein Verfügbarkeitsreplikat, das die sekundäre Rolle ausführt (also einem sekundären Replikat entspricht), Verbindungen von Clients zulassen kann. Folgende Werte sind möglich:<br /><br /> 0 = Nein. Für die Datenbanken im sekundären Replikat sind keine Verbindungen zugelassen, und die Datenbanken sind für den Lesezugriff nicht verfügbar. Dies ist die Standardeinstellung.<br /><br /> 1 = Nur Lesezugriff. Nur Verbindungen mit Lesezugriff auf die Datenbanken im sekundären Replikat sind zugelassen. Alle Datenbanken im Replikat sind für den Lesezugriff verfügbar.<br /><br /> 2 = Alle. Für alle Verbindungen mit den Datenbanken im sekundären Replikat ist der schreibgeschützte Zugriff zugelassen.<br /><br /> Weitere Informationen finden Sie unter [Aktive sekundäre Replikate: Lesbare sekundäre Replikate &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).|  
|**secondary_role_allow_connections_desc**|**nvarchar(60)**|Beschreibung der **Secondary_role_allow_connections**, eine von:<br /><br /> Nein<br /><br /> READ_ONLY<br /><br /> ALL|  
|**create_date**|**datetime**|Das Datum, an dem das Replikat erstellt wurde.<br /><br /> NULL = Replikat befindet sich nicht auf dieser Serverinstanz.|  
|**modify_date**|**datetime**|Datum der letzten Änderung des Replikats.<br /><br /> NULL = Replikat befindet sich nicht auf dieser Serverinstanz.|  
|**backup_priority**|**int**|Stellt die benutzerdefinierte Priorität für die Ausführung von Sicherungen auf diesem Replikat in Relation zu den anderen Replikaten in derselben Verfügbarkeitsgruppe dar. Der Wert liegt im Bereich von 0 bis 100 und ist eine ganze Zahl.<br /><br /> Weitere Informationen finden Sie unter [Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**read_only_routing_url**|**nvarchar(256)**|Konnektivitätsendpunkt (URL) der schreibgeschützten Verbindung für das Verfügbarkeitsreplikat. Weitere Informationen finden Sie unter [Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md).|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW ANY DEFINITION-Berechtigung für die Serverinstanz.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
