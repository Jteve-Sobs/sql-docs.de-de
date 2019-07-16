---
title: Sp_help_jobhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10033b2525ba28e79bd31a73bd9e71a7cca15e42
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054928"
---
# <a name="sphelpjobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu den Aufträgen für Server in der Domäne zur Multiserveradministration bereit.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` ID des Auftrags. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @step_id = ] step_id` Die Schritt-ID. *Step_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @sql_message_id = ] sql_message_id` Die ID der Fehlermeldung, die von Microsoft SQL Server beim Ausführen des Auftrags zurückgegeben werden soll. *Sql_message_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @sql_severity = ] sql_severity` Der Schweregrad der Fehlermeldung, die von SQL Server beim Ausführen des Auftrags zurückgegeben werden soll. *Sql_severity* ist **Int**, hat den Standardwert NULL.  
  
`[ @start_run_date = ] start_run_date` Das Datum, an der Auftrag gestartet wurde. *Start_run_date*ist **Int**, hat den Standardwert NULL. *Start_run_date* muss, werden die im Formular eingegebenen YYYYMMDD, wobei YYYY ein vier Zeichen bestehende Jahreszahl ist, MM ein zwei Zeichen bestehenden Monatsnamen und DD ein zwei Zeichen bestehenden-Tagesname ist.  
  
`[ @end_run_date = ] end_run_date` Das Datum, an das der Auftrag abgeschlossen wurde. *End_run_date* ist **Int**, hat den Standardwert NULL. *End_run_date*muss, werden im Formular eingegebenen YYYYMMDD, wobei YYYY eine vierstellige Jahresangabe ist, MM ein zwei Zeichen bestehenden Monatsnamen und DD ein zwei Zeichen bestehenden-Tagesname ist.  
  
`[ @start_run_time = ] start_run_time` Die Zeit, die der Auftrag gestartet wurde. *Start_run_time* ist **Int**, hat den Standardwert NULL. *Start_run_time*muss, werden im Formular eingegebenen HHMMSS, wobei HH eine zwei Zeichen bestehenden Stunde des Tages ist, MM ein zwei Zeichen des Tages, und SS eine zwei Zeichen bestehenden Sekunde des Tages handelt es sich.  
  
`[ @end_run_time = ] end_run_time` Der Zeitpunkt, an der der Auftrag beendet wurde. *End_run_time* ist **Int**, hat den Standardwert NULL. *End_run_time*muss, werden im Formular eingegebenen HHMMSS, wobei HH eine zwei Zeichen bestehenden Stunde des Tages ist, MM ein zwei Zeichen des Tages, und SS eine zwei Zeichen bestehenden Sekunde des Tages handelt es sich.  
  
`[ @minimum_run_duration = ] minimum_run_duration` Die minimale Länge der Zeit für den Abschluss des Auftrags. *Minimum_run_duration* ist **Int**, hat den Standardwert NULL. *Minimum_run_duration*muss, werden im Formular eingegebenen HHMMSS, wobei HH eine zwei Zeichen bestehenden Stunde des Tages ist, MM ein zwei Zeichen des Tages, und SS eine zwei Zeichen bestehenden Sekunde des Tages handelt es sich.  
  
`[ @run_status = ] run_status` Der Ausführungsstatus des Auftrags. *Run_status* ist **Int**, hat den Standardwert NULL und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Fehler|  
|**1**|Erfolgreich|  
|**2**|Wiederholen (nur Schritte)|  
|**3**|Canceled|  
|**4**|In Bearbeitung befindlichen Nachrichten|  
|**5**|Unbekannt|  
  
`[ @minimum_retries = ] minimum_retries` Die Mindestanzahl an, wie oft, die Wiederholen eines Auftrags ausführen soll. *Minimum_retries* ist **Int**, hat den Standardwert NULL.  
  
