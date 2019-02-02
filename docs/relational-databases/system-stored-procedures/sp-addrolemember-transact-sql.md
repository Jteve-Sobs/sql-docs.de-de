---
title: Sp_addrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrolemember_TSQL
- sp_addrolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrolemember
ms.assetid: a583c087-bdb3-46d2-b9e5-3921b3e6d10b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d7b47670d56ab916a8c2f263f9ddee3dc85c0a6
ms.sourcegitcommit: c4870cb5bebf9556cdb4d8b35ffcca265fb07862
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652539"
---
# <a name="spaddrolemember-transact-sql"></a>sp_addrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Fügt einer Datenbankrolle in der aktuellen Datenbank einen Datenbankbenutzer, eine Datenbankrolle, einen Windows-Anmeldenamen oder eine Windows-Gruppe hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
sp_addrolemember [ @rolename = ] 'role', [ @membername = ] 'security_account'  

```    
  
## <a name="arguments"></a>Argumente  
 [ @rolename=] '*Rolle*"  
 Der Name der Datenbankrolle in der aktuellen Datenbank. *role* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [ @membername=] '*Security_account*"  
 Das Sicherheitskonto, das der Rolle hinzugefügt wird. *Security_account* ist eine **Sysname**, hat keinen Standardwert. *Security_account* kann ein Datenbankbenutzer, Datenbankrolle, Windows-Anmeldename oder Windows-Gruppe sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Ein Mitglied, das einer Rolle mithilfe von sp_addrolemember hinzugefügt wird, erbt die Berechtigungen der Rolle. Falls das neue Mitglied ein Prinzipal auf Windows-Ebene ohne einen entsprechenden Datenbankbenutzer ist, wird ein Datenbankbenutzer erstellt, jedoch möglicherweise nicht vollständig der Anmeldung zugeordnet. Überprüfen Sie stets, ob die Anmeldung vorhanden ist und Zugriff auf die Datenbank hat.  
  
 Eine Rolle kann sich selbst nicht als Mitglied enthalten. Diese ringförmigen Definitionen sind ungültig, auch wenn die Mitgliedschaft nur indirekt durch eine Zwischenmitgliedschaft impliziert ist.  
  
 Sp_addrolemember kann nicht auf einer festen Datenbankrolle, feste Serverrolle oder Dbo zu einer Rolle hinzufügen. Sp_addrolemember kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Verwenden Sie ausschließlich sp_addrolemember, um einer Datenbankrolle ein Mitglied hinzuzufügen. Verwenden Sie ein Mitglied einer Serverrolle hinzuzufügen, [Sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Für das Hinzufügen von Mitgliedern zu flexiblen Datenbankrollen muss eine der folgenden Bedingungen erfüllt sein:  
  
-   Mitgliedschaft in der festen Datenbankrolle Db_securityadmin oder Db_owner.  
  
-   Mitgliedschaft in der Rolle, die die Rolle besitzt.  
  
-   **ALTER ANY ROLE** Berechtigung oder **ALTER** Berechtigung für die Rolle.  
  
 Zum Hinzufügen von Mitgliedern zu festen Datenbankrollen ist die Mitgliedschaft in der festen Datenbankrolle db_owner erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-adding-a-windows-login"></a>A. Hinzufügen eines Windows-Anmeldenamens  
 Im folgenden Beispiel wird die Windows-Anmeldung `Contoso\Mary5` auf die `AdventureWorks2012` Datenbank als Benutzer `Mary5`. Der Benutzer `Mary5` wird dann der `Production`-Rolle hinzugefügt.  
  
> [!NOTE]  
>  Da `Contoso\Mary5` als Datenbankbenutzer `Mary5` in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank bekannt ist, muss der Benutzername `Mary5` angegeben werden. Die Anweisung führt zu einem Fehler, es sei denn, es ist ein Anmeldename `Contoso\Mary5` vorhanden. Testen Sie dies, indem Sie einen Anmeldenamen Ihrer Domäne verwenden.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE USER Mary5 FOR LOGIN [Contoso\Mary5] ;  
GO  
```  
  
### <a name="b-adding-a-database-user"></a>B. Hinzufügen eines Datenbankbenutzers  
 Im folgenden Beispiel wird der Datenbankbenutzer `Mary5` der `Production`-Datenbankrolle in der aktuellen Datenbank hinzugefügt.  
  
```  
EXEC sp_addrolemember 'Production', 'Mary5';  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-adding-a-windows-login"></a>C. Hinzufügen eines Windows-Anmeldenamens  
 Im folgenden Beispiel wird die Anmeldung `LoginMary` auf die `AdventureWorks2008R2` Datenbank als Benutzer `UserMary`. Der Benutzer `UserMary` wird dann der `Production`-Rolle hinzugefügt.  
  
> [!NOTE]  
>  Da die Anmeldung `LoginMary` wird bezeichnet als Datenbankbenutzer `UserMary` in die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Datenbank, den Benutzernamen `UserMary` muss angegeben werden. Die Anweisung führt zu einem Fehler, es sei denn, es ist ein Anmeldename `Mary5` vorhanden. Anmeldungen und Benutzern, in der Regel den gleichen Namen haben. Dieses Beispiel verwendet unterschiedliche Namen, um die Aktionen, die Auswirkungen auf die Anmeldung im Vergleich zu den Benutzer zu unterscheiden.  
  
```  
-- Uses AdventureWorks  
  
CREATE USER UserMary FOR LOGIN LoginMary ;  
GO  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
### <a name="d-adding-a-database-user"></a>D. Hinzufügen eines Datenbankbenutzers  
 Im folgenden Beispiel wird der Datenbankbenutzer `UserMary` der `Production`-Datenbankrolle in der aktuellen Datenbank hinzugefügt.  
  
```  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  
