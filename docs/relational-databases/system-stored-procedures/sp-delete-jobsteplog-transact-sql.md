---
title: Sp_delete_jobsteplog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c1587b65df123400188ba062ef40e57f9a0a550
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085314"
---
# <a name="spdeletejobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftragsschrittprotokolle, die mit den Argumenten angegeben sind. Verwenden Sie diese gespeicherte Prozedur zum Verwalten der **Sysjobstepslogs** -Tabelle in der **Msdb** Datenbank.  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] 'job_id'` Die Auftrags-ID für den Auftrag, der die zu entfernende auftragsschrittprotokoll enthält. *Job_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> **HINWEIS:** Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
`[ @step_id = ] step_id` Die ID des Schritts im Auftrag, für den das auftragsschrittprotokoll gelöscht werden. Wenn keine Angabe erfolgt, werden alle Auftragsschrittprotokolle im Auftrag gelöscht, es sei denn, **@older_than** oder **@larger_than** angegeben sind. *Step_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'` Der Name des Schritts im Auftrag, für den das auftragsschrittprotokoll gelöscht werden. *Step_name* ist **Sysname**, hat den Standardwert NULL.  
  
> **HINWEIS:** Entweder *Step_id* oder *Step_name* kann angegeben werden, aber beide Angaben sind nicht möglich.  
  
`[ @older_than = ] 'date'` Das Datum und Uhrzeit des ältesten auftragsschrittprotokolls, die Sie beibehalten möchten. Alle Auftragsschrittprotokolle vor diesem Datum und dieser Uhrzeit werden entfernt. *Datum* ist **"DateTime"** , hat den Standardwert NULL. Beide **@older_than** und **@larger_than** kann angegeben werden.  
  
`[ @larger_than = ] 'size_in_bytes'` Die Größe in Bytes, der das auftragsschrittprotokoll, die Sie beibehalten möchten. Alle Auftragsschrittprotokolle, die diese Größe überschreiten, werden entfernt. Beide **@larger_than** und **@older_than** kann angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_delete_jobsteplog** befindet sich in der **Msdb** Datenbank.  
  
 Wenn keine Argumente außer **@job_id** oder **@job_name** angegeben sind, werden alle Auftragsschrittprotokolle für den angegebenen Auftrag gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **Sysadmin** können löschen ein auftragsschrittprotokolls, das von einem anderen Benutzer gehört.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. Entfernen aller Auftragsschrittprotokolle aus einem Auftrag  
 Im folgenden Beispiel werden alle Auftragsschrittprotokolle für den `Weekly Sales Data Backup`-Auftrag entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>B. Entfernen des Auftragsschrittprotokolls für einen bestimmten Auftragsschritt  
 Im folgenden Beispiel wird das Auftragsschrittprotokoll für Schritt 2 im `Weekly Sales Data Backup`-Auftrag entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>C. Entfernen aller Auftragsschrittprotokolle auf Grundlage von Alter und Größe  
 Im folgenden Beispiel werden alle Auftragsschrittprotokolle aus dem `Weekly Sales Data Backup`-Auftrag entfernt, die älter sind als 12 Uhr mittags, 25. Oktober 2005, und die größer sind als 100 MB (Megabyte).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
