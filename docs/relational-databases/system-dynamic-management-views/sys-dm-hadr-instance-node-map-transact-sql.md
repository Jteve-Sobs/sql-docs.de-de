---
title: Sys.dm_hadr_instance_node_map (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sys.dm_hadr_instance_node_map_TSQL
- sys.sys.dm_hadr_instance_node_map
- sys.dm_hadr_instance_node_map_TSQL
- sys.dm_hadr_instance_node_map
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.sys.dm_hadr_instance_node_map dynamic management view
ms.assetid: ccfaf62c-9f87-43cf-a5e7-8942e91dd041
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e857682f5bb03256b129521840f8969e797e1a5f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535741"
---
# <a name="sysdmhadrinstancenodemap-transact-sql"></a>sys.dm_hadr_instance_node_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Für jede Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , hostet das Replikat einer verfügbarkeitsgruppe, die mit seiner AlwaysOn-verfügbarkeitsgruppe verknüpft ist, gibt den Namen der Windows Server Failover Clustering (WSFC)-Knoten, die Server-Instanz hostet, zurück. Die dynamische Verwaltungssicht dient für Folgendes:  
  
-   Diese dynamische Verwaltungssicht ist nützlich für das Erkennen einer Verfügbarkeitsgruppe mit mehreren Verfügbarkeitsreplikaten, die im selben WSFC-Knoten gehostet werden, der eine nicht unterstützte Konfiguration ist. Letztere könnte nach einem FCI-Failover auftreten, wenn die Verfügbarkeitsgruppe falsch konfiguriert wird. Weitere Informationen finden Sie unter [Failoverclustering und Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
-   Wenn mehrere SQL Server-Instanzen auf demselben WSFC-Knoten gehostet werden, verwendet die Ressourcen-DLL diese dynamische Verwaltungssicht, um die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu bestimmen, mit der eine Verbindung hergestellt werden soll.  
   
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**ag_resource_id**|**nvarchar(256)**|Eindeutige ID der Verfügbarkeitsgruppe als Ressource im WSFC-Cluster.|  
|**instance_name**|**nvarchar(256)**|Name -*Server*/*Instanz*-einer Serverinstanz, die ein Replikat für die verfügbarkeitsgruppe hostet.|  
|**node_name**|**nvarchar(256)**|Der Name des WSFC-Clusterknotens.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen für Always On-Verfügbarkeitsgruppen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
