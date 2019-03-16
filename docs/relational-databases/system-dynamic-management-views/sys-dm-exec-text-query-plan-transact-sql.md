---
title: Sys. dm_exec_text_query_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_text_query_plan
- sys.dm_exec_text_query_plan_TSQL
- dm_exec_text_query_plan_TSQL
- sys.dm_exec_text_query_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_text_query_plan dynamic management function
ms.assetid: 9d5e5f59-6973-4df9-9eb2-9372f354ca57
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4329b8fcbddb0050f529e401da8d6c7c14f065d9
ms.sourcegitcommit: d92ad400799d8b74d5c601170167b86221f68afb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58080272"
---
# <a name="sysdmexectextqueryplan-transact-sql"></a>sys.dm_exec_text_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den Showplan im Textformat für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder für eine bestimmte Anweisung innerhalb des Batches zurück. Der Abfrageplan wird angegeben, vom planhandle entweder zwischengespeichert oder wird derzeit ausgeführt werden können. Diese Tabellenwertfunktion ähnelt [Sys. dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md), jedoch weist die folgenden Unterschiede:  
  
-   Die Ausgabe des Abfrageplans wird im Textformat zurückgegeben.  
-   Die Größe der Ausgabe des Abfrageplans ist nicht beschränkt.  
-   Im Batch können einzelne Anweisungen angegeben werden.  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_exec_text_query_plan   
(   
    plan_handle   
    , { statement_start_offset | 0 | DEFAULT }  
        , { statement_end_offset | -1 | DEFAULT }  
)  
```  
  
## <a name="arguments"></a>Argumente  
*plan_handle*  
Ist ein Token, die eindeutig einen Abfrageplan für die Ausführung für einen Batch, die ausgeführt wurde und der Plan im Plancache befindet, oder wird gerade ausgeführt. *plan_handle* ist **varbinary(64)**   

*plan_handle* kann aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden: 
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
*Statement_start_offset* | 0 | STANDARDWERT  
Gibt die Startposition der Abfrage an (in Bytes), die von der Zeile im Text des zugehörigen Batches oder persistenten Objekts beschrieben wird. *Statement_start_offset* ist **Int**. Der Wert 0 gibt den Anfang des Batches an. Der Standardwert ist 0.  
  
Der Startoffset der Anweisung kann aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden:  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*Statement_end_offset* |-1 | STANDARDWERT  
Gibt (in Bytes) die Endposition der Abfrage an, die die Zeile innerhalb des Texts des Batches oder des persistenten Objekts beschreibt.  
  
*Statement_start_offset* ist **Int**.  
  
Der Wert -1 gibt das Ende des Batches an. Der Standardwert ist 1.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**objectid**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**number**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Eine Gruppe von Prozeduren für die **orders** -Anwendung kann z. B. die Namen **orderproc;1**, **orderproc;2**usw. haben. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**encrypted**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**nvarchar(max)**|Enthält eine zur Kompilierzeit erstellte Showplandarstellung des Abfrageausführungsplans, der mit *plan_handle*angegeben ist. Der Showplan liegt im Textformat vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
  
## <a name="remarks"></a>Hinweise  
 Unter den folgenden Bedingungen wird keine Showplanausgabe zurückgegeben, der **Plan** Spalte der zurückgegebenen Tabelle für **Sys. dm_exec_text_query_plan**:  
  
-   Falls der mit *plan_handle* angegebene Abfrageplan aus dem Plancache entfernt wurde, enthält die **query_plan** -Spalte der zurückgegebenen Tabelle den Wert NULL. Diese Bedingung kann z. B. auftreten, liegt eine zeitliche Verzögerung zwischen, wenn das planhandle erfasst wurde und seiner Verwendung mit wurde **Sys. dm_exec_text_query_plan**.  
  
-   Einige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen werden nicht zwischengespeichert. Beispiele hierfür sind Anweisungen für Massenvorgänge oder Anweisungen mit Zeichenfolgenliteralen, die größer als 8 KB sind. Showpläne für diese Anweisungen kann nicht abgerufen werden, mithilfe von **Sys. dm_exec_text_query_plan** , da sie nicht im Cache vorhanden sind.  
  
-   Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches oder gespeicherte Prozedur enthält einen Aufruf für eine benutzerdefinierte Funktion oder einen Aufruf für eine dynamische SQL, z. B. mit EXEC (*Zeichenfolge*), wird der kompilierte XML-Showplan, für die benutzerdefinierte Funktion nicht in der Tabelle enthalten ist zurückgegebenes **Sys. dm_exec_text_query_plan** für den Batch oder die gespeicherte Prozedur. Stattdessen müssen Sie einen separaten Aufruf von, **Sys. dm_exec_text_query_plan** für die *Plan_handle* , die der benutzerdefinierten Funktion entspricht.  
  
Wenn eine ad-hoc-Abfrage verwendet [einfache](../../relational-databases/query-processing-architecture-guide.md#SimpleParam) oder [erzwungene Parametrisierung](../../relational-databases/query-processing-architecture-guide.md#ForcedParam), **Query_plan** Spalte enthält nur den Text der Anweisung und nicht der tatsächliche Abfrageplan. Rufen Sie zum Zurückgeben des Abfrageplans **Sys. dm_exec_text_query_plan** für das planhandle der vorbereiteten parametrisierten Abfrage. Sie können anhand der **sql** -Spalte der [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md) -Sicht oder anhand der Textspalte der dynamischen [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) -Verwaltungssicht ermitteln, ob die Abfrage parametrisiert wurde.  
  
## <a name="permissions"></a>Berechtigungen  
 Auszuführende **Sys. dm_exec_text_query_plan**, ein Benutzer muss ein Mitglied der **Sysadmin** festen Serverrolle oder die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-retrieving-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. Abrufen des zwischengespeicherten Abfrageplans für eine langsam ausgeführte Transact-SQL-Abfrage oder einen langsam ausgeführten Transact-SQL-Batch  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage oder ein -Batch für lange Zeit mit einer bestimmten Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird, können Sie den Ausführungsplan für diese Abfrage oder diesen Batch abrufen, um die Ursache der Verzögerung zu ermitteln. Im folgenden Beispiel wird das Abrufen des Showplans für eine langsam ausgeführte Abfrage oder einen Batch gezeigt.  
  
> [!NOTE]  
> Ersetzen Sie zum Ausführen dieses Beispiels die Werte für *session_id* und *plan_handle* mit den Werten Ihres Servers.  
  
 Rufen Sie zunächst die Serverprozess-ID (SPID) für den Prozess ab, der die Abfrage oder den Batch ausführt, indem Sie die gespeicherte Prozedur `sp_who` verwenden:  
  
```sql  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
 Das von `sp_who` zurückgegebene Resultset gibt die SPID `54`an. Verwenden Sie die SPID nun mit der dynamischen Verwaltungssicht `sys.dm_exec_requests` , um das Planhandle mithilfe der folgenden Abfrage abzurufen:  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 Die Tabelle, die von zurückgegeben wird **Sys. dm_exec_requests** gibt an, dass das planhandle für die langsam ausgeführte Abfrage oder einen Batch `0x06000100A27E7C1FA821B10600`. Im folgenden Beispiel wird der Abfrageplan für das angegebene Planhandle zurückgegeben, und die Standardwerte 0 und -1 werden verwendet, um alle Anweisungen in der Abfrage oder im Batch zurückzugeben.  
  
