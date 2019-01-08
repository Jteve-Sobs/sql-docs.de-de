---
title: Sp_addmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98d31c0d4895573059104d43a1ebddd879ba1967
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52813122"
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt ein Pullabonnement zu einer Mergeveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepullsubscription [ @publication= ] 'publication'   
    [ , [ @publisher= ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @subscriber_type= ] 'subscriber_type' ]   
    [ , [ @subscription_priority= ] subscription_priority ]   
    [ , [ @sync_type= ] 'sync_type' ]   
    [ , [ @description= ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publisher=**] **"**_Verleger_**"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert der Name des lokalen Servers. Der Verleger muss ein gültiger Server sein.  
  
 [  **@publisher_db =**] **"**_Publisher_db_**"**  
 Der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_type=**] **"**_Subscriber_type_**"**  
 Der Typ des Abonnenten. *subscriber_type kann* ist **nvarchar(15)**, und kann **globale**, **lokalen** oder **anonyme**. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden lokale Abonnements als Clientabonnements bezeichnet und globale Abonnements als serverabonnements bezeichnet.  
  
 [  **@subscription_priority=**] *Subscription_priority*  
 Die Abonnementpriorität. *Subscription_priority*ist **echte**, hat den Standardwert NULL. Für lokale und anonyme Abonnements, die Priorität ist **0,0**. Die Priorität wird vom Standardresolver verwendet, um einen Gewinner zu ermitteln, wenn Konflikte erkannt werden. Für globale Abonnenten muss die Abonnementpriorität kleiner als 100 sein. Dieser Wert gibt die Priorität des Verlegers an.  
  
 [  **@sync_type=**] **"**_Sync_type_**"**  
 Der Synchronisierungstyp des Abonnements. *Sync_type*ist **nvarchar(15)**, hat den Standardwert **automatische**. Kann **automatische** oder **keine**. Wenn **automatische**, das Schema und die Ausgangsdaten für veröffentlichte Tabellen zuerst an den Abonnenten übertragen werden. Wenn **keine**, es wird davon ausgegangen, dass der Abonnent hat bereits das Schema und die Ausgangsdaten für veröffentlichte Tabellen. Systemtabellen und Daten werden immer übertragen.  
  
> [!NOTE]  
>  Es wird nicht empfohlen, geben Sie einen Wert **keine**.  
  
 [  **@description=**] **"**_Beschreibung_**"**  
 Eine kurze Beschreibung dieses Pullabonnements. *Beschreibung*ist **nvarchar(255)**, hat den Standardwert NULL. Dieser Wert wird angezeigt, vom Replikationsmonitor in der **Anzeigenamen** Spalte, die zum Sortieren von Abonnements für eine überwachte Veröffentlichung verwendet werden kann.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addmergepullsubscription** wird für die Mergereplikation verwendet.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent zum Synchronisieren des Abonnements, die [Sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) gespeicherte Prozedur muss ausgeführt werden, auf dem Abonnenten ein Agent und der Auftrag zum Synchronisieren mit der Veröffentlichung zu erstellen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addmergepullsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [Sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [Sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [Sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [Sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
