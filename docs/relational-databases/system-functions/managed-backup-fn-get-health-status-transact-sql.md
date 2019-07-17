---
title: managed_backup.fn_get_health_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_health_status_TSQL
- smart_admin.fn_get_health_status_TSQL
- smart_admin.fn_get_health_status
- fn_get_health_status
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_health_status
- fn_get_health_status
ms.assetid: b376711d-444a-4b5e-b483-8df323b4e31f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b921846b0fc27e59ff0874cdbf0827095bfc7db4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140658"
---
# <a name="managedbackupfngethealthstatus-transact-sql"></a>managed_backup.fn_get_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen der aggregierten Anzahl der Fehler zurück, die durch erweiterte Ereignisse während eines bestimmten Zeitraums gemeldet wurden.  
  
 Die Funktion wird verwendet, um Integritätsstatus von Diensten unter Smart Admin zu melden.  Derzeit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] des wirkungsfelds Smart Admin unterstützt wird. Daher beziehen sich die zurückgegebenen Fehler auf [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
managed_backup.fn_get_health_status([@begin_time = ] 'time_1' , [ @end_time = ] 'time_2')  
```  
  
##  <a name="Arguments"></a> Argumente  
 [@begin_time]  
 Der Beginn des Zeitraums, von dem an die aggregierte Anzahl von Fehlern berechnet wird.  Die @begin_time Parameter ist "DateTime". Der Standardwert ist NULL. Wenn der Wert NULL ist, verarbeitet die Funktion die Ereignisse, die bereits 30 Minuten vor der aktuellen Zeit gemeldet wurden.  
  
 [ @end_time]  
 Das Ende des Zeitraums, von dem an die aggregierte Anzahl von Fehlern berechnet wird. Die @end_time Parameter ist "DateTime" hat den Standardwert NULL. Wenn der Wert NULL ist, verarbeitet die Funktion erweiterte Ereignisse bis zur aktuellen Zeit.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|number_of_storage_connectivity_errors|ssNoversion|Die Anzahl von Verbindungsfehlern, die auftreten, wenn das Programm eine Verbindung mit dem Windows Azure-Speicherkonto herstellt.|  
|number_of_sql_errors|ssNoversion|Die Anzahl der Fehler, die zurückgegeben werden, wenn das Programm eine Verbindung mit der SQL Server Engine herstellt.|  
|number_of_invalid_credential_errors|ssNoversion|Die Anzahl der Fehler, die zurückgegeben werden, wenn das Programm versucht, sich mit den SQL-Anmeldeinformationen zu authentifizieren.|  
|number_of_other_errors|ssNoversion|Die Anzahl der Fehler aus anderen Kategorien außer Konnektivität, SQL oder Anmeldeinformationen.|  
|number_of_corrupted_or_deleted_backups|ssNoversion|Die Anzahl der gelöschten oder beschädigte Sicherungsdateien.|  
|number_of_backup_loops|ssNoversion|Die Anzahl der Scans, die der Sicherungs-Agent für alle mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurierten Datenbanken ausführt sind.|  
|number_of_retention_loops|ssNoversion|Die Anzahl der Datenbankscans, die zur Ermittlung der festgelegten Beibehaltungsdauer ausgeführt werden.|  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Anhand dieser aggregierten Anzahl kann die Systemintegrität überwacht werden. Wenn die Spalte number_ of_retention_loops nach 30 Minuten beispielsweise 0 ist, dauert die Überwachung der Beibehaltungsdauer entweder sehr lange oder funktioniert nicht ordnungsgemäß. Spalten mit Werten ungleich 0 können auf Probleme hindeuten. Sie sollten die Protokolle der erweiterten Ereignisse prüfen, um das Problem einzugrenzen. Alternativ können Sie mithilfe der gespeicherten Prozedur **managed_backup.sp_get_backup_diagnostics** zum Abrufen einer Liste der erweiterten Ereignisse, um die Details des Fehlers zu finden.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **wählen** Berechtigungen für die Funktion.  
  
## <a name="examples"></a>Beispiele  
  
-   Das folgende Beispiel gibt die aggregierte Fehleranzahl für die letzten 30 Minuten seit der Ausführung zurück.  
  
    ```  
    SELECT *  
    FROM managed_backup.fn_get_health_status(NULL, NULL)  
  
    ```  
  
-   Im folgenden Beispiel wird die aggregierte Fehleranzahl für die aktuelle Woche zurückgegeben:  
  
    ```  
    Use msdb  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
    SELECT *  
    FROM managed_backup.fn_get_health_status(@startofweek, @endofweek)  
  
    ```  
  
  
