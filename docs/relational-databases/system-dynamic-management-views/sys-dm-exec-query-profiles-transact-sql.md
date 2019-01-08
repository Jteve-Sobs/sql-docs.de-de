---
title: dm_exec_query_profiles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fb79f056e533f4aabacdab5e3467bedce22b696
ms.sourcegitcommit: e0178cb14954c45575a0bab73dcc7547014d03b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860093"
---
# <a name="sysdmexecqueryprofiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Überwacht den Abfragestatus einer ausgeführten Abfrage in Echtzeit. Verwenden Sie beispielsweise diese DMV, um zu ermitteln, welcher Teil der Abfrage langsam ausgeführt wird. Verknüpfen Sie diese DMV mit anderen System-DMVs, indem Sie die im Beschreibungsfeld angegebenen Spalten verwenden. Sie können diese DMV aber auch mit anderen Leistungsindikatoren (z. B. Systemmonitor, xperf) verknüpfen, indem Sie die timestamp-Spalten verwenden.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 Die zurückgegebenen Leistungsindikatoren gelten pro Operator und pro Thread. Die Ergebnisse sind dynamisch und stimmen nicht mit den Ergebnissen für vorhandene Optionen wie SET STATISTICS XML ON überein, für die nur eine Ausgabe erfolgt, wenn die Abfrage abgeschlossen ist.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Identifiziert die Sitzung, in der die Abfrage ausgeführt wird. Verweist auf dm_exec_sessions.session_id.|  
|request_id|**int**|Identifiziert die Zielanforderung. Verweist auf dm_exec_sessions.request_id.|  
|sql_handle|**varbinary(64)**|Identifiziert die Zielabfrage. Verweist auf dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary(64)**|Identifiziert die Zielabfrage (verweist auf dm_exec_query_stats.plan_handle).|  
|physical_operator_name|**nvarchar(256)**|Der Name des physischen Operators.|  
|node_id|**int**|Identifiziert einen Operatorknoten in der Abfragestruktur.|  
|thread_id|**int**|Unterscheidet die Threads (für eine parallele Abfrage), die zu demselben Abfrageoperatorknoten gehören.|  
|task_address|**varbinary(8)**|Identifiziert den SQLOS-Task, den dieser Thread verwendet. Verweist auf dm_os_tasks.task_address.|  
|row_count|**bigint**|Anzahl der bisher vom Operator zurückgegebenen Zeilen.|  
|rewind_count|**bigint**|Anzahl der bisherigen Zurückspulvorgänge.|  
|rebind_count|**bigint**|Anzahl der bisherigen erneuten Bindungen.|  
|end_of_scan_count|**bigint**|Anzahl der bisherigen Scanenden.|  
|estimate_row_count|**bigint**|Geschätzte Anzahl von Zeilen. Es kann nützlich sein, "estimated_row_count" mit dem tatsächlichen "row_count" zu vergleichen.|  
|first_active_time|**bigint**|Die Zeit in Millisekunden, zu der der Operator zuerst aufgerufen wurde.|  
|last_active_time|**bigint**|Die Zeit in Millisekunden, zu der der Operator zuletzt aufgerufen wurde.|  
|open_time|**bigint**|Zeitstempel beim Öffnen (in Millisekunden).|  
|first_row_time|**bigint**|Zeitstempel beim Öffnen der ersten Zeile (in Millisekunden).|  
|last_row_time|**bigint**|Zeitstempel beim Öffnen der letzten Zeile (in Millisekunden).|  
|close_time|**bigint**|Zeitstempel beim Schließen (in Millisekunden).|  
|elapsed_time_ms|**bigint**|Gesamte verstrichene Zeit (in Millisekunden) ein, die Vorgänge des Zielknotens bisher.|  
|cpu_time_ms|**bigint**|Gesamtanzahl der Verwendung von CPU-Zeit (in Millisekunden) bisher durch die Vorgänge des Zielknotens.|  
|database_id|**smallint**|ID der Datenbank, die das Objekt enthält, für das die Lese- und Schreibvorgänge ausgeführt werden.|  
|object_id|**int**|Der Bezeichner für das Objekt, für das die Lese- und Schreibvorgänge ausgeführt werden. Verweist auf "sys.objects.object_id".|  
|index_id|**int**|Der Index (sofern vorhanden), für den das Rowset geöffnet wird.|  
|scan_count|**bigint**|Anzahl der bisherigen Tabellen-/Indexscans.|  
|logical_read_count|**bigint**|Anzahl der bisherigen logischen Lesevorgänge.|  
|physical_read_count|**bigint**|Anzahl der bisherigen physischen Lesevorgänge.|  
|read_ahead_count|**bigint**|Anzahl der bisherigen Read-Ahead-Lesevorgänge.|  
|write_page_count|**bigint**|Anzahl der bisherigen page-writes-Schreibvorgänge aufgrund eines Überlaufs.|  
|lob_logical_read_count|**bigint**|Anzahl der bisherigen logischen LOB-Lesevorgänge.|  
|lob_physical_read_count|**bigint**|Anzahl der bisherigen physischen LOB-Lesevorgänge.|  
|lob_read_ahead_count|**bigint**|Anzahl der bisherigen Read-Ahead-LOB-Lesevorgänge.|  
|segment_read_count|**int**|Anzahl der bisherigen Segment-Read-Ahead-Lesevorgänge.|  
|segment_skip_count|**int**|Anzahl der bisher übersprungenen Segmente.| 
|actual_read_row_count|**bigint**|Anzahl der Zeilen, die durch den Operator zu lesen, bevor die residuale-Prädikat angewendet wurde.| 
|estimated_read_row_count|**bigint**|**Gilt für:** Beginnend mit [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1. <br/>Geschätzte Anzahl von Zeilen durch den Operator gelesen werden, bevor die residuale-Prädikat angewendet wurde.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Wenn der Abfrageplanknoten keine E/A-Vorgänge aufweist, werden alle E/A-Leistungsindikatoren auf NULL festgelegt.  
  
 Die von dieser DMV gemeldeten E/A-Leistungsindikatoren sind in zweierlei Hinsicht präziser als die von SET STATISTICS IO gemeldeten Leistungsindikatoren:  
  
-   SET STATISTICS IO fasst die Leistungsindikatoren für alle E/A-Vorgänge für eine bestimmte Tabelle als Gruppe zusammen. Mit dieser DMV erhalten Sie separate Leistungsindikatoren für jeden Knoten im Abfrageplan, der E/A-Vorgänge für die Tabelle ausführt.  
  
-   Bei einem parallelen Scan meldet diese DMV Leistungsindikatoren für jeden der parallelen Threads für den Scan.
 
Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 den standard abfrageausführungsstatistik profilerstellungsinfrastruktur Seite-an-Seite mit einer einfachen abfrageausführungsstatistik profilerstellungsinfrastruktur vorhanden. Die neue Abfrage Ausführung profilerstellung statistikinfrastruktur verringert erheblich Performance-Overhead pro Operator Statistiken zur abfrageausführung, z. B. die tatsächliche Anzahl der Zeilen erfassen. Diese Funktion kann aktiviert werden, entweder über globale Start [Ablaufverfolgungsflags 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md), oder Sie wird automatisch aktiviert, wenn Query_thread_profile erweiterten Ereignis verwendet wird.

>[!NOTE]
> CPU und der verstrichenen Zeit werden unter die einfache Ausführung profilerstellung statistikinfrastruktur Reduzieren der Auswirkungen auf die Leistung nicht unterstützt.

Legen Sie die STATISTICS XML ON und SET STATISTICS PROFILE ON immer die ältere abfrageausführungsstatistik profilerstellungsinfrastruktur verwenden.

Zum Aktivieren der Ausgabe in dm_exec_query_profiles folgendermaßen vor:

In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 und höher verwenden Sie SET STATISTICS PROFILE ON oder SET STATISTICS XML ON zusammen mit der Abfrage wird untersucht. Dies kann die profilerstellung Infrastruktur und führt zu Ergebnissen im DMV für die Sitzung, in der SET-Befehl ausgeführt wurde. Wenn Sie eine Abfrage aus einer Anwendung untersuchen und SET-Optionen mit ihm können nicht aktiviert werden, können Sie erweiterte Ereignisse mit dem das Query_post_execution_showplan-Ereignis, das in der profilerstellungs-Infrastruktur aktivieren wird erstellen. 

In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 können Sie entweder aktivieren [Ablaufverfolgungsflags 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) oder verwenden Sie das erweiterte Query_thread_profile-Ereignis.

>[!NOTE]
> Die Abfrage geprüft hat, starten Sie nach der Aktivierung der profilerstellungs-Infrastruktur. Wenn die Abfrage bereits ausgeführt wird, wird eine Sitzung für erweiterte Ereignisse starren in nicht dm_exec_query_profiles Ergebnissen.


## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
   
## <a name="examples"></a>Beispiele  
 Schritt 1: Melden Sie sich bei einer Sitzung an, in der Sie die Abfrage ausführen möchten, die Sie mit "sys.dm_exec_query_profiles" analysieren werden. Verwenden zum Konfigurieren die Abfrage für die profilerstellung SET STATISTICS PROFILE auf. Führen Sie Ihre Abfrage in derselben Sitzung aus.  
  
```  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 Schritt 2: Melden Sie sich bei einer zweiten Sitzung an, die sich von der Sitzung unterscheidet, in der Ihre Abfrage ausgeführt wird.  
  
 Die folgende Anweisung fasst den Fortschritt der Abfrage zusammen, die derzeit in Sitzung 54 ausgeführt wird. Zu diesem Zweck wird die Gesamtzahl der Ausgabezeilen aller Threads für jeden Knoten berechnet und mit der geschätzten Anzahl an Ausgabezeilen für diesen Knoten verglichen.  
  
```  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

