---
title: Sp_dropmergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords:
- sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acb16727506952146ace1383c8d36808d7c22a73
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791502"
---
# <a name="spdropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht ein Abonnement für eine Mergeveröffentlichung und den zugehörigen Merge-Agent. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=** ] **"***Veröffentlichung***"**  
 Ist der Veröffentlichungsname. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Die Veröffentlichung muss bereits vorhanden ist und den Regeln für Bezeichner entsprechen.  
  
 [  **@subscriber=**] **"***Abonnenten***"**  
 Der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_db=** ] **"***Subscriber_db***"**  
 Ist der Name der Abonnementdatenbank. *subscription_database eingestellt wird*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscription_type=** ] **"***Subscription_type***"**  
 Ist der Typ des Abonnements. *Subscription_type*ist **nvarchar(15)**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Alle**|Push-, Pull- und anonyme Abonnements.|  
|**Anonyme**|Anonymes Abonnement.|  
|**Pushbenachrichtigungen**|Pushabonnement.|  
|**Pull**|Pullabonnement.|  
|**both** (Standard)|Sowohl Push- als auch Pullabonnements.|  
  
 [  **@ignore_distributor =** ] *Ignore_distributor*  
 Gibt an, ob diese gespeicherte Prozedur ausgeführt wird, ohne eine Verbindung mit dem Verteiler herzustellen. *Ignore_distributor* ist **Bit**, hat den Standardwert **0**. Mit diesem Parameter kann ein Abonnement gelöscht werden, ohne Cleanuptasks auf dem Verteiler auszuführen. Er erweist sich auch bei einer etwaigen Neuinstallation des Verteilers als hilfreich.  
  
 [  **@reserved=** ] *reserviert*  
 Ist für die zukünftige Verwendung reserviert. *reservierte* ist **Bit**, hat den Standardwert **0**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropmergesubscription** wird bei der Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_dropmergesubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Pushabonnements](../../relational-databases/replication/delete-a-push-subscription.md)   
 [Löschen eines Pullabonnements](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [Sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [Sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [Sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
