---
title: Sp_help_targetservergroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_targetservergroup_TSQL
- sp_help_targetservergroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_targetservergroup
ms.assetid: ec3a4a68-b591-431c-9518-053ede522d0c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcb699741435bace786241ac01a57ad66dd5631d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017796"
---
# <a name="sphelptargetservergroup-transact-sql"></a>sp_help_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet alle Zielserver in der angegebenen Gruppe auf. Wenn keine Gruppe angegeben wird, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationen zu allen Zielservergruppen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_targetservergroup  
    [ [ @name = ] 'name' ]  
```  
  
## <a name="argument"></a>Argument  
`[ @name = ] 'name'` Ist der Name der Zielservergruppe für die Informationen zurückgegeben werden sollen. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|ID der Servergruppe.|  
|**name**|**sysname**|Name der Servergruppe.|  
  
## <a name="permissions"></a>Berechtigungen  
 Berechtigungen zum Ausführen dieses Verfahrens werden standardmäßig die **Sysadmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-information-for-all-target-server-groups"></a>A. Auflisten von Informationen für alle Zielservergruppen  
 In diesem Beispiel werden Informationen für alle Zielservergruppen aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server-group"></a>B. Auflisten von Informationen für eine bestimmte Zielservergruppe  
 In diesem Beispiel werden Informationen für die `Servers Maintaining Customer Information`-Zielservergruppe aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup   
    N'Servers Maintaining Customer Information' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
