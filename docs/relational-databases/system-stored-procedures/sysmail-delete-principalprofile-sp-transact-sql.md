---
title: Sysmail_delete_principalprofile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae63fabdca36e70daa6da28daa136a5dfcec8e1f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527782"
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt für einen Datenbankbenutzer oder eine Rolle die Berechtigung zum Verwenden eines öffentlichen oder privaten Datenbank-E-Mail-Profils.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @principal_id = ] principal_id` Die ID des Datenbankbenutzers oder der Rolle in der **Msdb** -Datenbank für die Zuordnung zu löschen. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Um ein öffentliches Profil in ein privates Profil zu um vereinfachen, geben die Prinzipal-ID **0** oder den Prinzipalnamen **'public'**. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @principal_name = ] 'principal_name'` Der Name des Datenbankbenutzers oder der Rolle in der **Msdb** -Datenbank für die Zuordnung zu löschen. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Um ein öffentliches Profil in ein privates Profil zu um vereinfachen, geben die Prinzipal-ID **0** oder den Prinzipalnamen **'public'**. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
`[ @profile_id = ] profile_id` Ist die ID des Profils für die Zuordnung zu löschen. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'` Ist der Name des Profils für die Zuordnung zu löschen. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein öffentliches Profil in ein privates Profil umgewandelt werden, geben **'public'** für den Benutzerprinzipalnamen oder **0** Prinzipal-ID.  
  
 Gehen Sie vorsichtig vor, wenn Sie für einen Benutzer die Berechtigungen für das private Standardprofil entfernen oder das öffentliche Standardprofil entfernen. Wenn kein Standardprofil verfügbar ist **Sp_send_dbmail** erfordert den Namen eines Profils als Argument. Entfernen eines Standardprofils aus diesem Grund kann verursachen Aufrufe der **Sp_send_dbmail** fehlschlägt. Weitere Informationen finden Sie unter [Sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Die gespeicherte Prozedur **Sysmail_delete_principalprofile_sp** befindet sich in der **Msdb** -Datenbank und im Besitz der **Dbo** Schema. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Zuordnung zwischen dem Profil löschen **AdventureWorks Administrator** und den Anmeldenamen **"applicationuser"** in die **Msdb** Datenbank.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Configuration Objects](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-e-Mails gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
