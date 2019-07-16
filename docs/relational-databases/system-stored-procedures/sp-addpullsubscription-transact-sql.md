---
title: Sp_addpullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords:
- sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea87c5e83b5be3945469ddb0e32c9f8158a5e116
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022440"
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt ein Pullabonnement einer Momentaufnahmen- oder Transaktionsveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Datenbank ausgeführt, für die das Pullabonnement erstellt werden soll.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addpullsubscription [ @publisher= ] 'publisher'  
    [ , [ @publisher_db= ] 'publisher_db' ]  
        , [ @publication= ] 'publication'  
    [ , [ @independent_agent= ] 'independent_agent' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @update_mode= ] 'update_mode' ]  
    [ , [ @immediate_sync = ] immediate_sync ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. *Publisher_db* wird von Oracle-Verlegern ignoriert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @independent_agent = ] 'independent_agent'` Gibt an, ob ein eigenständiger Verteilungs-Agent für diese Veröffentlichung. *Independent_agent* ist **nvarchar(5)** , hat den Standardwert "true". Wenn **"true"** , ein eigenständiger Verteilungs-Agent für diese Veröffentlichung vorhanden ist. Wenn **"false"** , es gibt für jedes Verlegerdatenbank und Abonnentendatenbank-Paar ein Verteilungs-Agent. *Independent_agent* ist eine Eigenschaft der Veröffentlichung und muss den gleichen Wert aufweisen, wie sie auf dem Verleger übereinstimmt.  
  
`[ @subscription_type = ] 'subscription_type'` Ist der Typ des Abonnements. *Subscription_type* ist **vom Datentyp nvarchar(9)** , hat den Standardwert **anonyme**. Geben Sie einen Wert von **Pull** für *Subscription_type*, es sei denn, Sie möchten ein Abonnement erstellen, ohne das Abonnement auf dem Verleger zu registrieren. Sie müssen in diesem Fall geben Sie den Wert **anonyme**. Dies ist notwendig für Fälle, in denen Sie während der Abonnementkonfiguration keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindung mit dem Verleger herstellen können.  
  
`[ @description = ] 'description'` Ist die Beschreibung der Veröffentlichung. *Beschreibung* ist **nvarchar(100)** , hat den Standardwert NULL.  
  
`[ @update_mode = ] 'update_mode'` Ist der Typ des Updates. *Update_mode* ist **nvarchar(30)** , und kann einen der folgenden Werte.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Schreibgeschützt** (Standard)|Das Abonnement ist schreibgeschützt. Änderungen am Abonnenten werden nicht an den Verleger zurückgesendet. Sollte verwendet werden, wenn Updates nicht auf dem Abonnenten vorgenommen werden.|  
|**synctran**|Aktiviert die Unterstützung für das sofortige Aktualisieren von Abonnements.|  
|**in der Warteschlange tran**|Aktiviert das verzögerte Aktualisieren über eine Warteschlange für das Abonnement. Daten können auf dem Abonnenten geändert werden; die Änderungen werden in einer Warteschlange gespeichert und an den Verleger weitergegeben.|  
|**failover**|Aktiviert das sofortige Aktualisieren für das Abonnement, wobei als Failover das verzögerte Aktualisieren über eine Warteschlange verwendet wird. Daten können auf dem Abonnenten geändert werden; die Änderungen werden sofort an den Verleger weitergegeben. Wenn der Verleger und der Abonnent nicht verbunden sind, können Datenänderungen auf dem Abonnenten in einer Warteschlange gespeichert werden, bis Abonnent und Verleger erneut verbunden sind.|  
|**in der Warteschlange failover**|Ermöglicht das Abonnement als Update über eine Warteschlange, mit der Möglichkeit des Wechsels zum sofortigen Updatemodus. Daten können auf dem Abonnenten geändert und in einer Warteschlange gespeichert werden, bis eine Verbindung zwischen dem Abonnenten und dem Verleger hergestellt wird. Wenn eine kontinuierliche Verbindung hergestellt wird, kann der Updatemodus in den sofortigen Updatemodus geändert werden. *Nicht für Oracle-Verleger unterstützt*.|  
  
`[ @immediate_sync = ] immediate_sync` Ist an, ob die Synchronisierungsdateien erstellt oder neu erstellt jedes Mal, wenn der Momentaufnahme-Agent ausgeführt wird. *Immediate_sync* ist **Bit** hat den Standardwert 1, und muss festgelegt werden, um den gleichen Wert wie *Immediate_sync* in **Sp_addpublication**. *Immediate_sync* ist eine Eigenschaft der Veröffentlichung und muss den gleichen Wert aufweisen, wie sie auf dem Verleger übereinstimmt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addpullsubscription** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
> [!IMPORTANT]  
>  Bei Abonnements mit verzögertem Update über eine Warteschlange verwenden Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für Verbindungen mit Abonnenten. Geben Sie für die Verbindung zu den einzelnen Abonnenten jeweils ein anderes Konto an. Beim Erstellen eines Pullabonnements, das verzögerte Updates über eine Warteschlange unterstützt, legt die Replikation immer die Verwendung der Windows-Authentifizierung für die Verbindung fest (für Pullabonnements kann die Replikation nicht auf Metadaten beim Abonnenten zugreifen, die für die Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung erforderlich sind). In diesem Fall führen Sie [Sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) so ändern Sie die zu verwendende Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, nachdem das Abonnement konfiguriert wurde.  
  
 Wenn die [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) Tabelle ist nicht vorhanden, auf dem Abonnenten **Sp_addpullsubscription** wird erstellt. Es fügt auch eine Zeile in der [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) Tabelle. Bei Pullabonnements müssen Sie [Sp_addsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) zuerst auf dem Verleger aufgerufen werden soll.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addpullsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [Sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
