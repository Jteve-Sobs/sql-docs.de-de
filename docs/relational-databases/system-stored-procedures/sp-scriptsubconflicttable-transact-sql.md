---
title: Sp_scriptsubconflicttable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptsubconflicttable
- sp_scriptsubconflicttable_TSQL
helpviewer_keywords:
- sp_scriptsubconflicttable
ms.assetid: 13867145-3dad-47a4-8d50-a65175418479
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33aa0ee68e649dbf1fd2d0fa7373cab64560fa5d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816202"
---
# <a name="spscriptsubconflicttable-transact-sql"></a>sp_scriptsubconflicttable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert ein Skript zum Erstellen einer Konflikttabelle auf dem Abonnenten für einen gegebenen Artikel in einem Abonnement mit Warteschlange. Das generierte Skript wird beim Abonnenten mit der Abonnementdatenbank ausgeführt. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_scriptsubconflicttable [@publication =] 'publication'    , [@article =] 'article'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, die den Artikel enthält. Der Name muss in der Datenbank eindeutig sein. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"***Artikel***"**  
 Der Name des Artikels im Abonnement. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Befehlstext**|**nvarchar(4000)**|Gibt das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skript für die Erstellung der Konflikttabelle beim Abonnementen für den Artikel in dem Abonnement mit Warteschlange zurück. Dieses Skript wird beim Abonnementen in der Abonnementendatenbank ausgeführt.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_scriptsubconflicttable** für Abonnenten, die über Abonnements verfügen, in denen die anfangsmomentaufnahme manuell angewendet werden. Bei der Konflikttabelle handelt es sich um eine optionale Tabelle beim Abonnementen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_scriptsubconflicttable**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konflikterkennung und -lösung beim verzögerten Update über eine Warteschlange](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
