---
title: Sp_changesubstatus (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords:
- sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0040f986e5ff3b6de025761b32d2f40e2e127d39
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529615"
---
# <a name="spchangesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Status eines vorhandenen Abonnenten. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubstatus [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
        , [ @status = ] 'status'  
    [ , [ @previous_status = ] 'previous_status' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @distribution_jobid = ] distribution_jobid ]  
    [ , [ @from_auto_sync = ] from_auto_sync ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @offloadagent= ] remote_agent_activation ]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] dts_package_location ]  
    [ , [ @skipobjectactivation = ] skipobjectactivation  
  [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert **%**. Wenn *Veröffentlichung* nicht angegeben ist, werden alle Veröffentlichungen betroffen sind.  
  
`[ @article = ] 'article'` Ist der Name des Artikels. Er muss für die Veröffentlichung eindeutig sein. *Artikel* ist **Sysname**, hat den Standardwert **%**. Wenn *Artikel* nicht angegeben ist, wird allen Artikeln betroffen sind.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten, die den Status zu ändern. *Abonnenten* ist **Sysname**, hat den Standardwert **%**. Wenn *Abonnenten* nicht angegeben ist, ändert sich der Status für alle Abonnenten des angegebenen Artikels.  
  
`[ @status = ] 'status'` Wird der Abonnementstatus in der **Syssubscriptions** Tabelle. *Status* ist **Sysname**und hat keinen Standardwert und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**active**|Der Abonnent ist synchronisiert und empfängt Daten.|  
|**inactive**|Es ist ein Eintrag für einen Abonnenten ohne Abonnement vorhanden.|  
|**subscribed**|Der Abonnent fordert Daten an, ist aber noch nicht synchronisiert.|  
  
`[ @previous_status = ] 'previous_status'` Ist der vorherige Status für das Abonnement an. *Previous_status* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter können Sie Abonnements zu ändern, die aktuell diesen Status, und er ermöglicht damit Gruppenfunktionen für eine bestimmte Gruppe von Abonnements aufweisen (Beispiel: Wenn alle aktiven Abonnements zurück, in **abonniert**).  
  
`[ @destination_db = ] 'destination_db'` Ist der Name der Zieldatenbank. *Destination_db* ist **Sysname**, hat den Standardwert **%**.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit denen des Verteilungstasks. *Frequency_type* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Verteilungstasks. Dieser Parameter wird verwendet, wenn *Frequency_type* auf 32 (monatlich, relativ) festgelegt wird. *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Wie oft ist, in Minuten, für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit, die bei der der Verteilungstask erste ist wird geplant HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Verteilungstask nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Verteilungstask erste ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Verteilungstask nicht mehr, geplant ist JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'` Ist eine optionale Eingabeaufforderung. *Der Standardwert* ist **nvarchar(4000)**, hat den Standardwert NULL.  
  
`[ @distribution_jobid = ] distribution_jobid` Die Auftrags-ID des Verteilungs-Agents auf dem Verteiler für das Abonnement ist, wenn den Abonnementstatus von inaktiv auf aktiv geändert. In anderen Fällen wird sie nicht definiert. Wenn an einem einzelnen Aufruf dieser gespeicherten Prozedur mehrere Verteilungs-Agents beteiligt sind, ist Ergebnis nicht definiert. *Distribution_jobid* ist **'binary(16)'**, hat den Standardwert NULL.  
  
`[ @from_auto_sync = ] from_auto_sync` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] remote_agent_activation`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_activation* auf einen anderen Wert als **0** wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_server_name* auf einen beliebigen Wert ungleich NULL wird ein Fehler generiert.  
  
`[ @dts_package_name = ] 'dts_package_name'` Gibt den Namen des Pakets Data Transformation Services (DTS). *Dts_package_name* ist eine **Sysname**, hat den Standardwert NULL. Z. B. für ein Paket mit dem Namen **DTSPub_Package** möchten, geben `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'` Gibt das Kennwort für das Paket an. *Dts_package_password* ist **Sysname** hat den Standardwert NULL, der angibt, dass die Kennworteigenschaft ist, werden nicht geändert.  
  
> [!NOTE]  
>  Ein DTS-Paket muss über ein Kennwort verfügen.  
  
`[ @dts_package_location = ] dts_package_location` Gibt den Speicherort des Pakets an. *Dts_package_location* ist ein **Int**, hat den Standardwert **0**. Wenn **0**, den Speicherort des Pakets auf dem Verteiler ist. Wenn **1**, den Speicherort des Pakets wird auf dem Abonnenten. Der Speicherort des Pakets kann sein **Verteiler** oder **Abonnenten**.  
  
`[ @skipobjectactivation = ] skipobjectactivation` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @distribution_job_name = ] 'distribution_job_name'` Ist der Name des Verteilungsauftrags. *distribution_job _name* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, beim Ändern von Artikeleigenschaften auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changesubstatus** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_changesubstatus** ändert sich der Status des Abonnenten in die **Syssubscriptions** Tabelle mit den geänderten Status. Falls erforderlich, aktualisiert der Artikelstatus in der **Sysarticles** Tabelle, um die Aktivität bzw. Inaktivität anzuzeigen. Falls erforderlich, wird das Replikationsflag ein- oder ausschalten die **Sysobjects** Tabelle für die replizierte Tabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle **Db_owner** feste Datenbankrolle oder der Ersteller des Abonnements kann ausführen **Sp_changesubstatus**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
