---
title: Sp_reinitsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b9d03099ae48bf463df82d1392e97d4729ec518a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528782"
---
# <a name="spreinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Kennzeichnet das Abonnement für die erneute Initialisierung. Diese gespeicherte Prozedur wird auf dem Verleger für Pushabonnements ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert all.  
  
`[ @article = ] 'article'` Ist der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert all. Für eine sofort aktualisierbare Veröffentlichung *Artikel* muss **alle**ist, andernfalls die gespeicherte Prozedur überspringt die Veröffentlichung und meldet einen Fehler.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat keinen Standardwert.  
  
`[ @destination_db = ] 'destination_db'` Ist der Name der Zieldatenbank. *Destination_db* ist **Sysname**, hat den Standardwert all.  
  
`[ @for_schema_change = ] 'for_schema_change'` Gibt an, ob eine erneute Initialisierung als Ergebnis einer schemaänderung in der Veröffentlichungsdatenbank. *For_schema_change* ist **Bit**, hat den Standardwert 0. Wenn **0**, aktive Abonnements für Veröffentlichungen, die sofortiges Aktualisieren zulassen, werden erneut aktiviert werden, solange die gesamte Veröffentlichung, nicht nur einige Artikel darin, erneut initialisiert werden. Die erneute Initialisierung wird demnach als Ergebnis von Schemaänderungen initiiert. Wenn **1**, aktive Abonnements werden nicht erneut aktiviert, bis der Momentaufnahme-Agent ausgeführt wird.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber.  
  
`[ @ignore_distributor_failure = ] ignore_distributor_failure` Lässt die erneute Initialisierung auch, wenn der Verteiler nicht vorhanden ist oder offline ist. *Ignore_distributor_failure* ist **Bit**, hat den Standardwert 0. Wenn **0**, erneute Initialisierung erfolglos, wenn der Verteiler nicht vorhanden ist oder offline ist.  
  
`[ @invalidate_snapshot = ] invalidate_snapshot` Erklärt die vorhandene veröffentlichungsmomentaufnahme für ungültig. *Invalidate_snapshot* ist **Bit**, hat den Standardwert 0. Wenn **1**, eine neue Momentaufnahme für die Veröffentlichung generiert wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_reinitsubscription** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_reinitsubscription** wird nicht für die Peer-zu-Peer-Transaktionsreplikation unterstützt.  
  
 Für Abonnements, bei denen die Anfangsmomentaufnahme automatisch angewendet wird und bei denen die Veröffentlichung keine aktualisierbaren Abonnements zulässt, muss der Momentaufnahme-Agent ausgeführt werden, nachdem diese gespeicherte Prozedur ausgeführt wird, sodass Programmdateien für das Schema- und Massenkopieren vorbereitet werden und die Verteilungs-Agents in der Lage sind, die Abonnements neu zu synchronisieren.  
  
 Für Abonnements, bei denen die Anfangsmomentaufnahme automatisch angewendet wird und bei denen die Veröffentlichung aktualisierbare Abonnements zulässt, führt der Verteilungs-Agent eine erneute Synchronisierung für das Abonnement durch, indem die neuesten Programmdateien für das Schema- und Massenkopieren verwendet werden, die zuvor vom Momentaufnahme-Agent erstellt wurden. Der Verteilungs-Agent synchronisiert das Abonnement sofort, nachdem der Benutzer führt **Sp_reinitsubscription**, wenn der Verteilungs-Agent nicht Synchronisierung kann auftreten, nachdem die Nachricht Intervall (ausgelastet ist, andernfalls Verteilungs-Agent-Befehlszeilenparameter angegeben: **MessageInterval**).  
  
 **Sp_reinitsubscription** hat keine Auswirkungen auf Abonnements, in denen die anfangsmomentaufnahme manuell angewendet wird.  
  
 Übergeben Sie zur neusynchronisierung anonymer Abonnements einer Veröffentlichung **alle** oder NULL als *Abonnenten*.  
  
 Die Transaktionsreplikation unterstützt die erneute Initialisierung von Abonnements auf Artikelebene. Die Momentaufnahme des Artikels wird während der nächsten Synchronisierung erneut auf den Abonnenten angewendet, nachdem der Artikel für die erneute Initialisierung markiert wurde. Wenn jedoch abhängige Artikel vorhanden sind, die von demselben Abonnenten abonniert werden, kann die erneute Anwendung der Momentaufnahme auf den Artikel möglicherweise einen Fehler erzeugen, wenn in der Veröffentlichung nicht auch abhängige Artikel unter bestimmten Umständen automatisch erneut initialisiert werden:  
  
-   Wenn 'drop' als Vorabbefehl vor der Erstellung des entsprechenden Artikels verwendet wird, werden Artikel für schemagebundene Sichten und schemagebundene gespeicherte Prozeduren für das Basisobjekt des Artikels ebenfalls für die erneute Initialisierung markiert.  
  
-   Wenn die Schemaoption für den Artikel das Erstellen von Skripts für die deklarative referenzielle Integrität der Primärschlüssel einbezieht, werden Artikel, die über Basistabellen mit Fremdschlüsselbeziehungen zu Basistabellen des erneut initialisierten Artikels verfügen, ebenfalls für die erneute Initialisierung markiert.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** , den Mitgliedern der festen Serverrolle die **Db_owner** feste Datenbankrolle oder der Ersteller des Abonnements kann ausführen **Sp_reinitsubscription** .  
  
## <a name="see-also"></a>Siehe auch  
 [Erneutes Initialisieren eines Abonnements](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
