---
title: "' sp_migrate_user_to_contained ' (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 06/11/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_migrate_user_to_contained
- sp_migrate_user_to_contained_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_migrate_user_to_contained
ms.assetid: b3a49ff6-46ad-4ee7-b6fe-7e54213dc33e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5bcafb24313851f58fd18fc19ebabd0ee98f6dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022333"
---
# <a name="spmigrateusertocontained-transact-sql"></a>sp_migrate_user_to_contained (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Konvertiert einen Datenbankbenutzer, der mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft ist, in den Benutzer einer enthaltenen Datenbank mit Kennwort. In einer eigenständigen Datenbank können Sie mit diesem Verfahren Abhängigkeiten für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernen, in der die Datenbank installiert ist. **' sp_migrate_user_to_contained '** trennt den Benutzer aus der ursprünglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung, damit Einstellungen wie Kennwort und Standardsprache für die eigenständige Datenbank separat verwaltet werden können. **' sp_migrate_user_to_contained '** kann verwendet werden, vor dem Verschieben der eigenständigen Datenbank in eine andere Instanz von der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , Abhängigkeiten auf dem aktuellen zu beseitigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldungen-Instanz.  
  
> [!NOTE]
> Achten Sie bei Verwendung **Sp_migrate_user_to_contained**, wie Sie nicht die Wirkung zu stornieren können. Dieses Verfahren wird nur in einer eigenständigen Datenbank verwendet. Weitere Informationen finden Sie unter [Contained Databases](../../relational-databases/databases/contained-databases.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_migrate_user_to_contained [ @username = ] N'user' ,   
    [ @rename = ] { N'copy_login_name' | N'keep_name' } ,   
    [ @disablelogin = ] { N'disable_login' | N'do_not_disable_login' }   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@username =** ] **N'***Benutzer***"**  
 Der Name eines Benutzers in der aktuellen eigenständigen Datenbank, der mit einem authentifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft ist. Der Wert ist **Sysname**, hat den Standardwert **NULL**.  
  
 [ **@rename =** ] **N'***Copy_login_name***"**  | **N'***Keep_name***"**  
 Wenn Sie ein Datenbankbenutzer basierend auf einer Anmeldung auf einen anderen Benutzernamen als den Anmeldenamen verfügt, verwenden Sie *Keep_name* Datenbank während der Migration beibehalten werden sollen. Verwendung *Copy_login_name* auf den neuen eigenständigen Datenbankbenutzer mit dem Namen der Anmeldung, anstelle des Benutzers zu erstellen. Wenn der Benutzername eines Datenbankbenutzers dem Anmeldenamen entspricht, wird mit beiden Optionen der Benutzer der enthaltenen Datenbank erstellt, ohne den Namen zu ändern.  
  
 [ **@disablelogin =** ] **N'***disable_login***'**  | **N'***do_not_disable_login***'**  
 *Disable_login* deaktiviert die Anmeldung in der master-Datenbank. Um eine Verbindung herzustellen, wenn die Anmeldung deaktiviert ist, muss die Verbindung den Namen der eigenständigen Datenbank als Bereitstellen der **Anfangskatalog** als Teil der Verbindungszeichenfolge angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **' sp_migrate_user_to_contained '** erstellt von Benutzer der enthaltenen Datenbank mit Kennwort, unabhängig von den Eigenschaften oder Berechtigungen der Anmeldung. Die Prozedur kann z. B. erfolgreich, wenn die Anmeldung deaktiviert ist, oder wenn der Benutzer verweigert wird die **CONNECT** Berechtigung für die Datenbank.  
  
 **' sp_migrate_user_to_contained '** gelten folgende Einschränkungen.  
  
-   Der Benutzername darf nicht bereits in der Datenbank vorhanden sein.  
  
-   Integrierte Benutzer wie dbo und guest, können nicht konvertiert werden.  
  
-   Der Benutzer kann nicht angegeben werden, der **EXECUTE AS** -Klausel einer signierten gespeicherten Prozedur.  
  
-   Kann nicht im Besitz des Benutzers einer gespeicherten Prozedur, die enthält die **EXECUTE AS OWNER** Klausel.  
  
-   **' sp_migrate_user_to_contained '** kann nicht in einer Systemdatenbank verwendet werden.  
  
## <a name="security"></a>Sicherheit  
 Achten Sie beim Migrieren von Benutzern darauf, dass nicht alle Administratoranmeldungen von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gelöscht werden. Wenn alle Anmeldungen gelöscht werden, finden Sie unter [Herstellen einer Verbindung mit SQL Server, wenn Administratoren sind gesperrt](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Wenn die **"BUILTIN\Administrators"** -Anmeldung vorhanden ist, die Administratoren können eine Verbindung herstellen, indem starten die Anwendung mit der **als Administrator ausführen** Option.  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL SERVER** -Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-migrating-a-single-user"></a>A. Migrieren eines einzelnen Benutzers  
 Im folgenden Beispiel wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `Barry` in den Benutzer einer enthaltenen Datenbankbenutzer mit Kennwort migriert. Im Beispiel ändert sich nicht auf den Benutzernamen ein, und behält den Anmeldenamen als aktiviert.  
  
```sql  
sp_migrate_user_to_contained   
@username = N'Barry',  
@rename = N'keep_name',  
@disablelogin = N'do_not_disable_login' ;  
  
```  
  
### <a name="b-migrating-all-database-users-with-logins-to-contained-database-users-without-logins"></a>B. Migrieren aller Datenbankbenutzer mit Anmeldenamen zu Benutzern in eigenständigen Datenbanken ohne Anmeldenamen  
 Im folgenden Beispiel werden alle Benutzer, die auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen basieren, in Benutzer enthaltener Datenbanken mit Kennwörtern migriert. Nicht berücksichtigt werden Anmeldungen, die nicht aktiviert sind. Das Beispiel muss in der enthaltenen Datenbank ausgeführt werden.  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Migrate to a Partially Contained Database](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)   
 [Eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md)  
  
  
