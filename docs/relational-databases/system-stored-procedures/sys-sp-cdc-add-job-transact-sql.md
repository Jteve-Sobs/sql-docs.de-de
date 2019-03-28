---
title: sys.sp_cdc_add_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_add_job_TSQL
- sys.sp_cdc_add_job
- sys.sp_cdc_add_job_TSQL
- sp_cdc_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_add_job
ms.assetid: c4458738-ed25-40a6-8294-a26ca5a05bd9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 533f37252fa16e2e139f29ac843d6d4a933f13de
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532142"
---
# <a name="sysspcdcaddjob-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Cleanup- oder Aufzeichnungsauftrag für Change Data Capture in der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_add_job [ @job_type = ] 'job_type'  
    [ , [ @start_job = ] start_job ]   
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ , [ @threshold ] = 'delete_threshold' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_type = ] 'job\_type'` Der Typ des hinzuzufügenden Auftrags. *Der Standardwert ist* ist **nvarchar(20)** und darf nicht NULL sein. Gültige Eingaben sind **'capture'** und **'Cleanup'**.  
  
`[ @start_job = ] start_job` Flag zum angeben, ob der Auftrag gestartet werden soll, unmittelbar nachdem er hinzugefügt wurde. *Start_job* ist **Bit** hat den Standardwert 1.  
  
`[ @maxtrans ] = max_trans` Maximale Anzahl der in jedem Scanzyklus zu verarbeitenden Transaktionen. *Max_trans* ist **Int** hat den Standardwert von 500. Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 *Max_trans* ist nur für aufzeichnungsaufträge gültig.  
  
`[ @maxscans ] = max\_scans_` Maximale Anzahl der scanzyklen, ausführen, um alle Zeilen aus dem Protokoll zu extrahieren. *Max_scans* ist **Int** hat den Standardwert 10.  
  
 *Max_scan* ist nur für aufzeichnungsaufträge gültig.  
  
`[ @continuous ] = continuous_` Gibt an, ob der aufzeichnungsauftrag fortlaufend (1), oder nur einmalig (0). *fortlaufende* ist **Bit** hat den Standardwert 1.  
  
 Wenn *fortlaufende* = 1, die [Sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) Auftrag überprüft das Protokoll und verarbeitet bis zu (*Max_trans* \* *Max_scans*) Transaktionen. Er wartet dann die Anzahl der Sekunden, die im angegebenen *Polling_interval* vor Beginn des nächsten protokollscans.  
  
 Wenn *fortlaufende* = 0, die **Sp_cdc_scan** auftragsausführung bis zu *Max_scans* Scanvorgänge des Protokolls, verarbeitet dabei bis zu *Max_trans* Transaktion während jedes Scanvorgangs und wird dann beendet wird.  
  
 *fortlaufende* ist nur für aufzeichnungsaufträge gültig.  
  
`[ @pollinginterval ] = polling\_interval_` Anzahl von Sekunden zwischen den Scan des Replikationsprotokolls Prozessorzyklen. *Polling_interval* ist **Bigint** hat den Standardwert 5.  
  
 *Polling_interval* ist nur für aufzeichnungsaufträge gültig Aufträgen, wenn *fortlaufende* auf 1 festgelegt ist. Wenn angegeben, kann der Wert nicht negativ sein und 24 Stunden nicht übersteigen. Wenn der Wert 0 angegeben ist, wird zwischen den Protokollscans nicht gewartet.  
  
`[ @retention ] = retention_` Anzahl der Minuten, für die Zeilen werden in beibehalten werden sollen-Änderungstabellen. *Aufbewahrung* ist **Bigint** hat den Standardwert ist 4320 (72 Stunden). Der Maximalwert beträgt 52494800 (100 Jahre). Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 *Aufbewahrung* ist nur für cleanupaufträge gültig.  
  
`[ @threshold = ] 'delete\_threshold'` Maximale Anzahl von Einträgen für Löschvorgänge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können. *Delete_threshold* ist **Bigint** hat den Standardwert von 5000.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Es wird ein Cleanupauftrag mit den Standardwerten erstellt, wenn die erste Tabelle in der Datenbank für Change Data Capture aktiviert ist. Es wird ein Aufzeichnungsauftrag mit den Standardwerten erstellt, wenn die erste Tabelle in der Datenbank für Change Data Capture aktiviert ist und keine Transaktionsveröffentlichungen für diese Datenbank vorhanden sind. Wenn eine Transaktionsveröffentlichung vorhanden ist, wird der Transaktionsprotokollleser verwendet, um den Aufzeichnungsmechanismus zu ermöglichen. Ein separater Aufzeichnungsauftrag ist dann weder erforderlich noch zulässig.  
  
 Da die Cleanup- und Aufzeichnungsaufträge standardmäßig erstellt werden, ist diese gespeicherte Prozedur nur dann erforderlich, wenn ein Auftrag explizit gelöscht wurde und erneut erstellt werden muss.  
  
 Der Name des Auftrags ist **cdc.**  _\<Datenbank\_Namen\>_**\_Bereinigung** oder **cdc.**  _\<Datenbank\_Namen\>_**\_erfassen**, wobei *< Database_name >* ist der Name der aktuellen Datenbank. Wenn ein Auftrag mit dem gleichen Namen bereits vorhanden ist, wird der Name mit einem Punkt angefügt (**.**) gefolgt durch einen eindeutigen Bezeichner, z. B.: **cdc. AdventureWorks_capture. A1ACBDED-13FC-428C-8302-10100EF74F52**.  
  
 Verwenden Sie zum Anzeigen der aktuellen Konfigurations eines Cleanup- oder aufzeichnungsauftrag Auftrags [Sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md). Verwenden Sie zum Ändern der Konfigurations eines Auftrags [Sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Db_owner** festen Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-capture-job"></a>A. Erstellen eines Aufzeichnungsauftrags  
 Im folgenden Beispiel wird ein Aufzeichnungsauftrag erstellt. In diesem Beispiel wird davon ausgegangen, dass der vorhandene Cleanupauftrag explizit gelöscht wurde und erneut erstellt werden muss. Der Auftrag wird mit den Standardwerten erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job @job_type = N'capture';  
GO  
```  
  
### <a name="b-creating-a-cleanup-job"></a>B. Erstellen eines Cleanupauftrags  
 Im folgenden Beispiel wird ein Cleanupauftrag in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank erstellt. Der `@start_job`-Parameter wird auf 0 festgelegt, und `@retention` wird auf 5760 Minuten (96 Stunden) festgelegt. In diesem Beispiel wird davon ausgegangen, dass der vorhandene Cleanupauftrag explizit gelöscht wurde und erneut erstellt werden muss.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job  
     @job_type = N'cleanup'  
    ,@start_job = 0  
    ,@retention = 5760;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [Über Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
