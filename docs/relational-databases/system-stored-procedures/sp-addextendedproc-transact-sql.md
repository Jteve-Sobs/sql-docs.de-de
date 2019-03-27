---
title: sp_addextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b895692bf9ce65d9e063fb1d484cf84734897c86
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494282"
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registriert den Namen einer neuen erweiterten gespeicherten Prozedur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die [CLR-Integration](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @functname = ] 'procedure'` Ist der Name der Funktion, die die Dynamic Link Library (DLL) aufgerufen. *Prozedur* ist **nvarchar(517)**, hat keinen Standardwert. *Prozedur* optional den Namen des Besitzers in der Form enthalten können *owner.function*.  
  
`[ @dllname = ] 'dll'` Ist der Name der DLL, die die Funktion enthält. *DLL* ist **varchar(255)**, hat keinen Standardwert. Es ist empfehlenswert, den vollständigen Pfad der DLL anzugeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Nachdem eine erweiterte gespeicherte Prozedur erstellt wurde, es muss hinzugefügt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit **Sp_addextendedproc**. Weitere Informationen finden Sie unter [Hinzufügen einer erweiterten gespeicherten Prozedur zu SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Diese Prozedur kann nur in ausgeführt werden die **master** Datenbank. Um eine erweiterte gespeicherte Prozedur aus einer Datenbank außer auszuführen **master**, qualifizieren Sie den Namen der erweiterten gespeicherten Prozedur mit **master**.  
  
 **Sp_addextendedproc** fügt Einträge, die die [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalogsicht, registrieren den Namen der neuen erweiterten gespeicherten Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es fügt auch einen Eintrag in der [extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) -Katalogsicht angezeigt.  
  
> [!IMPORTANT]  
>  Vorhandene DLLs, die nicht mit einem vollständigen Pfad registriert wurden, sind nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht mehr funktionsfähig. Verwenden Sie zum Beheben des Problems **Sp_dropextendedproc** zum Aufheben der Registrierung der DLL, und klicken Sie dann registrieren Sie ihn mit **Sp_addextendedproc**, den vollständigen Pfad angeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_addextendedproc**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Xp_hello** der erweiterten gespeicherten Prozedur.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