```sql  
USE master;  
GO  
SELECT query_plan   
FROM sys.dm_exec_text_query_plan (0x06000100A27E7C1FA821B10600,0,-1);  
GO  
```  
  
### <a name="b-retrieving-every-query-plan-from-the-plan-cache"></a>B. Abrufen jedes einzelnen Abfrageplans aus dem Plancache  
 Wenn Sie eine Momentaufnahme aller im Plancache gespeicherten Abfragen abrufen möchten, rufen Sie die Planhandles aller Abfragepläne im Cache ab, indem Sie die dynamische Verwaltungssicht `sys.dm_exec_cached_plans` abfragen. Die Planhandles sind in der `plan_handle` -Spalte von `sys.dm_exec_cached_plans`gespeichert. Verwenden Sie dann den CROSS APPLY-Operator, um die Planhandles wie folgt an `sys.dm_exec_text_query_plan` zu übergeben. Die Showplanausgabe für jeden aktuell im Plancache gespeicherten Plan wird die `query_plan` -Spalte der Tabelle, die zurückgegeben wird.  
  
```sql  
USE master;  
GO  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_text_query_plan(cp.plan_handle, DEFAULT, DEFAULT);  
GO  
```  
  
### <a name="c-retrieving-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>C. Abrufen jedes einzelnen Abfrageplans für den Server aus dem Plancache Abfragestatistik erfasst hat  
 Wenn Sie eine Momentaufnahme aller im Plancache gespeicherten Abfragen abrufen möchten, für die der Server eine Statistik erfasst hat, rufen Sie die Planhandles dieser Pläne im Cache ab, indem Sie die dynamische Verwaltungssicht `sys.dm_exec_query_stats` abfragen. Die Planhandles sind in der `plan_handle` -Spalte von `sys.dm_exec_query_stats`gespeichert. Verwenden Sie dann den CROSS APPLY-Operator, um die Planhandles wie folgt an `sys.dm_exec_text_query_plan` zu übergeben. Die Showplanausgabe für die einzelnen Pläne befindet sich in der `query_plan`-Spalte der zurückgegebenen Tabelle.  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset);  
GO  
```  
  
### <a name="d-retrieving-information-about-the-top-five-queries-by-average-cpu-time"></a>D. Abrufen von Informationen zu den fünf Abfragen nach durchschnittlicher CPU-Zeit  
 Im folgenden Beispiel werden die Abfragepläne und die durchschnittliche CPU-Zeit für die fünf Abfragen mit der höchsten durchschnittlichen CPU-Zeit zurückgegeben. Die **Sys. dm_exec_text_query_plan** -Funktion gibt an, die Standardwerte 0 und 1, um alle Anweisungen im Batch im Abfrageplan zurückzugeben.  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, 0, -1)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