`[ @oldest_first = ] oldest_first` Gibt an, ob die Ausgabe die ältesten Aufträge zuerst angezeigt. *Oldest_first* ist **Int**, hat den Standardwert **0**, der die neuesten Aufträge zuerst dargestellt. **1** die ältesten Aufträge zuerst präsentiert.  
  
`[ @server = ] 'server'` Der Name des Servers, auf dem der Auftrag ausgeführt wurde. *Server* ist **nvarchar(30)** , hat den Standardwert NULL.  
  
`[ @mode = ] 'mode'` Gibt, ob SQL Server alle Spalten im Resultset ausgibt (**vollständige**) oder eine Zusammenfassung der Spalten. *Modus* ist **vom Datentyp varchar(7)** , hat den Standardwert **Zusammenfassung**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Die tatsächliche Spaltenliste hängt vom Wert der *Modus*. Die umfassendste Sammlung von Spalten ist unten dargestellt und wird zurückgegeben, wenn *Modus* ist "FULL".  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Verlaufseintrags-ID|  
|**job_id**|**uniqueidentifier**|ID des Auftrags.|  
|**job_name**|**sysname**|Name des Auftrags.|  
|**step_id**|**int**|Schritt-ID (werden **0** für einen Auftragsverlauf).|  
|**step_name**|**sysname**|Schrittname (NULL für einen Auftragsverlauf).|  
|**sql_message_id**|**int**|Für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritte die letzte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Fehlernummer, die beim Ausführen des Befehls gemeldet wurde.|  
|**sql_severity**|**int**|Für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritte der höchste [!INCLUDE[tsql](../../includes/tsql-md.md)]-Fehlerschweregrad, der beim Ausführen des Befehls gemeldet wurde.|  
|**Nachricht**|**nvarchar(1024)**|Meldung zu Auftrags- oder Schrittverlauf.|  
|**run_status**|**int**|Ergebnis des Auftrags oder Schritts.|  
|**run_date**|**int**|Datum, an dem das Ausführen des Auftrags oder Schritts begann.|  
|**run_time**|**int**|Uhrzeit, zu der das Ausführen des Auftrags oder Schritts begann.|  
|**run_duration**|**int**|Vergangene Ausführungszeit des Auftrags oder Schritts im Format HHMMSS.|  
|**operator_emailed**|**nvarchar(20)**|Operator, der bezüglich dieses Auftrags per E-Mail benachrichtigt wurde (NULL für Schrittverlauf).|  
|**operator_netsent**|**nvarchar(20)**|Operator, dem bezüglich dieses Auftrags eine Netzwerknachricht gesendet wurde (NULL für Schrittverlauf).|  
|**operator_paged**|**nvarchar(20)**|Operator, der bezüglich dieses Auftrags per Pager benachrichtigt wurde (NULL für Schrittverlauf).|  
|**retries_attempted**|**int**|Die Wiederholungsversuche für den Schritt (für einen Auftragsverlauf immer 0).|  
|**server**|**nvarchar(30)**|Server, auf dem der Schritt oder Auftrag ausgeführt wird. Ist immer (**lokalen**).|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_jobhistory** gibt einen Bericht mit den Verlauf des angegebenen geplanten Aufträge zurück. Werden keine Parameter angegeben, enthält der Bericht den Verlauf aller geplanten Aufträge.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **SQLAgentUserRole** -Datenbankrolle kann nur den Verlauf für Aufträge, deren Besitzer, anzeigen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Auflisten aller Auftragsinformationen für einen Auftrag  
 Im folgenden Beispiel werden alle Auftragsinformationen für den `NightlyBackups`-Auftrag aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. Auflisten von Informationen für Aufträge, die bestimmte Bedingungen erfüllen  
 Im folgenden Beispiel werden alle Spalten und alle Auftragsinformationen für alle fehlgeschlagenen Aufträge und fehlgeschlagenen Auftragsschritte mit der Fehlermeldung `50100` (eine benutzerdefinierte Fehlermeldung) und einem Schweregrad von `20` aufgelistet.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
