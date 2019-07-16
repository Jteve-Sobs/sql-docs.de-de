---
title: Sys. availability_group_listeners (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b363e410f35eb7880933520dd1dbf47f258b651e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041059"
---
# <a name="sysavailabilitygrouplisteners-transact-sql"></a>sys.availability_group_listeners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Für jede Always On-Verfügbarkeitsgruppe gilt: Entweder werden null Zeilen zurückgegeben, um anzuzeigen, dass der Verfügbarkeitsgruppe kein Netzwerkname zugeordnet ist, oder für jede Verfügbarkeitsgruppen-Listenerkonfiguration im WSFC-Cluster (Windows Server-Failoverclustering) wird eine Zeile zurückgegeben. In dieser Sicht wird die von Cluster erfasste Echtzeitkonfiguration angezeigt.  
  
> [!NOTE]  
>  In dieser Katalogsicht werden nicht die Details einer IP-Konfiguration beschrieben, die im WSFC-Cluster definiert wurde.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Verfügbarkeitsgruppen-ID (**Group_id**) von [Sys. availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md).|  
|**listener_id**|**nvarchar(36)**|Die GUID der Clusterressourcen-ID.|  
|**dns_name**|**vom Datentyp nvarchar(63)**|Der konfigurierte Netzwerkname (Hostname) des Verfügbarkeitsgruppenlisteners.|  
|**port**|**int**|Die für den Verfügbarkeitsgruppenlistener konfigurierte TCP-Portnummer.<br /><br /> NULL = Der Listener wurde außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfiguriert, und die Portnummer des Listeners wurde der Verfügbarkeitsgruppe nicht hinzugefügt. Port für dem, verwenden der Option MODIFY LISTENER, der die [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**is_conformant**|**bit**|Gibt an, ob diese IP-Konfiguration konform ist. Folgende Werte sind möglich:<br /><br /> 1 = Der Listener ist konform. Nur "OR"-Beziehungen, die zwischen der IP (Internet Protocol)-Adressen vorhanden sein. *Konforme* umfasst jede IP-Konfiguration, die erstellt wurde die [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung. Zudem gilt eine IP-Konfiguration als konform, die zwar außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurde (z. B. mit dem WSFC-Failovercluster-Manager), aber mit der TSQL-Anweisung ALTER AVAILABILITY GROUP geändert werden kann.<br /><br /> 0 = Der Listener ist nicht konform. In der Regel weist dies auf eine IP-Adresse hin, die nicht mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Befehlen konfiguriert werden konnte und stattdessen direkt im WSFC-Cluster definiert wurde.|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|Die Cluster-IP-Konfigurationszeichenfolgen für diesen Listener, falls vorhanden. NULL = Der Listener hat keine virtuellen IP-Adressen. Zum Beispiel:<br /><br /> IPv4-Adresse: `65.55.39.10`.<br /><br /> IPv6-Adresse: `2001::4898:23:1002:20f:1fff:feff:b3a3`|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen für Always On-Verfügbarkeitsgruppen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
