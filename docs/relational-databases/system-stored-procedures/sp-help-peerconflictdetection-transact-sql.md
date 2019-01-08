---
title: Sp_help_peerconflictdetection (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_peerconflictdetection
- sp_help_peerconflictdetection_TSQL
helpviewer_keywords:
- sp_help_peerconflictdetection
ms.assetid: 59e04107-5eaa-44a1-beb6-ac4f2dbbcb28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4fa967ec7809b8f638d9d032912969f24df1258
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770012"
---
# <a name="sphelppeerconflictdetection-transact-sql"></a>sp_help_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen über die Konflikterkennungseinstellungen für eine Veröffentlichung zurück, die Teil einer Peer-zu-Peer-Transaktionsreplikationstopologie ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_peerconflictdetection [ @publication = ] 'publication'  
    [ ,[ @timeout = ] timeout ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication= ] '*publication*'  
 Der Name der Veröffentlichung, für die Informationen zurückgegeben werden sollen. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ @timeout= ] *timeout*  
 Gibt den Zeitraum in Sekunden an, nachdem für die Prozedur ein Timeout eintritt, während auf die Antwort von jedem Knoten in der Topologie gewartet wird. Wenn die Topologie einen schreibgeschützten Abonnenten enthält, ist die Angabe eines Timeoutwerts nicht gültig. Schreibgeschützte Abonnenten reagieren nie auf einen Aufruf von dieser Prozedur. *Timeout* ist **Int**, hat den Standardwert 60.  
  
## <a name="result-sets"></a>Resultsets  
 sp_help_peerconflictdetection gibt drei Resultsets zurück. Diese Ergebnisse sind in den folgenden Themen dokumentiert:  
  
-   [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)  
  
-   [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)  
  
-   [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md)  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_help_peerconflictdetection wird in der Peer-zu-Peer-Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner.  
  
## <a name="see-also"></a>Siehe auch  
 [Konflikterkennung bei der Peer-zu-Peer-Replikation](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
