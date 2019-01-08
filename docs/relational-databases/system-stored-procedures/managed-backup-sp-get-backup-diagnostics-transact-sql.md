---
title: managed_backup.sp_get_backup_diagnostics (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_backup_diagnostics_TSQL
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics_TSQL
- smart_admin.sp_get_backup_diagnostics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics
ms.assetid: 2266a233-6354-464b-91ec-824ca4eb9ceb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 84fe7cea5418a022282958a7c16d263e5c7e9604
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399834"
---
# <a name="managedbackupspgetbackupdiagnostics-transact-sql"></a>managed_backup.sp_get_backup_diagnostics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt die erweiterten Ereignisse zurück, die von Smart Admin protokolliert wurden.  
  
 Verwenden Sie diese gespeicherte Prozedur zum Überwachen von Smart Admin protokollierten erweiterten Ereignisse. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Ereignisse werden in diesem System protokolliert und können überprüft werden, und mit dieser gespeicherten Prozedur überwacht.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
managed_backup.sp_get_backup_diagnostics [@xevent_channel = ] 'event type' [, [@begin_time = ] 'time1' ] [, [@end_time = ] 'time2'VARCHAR(255) = 'Xevent',@begin_time DATETIME = NULL,@end_time DATETIME = NULL  
```  
  
##  <a name="Arguments"></a> Argumente  
 @xevent_channel  
 Der Typ des erweiterten Ereignisses. Bei Verwendung des Standardwerts werden alle in den letzten 30 Minuten protokollierten Ereignisse zurückgegeben. Die protokollierten Ereignisse hängen vom aktivierten Typ der erweiterten Ereignisse ab. Sie können mithilfe dieses Parameters die gespeicherte Prozedur filtern, sodass nur Ereignisse eines bestimmten Typs angezeigt werden. Sie können den vollständigen Ereignisnamen oder eine Teilzeichenfolge angeben, wie z. B.: **'Admin'**, **'Analytic'**, **'Operational'**, und **"Debug"**. Die @event_channel ist **VARCHAR (255)**.  
  
 Um eine Liste der derzeit aktivierten Ereignistypen Ereignis erhalten die **managed_backup.fn_get_current_xevent_settings** Funktion.  
  
 [@begin_time  
 Der Beginn des Zeitraums, für den die Ereignisse angezeigt werden sollen. Die @begin_time Parameter ist "DateTime" hat den Standardwert NULL. Wenn dieser nicht angegeben ist, werden die Ereignisse der letzten 30 Minuten angezeigt.  
  
 @end_time  
 Das Ende des Zeitraums, für den die Ereignisse angezeigt werden sollen. Die @end_time -Parameter ist vom hat den Standardwert NULL.  Wenn dieser nicht angegeben ist, werden die Ereignisse bis zum aktuellen Zeitpunkt angezeigt.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 Die gespeicherte Prozedur gibt eine Tabelle mit den folgenden Informationen zurück:  
  
||||  
|-|-|-|  
|Spaltenname|Datentyp|Description|  
|event_type|NVARCHAR(512)|Typ des erweiterten Ereignisses.|  
|Ereignis|NVARCHAR(512)|Die Zusammenfassung der Ereignisprotokolle.|  
|Timestamp|timestamp|Der Zeitstempel des Ereignisses, der angibt, zu welchem Zeitpunkt das Ereignis ausgelöst wurde.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **EXECUTE** Berechtigungen für die gespeicherte Prozedur. Darüber hinaus müssen **VIEW SERVER STATE** Berechtigungen, da sie andere Systemobjekte, die ruft intern diese Berechtigung erfordern.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle für die letzten 30 Minuten protokollierten Ereignisse zurückgegeben.  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics  
  
```  
  
 Im folgenden Beispiel werden alle für einen bestimmten Zeitraum protokollierten Ereignisse zurückgegeben.  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Admin',  
  @begin_time = '2013-06-01', @end_time = '2013-06-10'  
  
```  
  
 Im folgenden Beispiel werden alle für die letzten 30 Minuten protokollierten Analyseereignisse zurückgegeben.  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Analytic'  
  
```  
  
  
