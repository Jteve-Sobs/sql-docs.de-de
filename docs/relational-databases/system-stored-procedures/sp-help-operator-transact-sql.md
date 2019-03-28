---
title: Sp_help_operator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 48d70126d071879754011fed7342d03dd72185a5
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534382"
---
# <a name="sphelpoperator-transact-sql"></a>sp_help_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu den für den Server definierten Operatoren zurück.  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @operator_name = ] 'operator_name'` Der Name des Operators. *Operatorname* ist **Sysname**. Wenn *Operatorname* ist nicht angegeben ist, werden Informationen zu allen Operatoren zurückgegeben.  
  
`[ @operator_id = ] operator_id` Die ID des Operators für die Informationen angefordert werden. *Operator_id*ist **Int**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Operator_id* oder *Operatorname* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Operator-ID.|  
|**name**|**sysname**|Name des Operators.|  
|**enabled**|**tinyint**|Operator steht für den Empfang von Benachrichtigungen zur Verfügung:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**email_address**|**nvarchar(100)**|E-Mail-Adresse des Operators.|  
|**last_email_date**|**int**|Datum, an dem der Operator zuletzt per E-Mail benachrichtigt wurde.|  
|**last_email_time**|**int**|Uhrzeit, zu der der Operator zuletzt per E-Mail benachrichtigt wurde.|  
|**pager_address**|**nvarchar(100)**|Pageradresse des Operators.|  
|**last_pager_date**|**int**|Datum, an dem der Operator zuletzt per Pager benachrichtigt wurde.|  
|**last_pager_time**|**int**|Uhrzeit, zu der der Operator zuletzt per Pager benachrichtigt wurde.|  
|**weekday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Arbeitstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**weekday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Arbeitstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**saturday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Samstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**saturday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Samstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**sunday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Sonntagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**sunday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Sonntagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**pager_days**|**tinyint**|Eine Bitmaske (**1** = Sonntag, **64** = Samstag) Tage der Woche, der angibt, wenn der Operator Pagerbenachrichtigungen empfangen kann.|  
|**netsend_address**|**nvarchar(100)**|Operatoradresse für Benachrichtigungen per Netzwerk-Popupnachricht.|  
|**last_netsend_date**|**int**|Datum, an dem der Operator zuletzt per Netzwerk-Popupnachricht benachrichtigt wurde.|  
|**last_netsend_time**|**int**|Uhrzeit, zu der der Operator zuletzt per Netzwerk-Popupnachricht benachrichtigt wurde.|  
|**category_name**|**sysname**|Name der Operatorkategorie, zu der dieser Operator gehört.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_operator** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zum `François Ajenstat`-Operator ausgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_operator  
    @operator_name = N'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
