---
title: Sp_msx_set_account (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22372412f9c3f905b8978741b556724ca880568c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108021"
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt den Namen und das Kennwort für das Masterserverkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents auf dem Zielserver fest.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @credential_name = ] 'credential_name'` Der Name der Anmeldeinformationen für die Anmeldung am Masterserver. Der bereitgestellte Name muss der Name vorhandener Anmeldeinformationen sein. Entweder *Credential_name* oder *Credential_id* muss angegeben werden.  
  
`[ @credential_id = ] credential_id` Der Bezeichner für die Anmeldeinformationen für die Anmeldung am Masterserver verwendet. Der Bezeichner muss ein Bezeichner für vorhandene Anmeldeinformationen sein. Entweder *Credential_name* oder *Credential_id* muss angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Anmeldeinformationen zum Speichern des Benutzernamens und der Kennwortinformationen, die ein Zielserver für die Anmeldung an einem Masterserver verwendet. Diese Prozedur legt die Anmeldeinformationen fest, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent für diesen Zielserver verwendet, um sich am Masterserver anzumelden.  
  
 Bei den angegebenen Anmeldeinformationen muss es sich um vorhandene Anmeldeinformationen handeln. Weitere Informationen zum Erstellen von Anmeldeinformationen finden Sie unter [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für **Sp_msx_set_account** standardmäßig Mitglieder der der **Sysadmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird festgelegt, dass dieser Server die Anmeldeinformationen `MsxAccount` für die Anmeldung am Masterserver verwenden soll.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [Sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
