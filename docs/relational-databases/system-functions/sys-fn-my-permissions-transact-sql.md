---
title: Sys. fn_my_permissions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_my_permissions_TSQL
- fn_my_permissions_TSQL
- sys.fn_my_permissions
- fn_my_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- fn_my_permissions function
- sys.fn_my_permissions function
ms.assetid: 30f97f00-03d8-443a-9de9-9ec420b7699b
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a64db42ba04e864752559bb2d2b895625f2c9f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122632"
---
# <a name="sysfnmypermissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste der Berechtigungen zurück, die dem Prinzipal eines sicherungsfähigen Elements effektiv gewährt wurden. Eine verwandte Funktion ist [HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>Argumente  
 *securable*  
 Der Name des sicherungsfähigen Elements. Wenn das sicherungsfähige Element der Server oder eine Datenbank ist, sollte dieser Wert auf NULL festgelegt werden. *securable* ist ein Skalarausdruck vom Typ **sysname**. *sicherungsfähige* kann ein mehrteiliger Name sein.  
  
 "*Securable_class*"  
 Der Name der Klasse des sicherungsfähigen Elements, für das Berechtigungen aufgelistet werden. *Securable_class* ist eine **Sysname**. *Securable_class* muss eine der folgenden sein: ANWENDUNGSROLLE, ASSEMBLY, ASYMMETRISCHEN SCHLÜSSEL, ZERTIFIKAT, VERTRAG, DATENBANK, ENDPUNKT, FULLTEXT CATALOG, LOGIN, NACHRICHTENTYP, OBJEKT, REMOTE SERVICE BINDING, ROLLE, ROUTE, SCHEMA, SERVER, SERVICE, SYMMETRISCHEN SCHLÜSSEL, TYP, BENUTZER, XML-SCHEMAAUFLISTUNG.  
  
## <a name="columns-returned"></a>Zurückgegebene Spalten  
 Die folgende Tabelle listet die Spalten, die **Fn_my_permissions** zurückgibt. Jede zurückgegebene Zeile beschreibt eine Berechtigung, über die der aktuelle Sicherheitskontext für das sicherungsfähige Element verfügt. Gibt NULL zurück, wenn die Abfrage einen Fehler erzeugt.  
  
|Spaltenname|Typ|Beschreibung|  
|-----------------|----------|-----------------|  
|Entitätsname|**sysname**|Der Name des sicherungsfähigen Elements, für das die aufgelisteten Berechtigungen effektiv gewährt wurden.|  
|subentity_name|**sysname**|Der Spaltenname, sofern das sicherungsfähige Element über Spalten verfügt; andernfalls NULL.|  
|permission_name|**nvarchar**|Der Name des Berechtigungssatzes.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Tabellenwertfunktion gibt eine Liste der gültigen Berechtigungen zurück, über die der aufrufende Prinzipal für ein bestimmtes sicherungsfähiges Element verfügt. Eine gültige Berechtigung ist eine der folgenden:  
  
-   Eine Berechtigung, die dem Prinzipal direkt gewährt und nicht verweigert wurde.  
  
-   Eine Berechtigung, die durch eine Berechtigung auf höherer Ebene des Prinzipals impliziert wird und nicht verweigert wird.  
  
-   Eine Berechtigung, die einer Rolle oder Gruppe erteilt wird, der der Prinzipal als Mitglied angehört, und nicht verweigert wird.  
  
-   Eine Berechtigung einer Rolle oder Gruppe, der der Prinzipal als Mitglied angehört, und die nicht verweigert wird.  
  
 Die Berechtigungsauswertung erfolgt immer im Sicherheitskontext des Aufrufers. Um zu ermitteln, ob ein anderer Prinzipal über eine gültige Berechtigung verfügt, muss der Aufrufer über die IMPERSONATE-Berechtigung für diesen Prinzipal verfügen.  
  
 Für Entitäten auf Schemaebene werden ein-, zwei- oder dreiteilige Namen akzeptiert, die ungleich NULL sind. Für Entitäten auf Datenbankebene ein einteiligen Namen akzeptiert, wobei eine Bedeutung für die null-Wert "*aktuelle Datenbank*". Für den Server selbst ist ein NULL-Wert (steht für "aktueller Server") erforderlich. **Fn_my_permissions** kann die Berechtigungen auf einem verknüpften Server überprüfen.  
  
 Die folgende Abfrage gibt eine Liste integrierter sicherungsfähiger Klassen zurück:  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 Wenn Standard, als der Wert des angegeben ist *sicherungsfähigen* oder *Securable_class*, wird der Wert als NULL interpretiert.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. Auflisten der gültigen Berechtigungen auf dem Server  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers auf dem Server zurück.  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>B. Auflisten der gültigen Berechtigungen für die Datenbank  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurück.  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>C. Auflisten der gültigen Berechtigungen für eine Sicht  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers für die `vIndividualCustomer`-Sicht im `Sales`-Schema der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurück.  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>D. Auflisten der gültigen Berechtigungen eines anderen Benutzers  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Datenbankbenutzers `Wanida` für die `Employee`-Tabelle im `HumanResources`-Schema der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurück. Der Aufrufer benötigt die IMPERSONATE-Berechtigung für den Benutzer `Wanida`.  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>E. Auflisten der gültigen Berechtigungen für ein Zertifikat  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers für ein Zertifikat namens `Shipping47` in der aktuellen Datenbank zurück.  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>F. Auflisten der gültigen Berechtigungen für eine XML-Schemaauflistung  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers für eine XML-Schemaauflistung, die mit dem Namen `ProductDescriptionSchemaCollection` in die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Datenbank.  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>G. Auflisten der gültigen Berechtigungen für einen Datenbankbenutzer  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des Aufrufers für einen Benutzer namens `MalikAr` in der aktuellen Datenbank zurück.  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>H. Auflisten der gültigen Berechtigungen eines anderen Anmeldenamens  
 Das folgende Beispiel gibt eine Liste der gültigen Berechtigungen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamens `WanidaBenshoof` für die `Employee`-Tabelle im `HumanResources`-Schema der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurück. Der Aufrufer benötigt die IMPERSONATE-Berechtigung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen `WanidaBenshoof`.  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Berechtigungshierarchie &#40;Datenbank-Engine &#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
