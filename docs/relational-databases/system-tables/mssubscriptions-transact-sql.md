---
title: MSsubscriptions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: stevestein
ms.author: sstein
ms.openlocfilehash: 51ab87c830d27a2749fdb332c5a13a5b5dd85542
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139710"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscriptions** -Tabelle enthält eine Zeile für jede in einem Abonnement, das vom lokalen Verteiler bediente Artikel veröffentlicht. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**article_id**|**int**|Die ID des Artikels.|  
|**subscriber_id**|**smallint**|Die ID des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der Abonnementdatenbank.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> **0** = Push.<br /><br /> **1** = Pullabonnement.<br /><br /> **2** = anonym.|  
|**sync_type**|**tinyint**|Typ der Synchronisierung:<br /><br /> **1** = Automatic.<br /><br /> **2** = keine Synchronisierung.|  
|**status**|**tinyint**|Status des Abonnements:<br /><br /> **0** = inaktiv.<br /><br /> **1** = abonniert.<br /><br /> **2** = aktiv.|  
|**subscription_seqno**|**varbinary(16)**|Die Sequenznummer der Momentaufnahmetransaktion.|  
|**snapshot_seqno_flag**|**bit**|Gibt die Quelle an die Sequenznummer der Snapshot-Transaktion ein Wert von **1** bedeutet, dass **Subscription_seqno** die momentaufnahmesequenznummer ist.|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**subscription_time**|**datetime**|Nur interne Verwendung.|  
|**loopback_detection**|**bit**|Gilt für Abonnements, die Teil einer bidirektionalen Transaktionsreplikationstopologie sind. Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **1** unterstützt = sendet nicht zurück.<br /><br /> **0** = sendet zurück.<br /><br /> Hinweis: Diese Spalte wird nur für Abwärtskompatibilität mit in die bidirektionale Replikation-Funktionalität unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. In höheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte stattdessen eine Peer-zu-Peer-Replikation verwendet werden. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|**agent_id**|**int**|Die ID der Momentaufnahme.|  
|**update_mode**|**tinyint**|Der Typ des Updates.|  
|**publisher_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion auf dem Verleger für dieses Abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Die Sequenznummer, die den Abschluss der Verarbeitung der gleichzeitigen Momentaufnahme anzeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
