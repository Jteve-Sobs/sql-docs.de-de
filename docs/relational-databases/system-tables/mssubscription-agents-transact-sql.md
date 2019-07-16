---
title: MSsubscription_agents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3354f69f92cbbbaa9d60ae8ed6352a0b3be6ab52
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139786"
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscription_agents** -Tabelle wird vom Verteilungs-Agent und Triggern aktualisierbarer Abonnements verwendet, um Abonnementeigenschaften nachzuverfolgen. Diese Tabelle wird in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID der Zeile.|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**publication**|**sysname**|Der Name der Veröffentlichung.|  
|**subscription_type**|**int**|Der Abonnementtyp:<br /><br /> 0 = Push.<br /><br /> 1 = Pullabonnement.<br /><br /> 2 = Anonymes Pullabonnement.|  
|**queue_id**|**sysname**|Die ID des dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Warteschlangen auf dem Verleger. *Queue_id* nastaven NA hodnotu **SQL** für SQL-basierte verzögerte Update.|  
|**update_mode**|**tinyint**|Typ des Aktualisierens:<br /><br /> **0** = schreibgeschützt.<br /><br /> **1** = sofortiges Update.<br /><br /> **2** = verzögertes Update über Message Queuing.<br /><br /> **3** = sofortiges Aktualisieren mit verzögertem Aktualisieren mithilfe von Message Queuing.<br /><br /> **4** = verzögertes Update über eine SQL Server-Warteschlange.<br /><br /> **5** = sofortiges Aktualisieren mit Failover Update über eine Warteschlange mithilfe von SQL Server-Warteschlange.|  
|**failover_mode**|**bit**|Wenn für das Update ein Failovertyp angegeben war, ist dies der gewählte Failovertyp:<br /><br /> **0** = sofortiges Update verwendet wird. Failover ist nicht aktiviert.<br /><br /> **1** = verzögertes Update verwendet wird. Failover ist aktiviert. Die für eine Failoversituation verwendete Warteschlange angegeben ist, der *Update_mode* Wert.|  
|**spid**|**int**|Die Systemprozess-ID der Verbindung, die von dem Verteilungs-Agent verwendet wird, der derzeit ausgeführt wird oder gerade ausgeführt wurde.|  
|**login_time**|**datetime**|Das Datum und die Uhrzeit der Verbindung des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde.|  
|**allow_subscription_copy**|**bit**|Gibt an, ob die Abonnementdatenbank kopiert werden darf oder nicht.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary(16)**|Der eindeutige Bezeichner, der die Version eines angefügten Abonnements darstellt.|  
|**last_sync_status**|**int**|Der letzte Ausführungsstatus des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde. Der Status kann Folgendes sein:<br /><br /> **1** = gestartet.<br /><br /> **2** = war erfolgreich.<br /><br /> **3** = wird ausgeführt.<br /><br /> **4** = im Leerlauf.<br /><br /> **5** = wiederholen.<br /><br /> **6** = Fehler.|  
|**last_sync_summary**|**sysname**|Die letzte Meldung des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde. Der Status kann Folgendes sein:<br /><br /> **Gestartet.**<br /><br /> **War erfolgreich.**<br /><br /> **In Bearbeitung.**<br /><br /> **Im Leerlauf.**<br /><br /> **Versuchen Sie erneut.**<br /><br /> **Ein Fehler auf.**|  
|**last_sync_time**|**datetime**|Das Datum und Uhrzeit der Erstellung der *Last_sync_summary* und *Last_sync_status* Spalten aktualisiert wurden. Verteilungs-Agents für Pull- oder anonyme Abonnements, die als Aufträge des SQL Server-Agent-Diensts ausgeführt werden, aktualisieren diese Spalten nicht. Die Verlaufsinformationen werden in diesem Fall stattdessen in der Auftragsverlaufstabelle protokolliert.|  
|**queue_server**|**sysname**|Nur interne Verwendung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
