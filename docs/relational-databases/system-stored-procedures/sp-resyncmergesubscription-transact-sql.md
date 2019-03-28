---
title: Sp_resyncmergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_resyncmergesubscription_TSQL
- sp_resyncmergesubscription
helpviewer_keywords:
- sp_resyncmergesubscription
ms.assetid: e04d464a-60ab-4b39-a710-c066025708e6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63a3ff2cdb075dc8ce48aaa6c6951458d12710b0
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538152"
---
# <a name="spresyncmergesubscription-transact-sql"></a>sp_resyncmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Synchronisiert ein Mergeabonnement in einen bekannten Validierungsstatus neu, der von Ihnen angegeben wird. Dies ermöglicht es Ihnen, die Konvergenz zu erzwingen oder die Abonnementdatenbank mit der Version eines bestimmten Zeitpunkts zu synchronisieren. Dabei kann es sich z. B. um die letzte erfolgreiche Überprüfung oder um ein angegebenes Datum handeln. Die Momentaufnahme wird bei der erneuten Synchronisierung eines Abonnements mithilfe dieser Methode nicht erneut angewendet. Diese gespeicherte Prozedur wird nicht für Momentaufnahme- oder Transaktionsreplikationsabonnements verwendet. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_resyncmergesubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
        , [ @publication = ] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @resync_type = ] resync_type ]  
    [ , [ @resync_date_str = ] resync_date_string ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL. Der Wert NULL ist zulässig, wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird. Wenn die gespeicherte Prozedur auf dem Abonnenten ausgeführt wird, muss ein Verleger angegeben werden.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. Der Wert NULL ist zulässig, wenn die gespeicherte Prozedur auf dem Verleger in der Veröffentlichungsdatenbank ausgeführt wird. Wenn die gespeicherte Prozedur auf dem Abonnenten ausgeführt wird, muss ein Verleger angegeben werden.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung*ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL. Der Wert NULL ist zulässig, wenn die gespeicherte Prozedur auf dem Abonnenten ausgeführt wird. Wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird, muss ein Abonnent angegeben werden.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscription_db* ist **Sysname**, hat den Standardwert NULL. Der Wert NULL ist zulässig, wenn die gespeicherte Prozedur auf dem Abonnenten in der Abonnementdatenbank ausgeführt wird. Wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird, muss ein Abonnent angegeben werden.  
  
`[ @resync_type = ] resync_type` Definiert, wann die erneute Synchronisierung gestartet werden soll. *Resync_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Die Synchronisierung beginnt nach der Anfangsmomentaufnahme. Dies ist die ressourcenintensivste Option, da alle Änderungen seit der Anfangsmomentaufnahme auf den Abonnenten erneut angewendet werden.|  
|**1**|Die Synchronisierung beginnt bei der letzten erfolgreichen Überprüfung. Alle neuen oder unvollständigen Generierungen, die seit der letzten erfolgreichen Überprüfung durchgeführt wurden, werden erneut auf den Abonnenten angewendet.|  
|**2**|Die Synchronisierung beginnt, ab dem Datum im angegebenen *resync_date_str angegeben wird*. Alle neuen oder unvollständigen Generierungen, die seit diesem Datum durchgeführt wurden, werden erneut auf den Abonnenten angewendet.|  
  
`[ @resync_date_str = ] resync_date_string` Legt das Datum an, wann die erneute Synchronisierung gestartet werden soll. *Resync_date_string* ist **nvarchar(30)**, hat den Standardwert NULL. Dieser Parameter wird verwendet, wenn die *Resync_type* ist ein Wert von **2**. Konvertiert das angegebene Datum in den entsprechenden **"DateTime"** Wert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_resyncmergesubscription** wird bei der Mergereplikation verwendet.  
  
 Der Wert **0** für die *Resync_type* Parameter, der alle Änderungen seit der anfangsmomentaufnahme erneut anwendet, ist möglicherweise ressourcenintensiv, aber möglicherweise viel kleiner als eine vollständige erneute Initialisierung. Wenn z. B. die Anfangsmomentaufnahme vor einem Monat erstellt wurde, dann führt dieser Wert dazu, dass die Daten des letzten Monats erneut angewendet werden. Wenn die Anfangsmomentaufnahme 1 Gigabyte (GB) an Daten umfasst, der Umfang der Änderungen des letzten Monats jedoch nur 2 Megabyte (MB), dann ist es effizienter, die Daten und nicht die gesamte 1-GB-Momentaufnahme erneut anzuwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_resyncmergesubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
