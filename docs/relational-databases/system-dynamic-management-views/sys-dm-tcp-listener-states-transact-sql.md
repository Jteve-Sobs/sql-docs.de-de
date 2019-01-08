---
title: dm_tcp_listener_states (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tcp_listener_states
- dm_tcp_listener_states
- sys.dm_tcp_listener_states_TSQL
- dm_tcp_listener_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.dm_tcp_listener_states dynamic management view
ms.assetid: 9997ffed-a4c1-428f-8bac-3b9e4b16d7cf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b69bfb4da1bf20a8d74f5adcda44e55954bbdf65
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52409637"
---
# <a name="sysdmtcplistenerstates-transact-sql"></a>sys.dm_tcp_listener_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile zurück, die Informationen zum dynamischen Status für jeden TCP-Listener enthält.  
  
> [!NOTE]
> Der Verfügbarkeitsgruppenlistener kann dem gleichen Port wie der Listener der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauschen. In diesem Fall sind die Listener getrennt aufgeführt, das Gleiche gilt für einen Service Broker-Listener.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**listener_id**|**int**|Interne ID des Listeners Lässt keine NULL-Werte zu.<br /><br /> Der Primärschlüssel.|  
|**ip_address**|**nvarchar48**|Die Listener-IP-Adresse, die online ist und an der gelauscht wird. Entweder ist IPv4 oder IPv6 zulässig. Wenn ein Listener beide Typen von Adressen besitzt, sind sie getrennt aufgeführt. Ein IPv4-Platzhalter wird als "0.0.0.0" angezeigt. Ein IPv6-Platzhalter wird als "::".<br /><br /> Lässt keine NULL-Werte zu.|  
|**is_ipv4**|**bit**|Der Typ der IP-Adresse.<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
|**port**|**int**|Die Nummer des Ports, an dem der Listener lauscht. Lässt keine NULL-Werte zu.|  
|**type**|**tinyint**|Der Typ des Listeners. Folgende Werte sind möglich:<br /><br /> 0 = [!INCLUDE[tsql](../../includes/tsql-md.md)]<br /><br /> 1 = Service Broker<br /><br /> 2 = Datenbankspiegelung<br /><br /> Lässt keine NULL-Werte zu.|  
|**type_desc**|**nvarchar(20)**|Beschreibung der **Typ**, eine von:<br /><br /> TSQL<br /><br /> SERVICE_BROKER<br /><br /> DATABASE_MIRRORING<br /><br /> Lässt keine NULL-Werte zu.|  
|**state**|**tinyint**|Der Status des Verfügbarkeitsgruppenlisteners. Folgende Werte sind möglich:<br /><br /> 1 = Online. Der Listener lauscht auf Anforderungen und verarbeitet sie.<br /><br /> 2 = Ausstehender Neustart. Der Listener ist offline, ein Neustart steht aus.<br /><br /> Wenn der Verfügbarkeitsgruppenlistener an dem gleichen Port wie die Serverinstanz lauscht, haben diese zwei Listener immer den gleichen Status.<br /><br /> Lässt keine NULL-Werte zu.<br /><br /> Hinweis: Die Werte in dieser Spalte stammen aus dem TSD_listener-Objekt. Die Spalte unterstützt keine Status "offline", da bei der TDS_listener offline ist, es für Status abgefragt werden kann.|  
|**state_desc**|**nvarchar(16)**|Beschreibung der **Zustand**, eine von:<br /><br /> ONLINE<br /><br /> PENDING_RESTART<br /><br /> Lässt keine NULL-Werte zu.|  
|**start_time**|**datetime**|Der Zeitstempel, der angibt, wann der Listener gestartet wurde. Lässt keine NULL-Werte zu.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
