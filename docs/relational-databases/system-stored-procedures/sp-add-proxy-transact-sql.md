---
title: Sp_add_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 247c834abfbc47485628702bf4cd87c7662c44a8
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494272"
---
# <a name="spaddproxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt den angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Proxy hinzu.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_name = ] 'proxy_name'` Der Name des zu erstellenden Proxys. Die *Proxy_name* ist **Sysname**, hat den Standardwert NULL. Wenn die *Proxy_name* ist NULL oder eine leere Zeichenfolge, die den Namen des der Proxy wird standardmäßig die *User_name* angegeben.  
  
`[ @enabled = ] is_enabled` Gibt an, ob der Proxy aktiviert ist. Die *Is_enabled* Flag **Tinyint**, hat den Standardwert 1. Wenn *Is_enabled* ist **0**, der Proxy nicht aktiviert und kann nicht von einem Auftragsschritt verwendet werden.  
  
`[ @description = ] 'description'` Eine Beschreibung des Proxys. Die Beschreibung ist **nvarchar(512)**, hat den Standardwert NULL. Mit der Beschreibung können Sie den Proxy dokumentieren. Sie erfüllt keine weiteren Aufgaben für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent. Daher ist dieses Argument optional.  
  
`[ @credential_name = ] 'credential_name'` Der Name der Anmeldeinformationen für den Proxy. Die *Credential_name* ist **Sysname**, hat den Standardwert NULL. Entweder *Credential_name* oder *Credential_id* muss angegeben werden.  
  
`[ @credential_id = ] credential_id` Die ID der Anmeldeinformationen für den Proxy. Die *Credential_id* ist **Int**, hat den Standardwert NULL. Entweder *Credential_name* oder *Credential_id* muss angegeben werden.  
  
`[ @proxy_id = ] id OUTPUT` Die Proxy-ID an den Proxy zugewiesen werden, wenn erfolgreich erstellt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Diese gespeicherte Prozedur muss ausgeführt werden, der **Msdb** Datenbank.  
  
 Von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Proxy wird die Sicherheit für Auftragsschritte verwaltet, die andere Subsysteme als das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Subsystem verwenden. Jeder Proxy entspricht einem Satz Sicherheitsanmeldeinformationen. Ein Proxy kann über Zugriff auf eine beliebige Anzahl von Subsystemen verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** festen Sicherheitsrolle diese Prozedur ausführen kann.  
  
 Mitglieder der **Sysadmin** festen Sicherheitsrolle, die jeden beliebigen Proxy verwenden-Auftragsschritte erstellen. Verwenden Sie die gespeicherte Prozedur [Sp_grant_login_to_proxy &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) anderen Anmeldenamen den Zugriff auf dem Proxy zu gewähren.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird ein Proxy für die Anmeldeinformationen `CatalogApplicationCredential` erstellt. Es wird im Code vorausgesetzt, dass die Anmeldeinformationen bereits vorhanden sind. Weitere Informationen zu Anmeldeinformationen finden Sie unter [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
