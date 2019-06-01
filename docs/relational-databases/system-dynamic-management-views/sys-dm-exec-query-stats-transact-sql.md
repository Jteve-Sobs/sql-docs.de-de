---
title: Sys. dm_exec_query_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 821eaa4b7c54d8d2f449b2b071582480ac806378
ms.sourcegitcommit: 5905c29b5531cef407b119ebf5a120316ad7b713
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66429026"
---
# <a name="sysdmexecquerystats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die zusammengefasste Leistungsstatistik für zwischengespeicherte Abfragepläne in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurück. Diese Sicht enthält eine Zeile pro Abfrageanweisung innerhalb des zwischengespeicherten Plans, und die Lebensdauer der Zeilen ist an den Plan selbst gebunden. Wenn ein Plan aus dem Cache entfernt wird, werden die entsprechenden Zeilen aus dieser Sicht entfernt.  
  
> [!NOTE]
> Erste Abfrage von **Sys. dm_exec_query_stats** kann zu ungenauen Ergebnissen führen, wenn eine arbeitsauslastung, die gerade ausgeführt wird, auf dem Server vorhanden ist. Erneutes Ausführen der Abfrage liefert unter Umständen genauere Ergebnisse.  
  
> [!NOTE]
> Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_exec_query_stats**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary(64)**  |Ist ein Token, das den Batch eindeutig identifiziert oder die gespeicherte Prozedur, die die Abfrage angehört.<br /><br /> **Sql_handle**zusammen mit **Statement_start_offset** und **Statement_end_offset**, können verwendet werden, um den SQL-Text der Abfrage abzurufen, indem die **sys.dm_exec_sql_ Text** dynamische Verwaltungsfunktion.|  
|**statement_start_offset**|**int**|Gibt die Startposition der Abfrage, die in der Zeile beschrieben wird, beginnend mit 0 im Text des zugehörigen persistenten Objekts oder Batchobjekts an (in Bytes).|  
|**statement_end_offset**|**int**|Gibt die Endposition der Abfrage, die in der Zeile beschrieben wird, beginnend mit 0 im Text des zugehörigen persistenten Objekts oder Batchobjekts an (in Bytes). Für Versionen vor [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], der Wert-1 gibt das Ende des Batches. Nachfolgende Kommentare sind nicht mehr enthalten.|  
|**plan_generation_num**|**bigint**|Eine Sequenznummer, anhand der nach einer Neukompilierung zwischen einzelnen Instanzen von Plänen unterschieden werden kann.|  
|**plan_handle**|**varbinary(64)**|Ist ein Token, die eindeutig einen Abfrageplan für die Ausführung für einen Batch, die ausgeführt wurde und der Plan im Plancache befindet, oder wird gerade ausgeführt. Dieser Wert kann an übergeben werden die [Sys. dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) dynamische Verwaltungsfunktion, um den Abfrageplan abzurufen.<br /><br /> Ist immer 0x000, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**creation_time**|**datetime**|Der Zeitpunkt, zu dem der Plan kompiliert wurde.|  
|**last_execution_time**|**datetime**|Der Zeitpunkt, zu dem die Ausführung des Plans zuletzt gestartet wurde.|  
|**execution_count**|**bigint**|Die Anzahl von Planausführungen seit der letzten Kompilierung.|  
|**total_worker_time**|**bigint**|Die CPU-Gesamtzeit in Mikrosekunden (aber nur auf Millisekunden genau) für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Wenn zahlreiche Ausführungen weniger als 1 Millisekunde dauern, wird **total_worker_time** bei nativ kompilierten gespeicherten Prozeduren u.U. nicht exakt angegeben.|  
|**last_worker_time**|**bigint**|Die CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für die letzte Ausführung des Plans. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Die minimale CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Maximale CPU-Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Die Gesamtanzahl physischer Lesevorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_physical_reads**|**bigint**|Die Anzahl physischer Lesevorgänge bei der letzten Ausführung des Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_physical_reads**|**bigint**|Die bisherige minimale Anzahl physischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_physical_reads**|**bigint**|Die bisherige maximale Anzahl physischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_writes**|**bigint**|Die Gesamtanzahl logischer Schreibvorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_writes**|**bigint**|Anzahl der pufferpoolseiten verschmutzte während der zuletzt abgeschlossenen Ausführung des Plans.<br /><br />Nachdem eine Seite gelesen wird, ist das die Seite modifizierte nur beim ersten Mal, wenn, das es geändert wird. Wenn eine Seite geändert wird, wird diese Zahl erhöht. Nachfolgende Änderungen an einem bereits modifizierte Seite wirken sich nicht auf diese Zahl aus.<br /><br />Diese Zahl wird immer 0 sein, beim Abfragen einer speicheroptimierten Tabelle.|  
|**min_logical_writes**|**bigint**|Die bisherige minimale Anzahl logischer Schreibvorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_writes**|**bigint**|Die bisherige maximale Anzahl logischer Schreibvorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_reads**|**bigint**|Die Gesamtanzahl logischer Lesevorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_reads**|**bigint**|Die Anzahl logischer Lesevorgänge bei der letzten Ausführung des Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_logical_reads**|**bigint**|Die bisherige minimale Anzahl logischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_reads**|**bigint**|Die bisherige maximale Anzahl logischer Lesevorgänge für eine einzelne Ausführung dieses Plans.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_clr_time**|**bigint**|Zeit in Mikrosekunden (aber nur auf Millisekunden genau), in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common Language Runtime (CLR) Objekten für Ausführungen dieses Plans seit der Kompilierung. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**last_clr_time**|**bigint**|Zeit in Mikrosekunden (aber nur auf Millisekunden genau) Ausführung in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR-Objekte während der letzten Ausführung dieses Plans. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**min_clr_time**|**bigint**|Minimale Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR-Objekten. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**max_clr_time**|**bigint**|Maximale Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine einzelne Ausführung dieses Plans in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR. Die CLR-Objekte können gespeicherte Prozeduren, Funktionen, Trigger, Typen und Aggregate sein.|  
|**total_elapsed_time**|**bigint**|Insgesamt verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für abgeschlossene Ausführungen dieses Plans.|  
|**last_elapsed_time**|**bigint**|Verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für die letzte abgeschlossene Ausführung dieses Plans.|  
|**min_elapsed_time**|**bigint**|Mindestens verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine beliebige abgeschlossene Ausführung dieses Plans.|  
|**max_elapsed_time**|**bigint**|Maximal verstrichene Zeit in Mikrosekunden (aber nur auf Millisekunden genau) für eine beliebige abgeschlossene Ausführung dieses Plans.|  
|**query_hash**|**Binary(8)**|Binärer Hashwert, der in der Abfrage berechnet wird und zum Identifizieren von Abfragen mit ähnlicher Logik verwendet wird. Sie können den Abfragehash verwenden, um die aggregierte Ressourcennutzung für Abfragen zu ermitteln, die sich nur durch Literalwerte unterscheiden.|  
|**query_plan_hash**|**binary(8)**|Binärer Hashwert, der im Abfrageausführungsplan wird und zum Identifizieren ähnlicher Abfrageausführungspläne verwendet wird. Sie können diesen Abfrageplan-Hashwert verwenden, um die kumulierten Kosten für Abfragen mit ähnlichen Ausführungsplänen zu suchen.<br /><br /> Ist immer 0x000, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**total_rows**|**bigint**|Die Gesamtanzahl der von der Abfrage zurückgegebenen Zeilen. Lässt keine NULL-Werte zu.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**last_rows**|**bigint**|Die Anzahl der bei der letzten Ausführung der Abfrage zurückgegebenen Zeilen. Lässt keine NULL-Werte zu.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**min_rows**|**bigint**|Minimale Anzahl von einmal während einer Ausführung der Abfrage zurückgegebenen Zeilen. Lässt keine NULL-Werte zu.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**max_rows**|**bigint**|Maximale Anzahl von einmal während einer Ausführung der Abfrage zurückgegebenen Zeilen. Lässt keine NULL-Werte zu.<br /><br /> Ist immer 0, wenn eine systemintern kompilierte gespeicherte Prozedur eine speicheroptimierte Tabelle abfragt.|  
|**statement_sql_handle**|**varbinary(64)**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Mit nicht-NULL-Werte nur aufgefüllt, wenn Query Store aktiviert ist, und Sammeln von Statistiken für diese bestimmte Abfrage.|  
|**statement_context_id**|**bigint**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Mit nicht-NULL-Werte nur aufgefüllt, wenn Query Store aktiviert ist, und Sammeln von Statistiken für diese bestimmte Abfrage.|  
|**total_dop**|**bigint**|Gesamtsumme der Grad an Parallelität verwendet dieses Plans seit der Kompilierung. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_dop**|**bigint**|Der Grad der Parallelität, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_dop**|**bigint**|Der minimale Grad an Parallelität verwendet diesen Plan je während einer Ausführung. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_dop**|**bigint**|Der maximale Grad an Parallelität verwendet diesen Plan je während einer Ausführung. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_grant_kb**|**bigint**|Die Gesamtmenge des reservierten Arbeitsspeichers der arbeitsspeicherzuweisung in KB dieses Plans seit der Kompilierung erhalten. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_grant_kb**|**bigint**|Der Umfang des reservierten Arbeitsspeichers arbeitsspeicherzuweisung in KB, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_grant_kb**|**bigint**|Die Mindestmenge des reservierten Arbeitsspeichers der arbeitsspeicherzuweisung in KB dieses Plans jemals bei einer Ausführung übermittelt wurden. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_grant_kb**|**bigint**|Die maximale Größe des reservierten Speichers der arbeitsspeicherzuweisung in KB dieses Plans jemals bei einer Ausführung übermittelt wurden. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_grant_kb**|**bigint**|Die Gesamtmenge des reservierten Arbeitsspeichers gewähren in KB. dieser Plan verwendet wird, seit der Kompilierung. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_grant_kb**|**bigint**|Die Menge des verwendeten arbeitsspeicherzuweisung in KB, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_grant_kb**|**bigint**|Die minimale Größe des verwendeten Speichers der arbeitsspeicherzuweisung in KB dieser Plan während einer Ausführung hat Sie bisher verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_grant_kb**|**bigint**|Die maximale Größe des verwendeten Speichers der arbeitsspeicherzuweisung in KB dieser Plan während einer Ausführung hat Sie bisher verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_ideal_grant_kb**|**bigint**|Die Gesamtmenge der ideale arbeitsspeicherzuweisung in KB, die diesem Plan geschätzt, seit der Kompilierung. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_ideal_grant_kb**|**bigint**|Die ideale Speichermenge arbeitsspeicherzuweisung in KB, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_ideal_grant_kb**|**bigint**|Die Mindestmenge an der ideale Arbeitsspeicher in KB, die diesem Plan immer während einer Ausführung geschätzte gewähren. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_ideal_grant_kb**|**bigint**|Erteilen Sie die Höchstmenge der ideale Arbeitsspeicher in KB, die diesem Plan immer während einer Ausführung geschätzt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_reserved_threads**|**bigint**|Gesamtsumme der reservierten parallelen threads dieses Plans seit der Kompilierung verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_reserved_threads**|**bigint**|Die Anzahl der reservierten parallelen Threads, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_reserved_threads**|**bigint**|Die minimale Anzahl von reservierten parallelen threads diesen Plan während einer Ausführung hat Sie bisher verwendet.  Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_reserved_threads**|**bigint**|Die maximale Anzahl von reservierten parallelen threads diesen Plan während einer Ausführung hat Sie bisher verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_threads**|**bigint**|Gesamtsumme der verwendeten parallelen Threads dieses Plans seit der Kompilierung verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_threads**|**bigint**|Die Anzahl der verwendeten parallelen Threads, wenn dieser Plan zuletzt ausgeführt. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_threads**|**bigint**|Die minimale Anzahl von verwendet parallelen Threads, diesen Plan während einer Ausführung hat Sie bisher verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_threads**|**bigint**|Die maximale Anzahl von verwendet parallelen Threads, diesen Plan während einer Ausführung hat Sie bisher verwendet. Es wird immer 0 für die Abfrage einer speicheroptimierten Tabelle sein.<br /><br /> **Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_columnstore_segment_reads**|**bigint**|Gesamtsumme der columnstore-Segmente, die von der Abfrage zu lesen. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_reads**|**bigint**|Die Anzahl der columnstore-Segmente, die von der letzten Ausführung der Abfrage gelesen. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_reads**|**bigint**|Die minimale Anzahl von columnstore-Segmente, die jemals während einer Ausführung von der Abfrage gelesen werden soll. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_reads**|**bigint**|Die maximale Anzahl von columnstore-Segmente, die jemals während einer Ausführung von der Abfrage gelesen werden soll. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**total_columnstore_segment_skips**|**bigint**|Gesamtsumme der columnstore-Segmente, die von der Abfrage ausgelassen. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_skips**|**bigint**|Die Anzahl der columnstore-Segmente, die von der letzten Ausführung der Abfrage ausgelassen. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_skips**|**bigint**|Die minimale Anzahl von columnstore-Segmente, die je von der Abfrage bei einer Ausführung übersprungen werden soll. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_skips**|**bigint**|Die maximale Anzahl von columnstore-Segmente, die je von der Abfrage bei einer Ausführung übersprungen werden soll. Lässt keine NULL-Werte zu.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|
|**total_spills**|**bigint**|Die Gesamtanzahl der Seiten, die durch die Ausführung dieser Abfrage überlaufen, seit der Kompilierung.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Die Anzahl der Seiten überlaufen, Zeitpunkt der letzten der Abfrage Ausführung.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Die minimale Anzahl der Seiten, die diese Abfrage immer eine einzelne Ausführung übergelaufen.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Die maximale Anzahl der Seiten, die diese Abfrage immer eine einzelne Ausführung übergelaufen.<br /><br /> **Gilt für**: Beginnend mit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.<br /><br /> **Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 
|**total_page_server_reads**|**bigint**|Gesamtanzahl der remote-Seite Server Lesevorgänge für Ausführungen dieses Plans seit der Kompilierung.<br /><br /> **Gilt für:** Azure SQL DB Hyperskalierung |  
|**last_page_server_reads**|**bigint**|Die Anzahl der entfernten Server Seitenlesevorgänge bei der letzten Ausführung des Plans.<br /><br /> **Gilt für:** Azure SQL DB Hyperskalierung |  
|**min_page_server_reads**|**bigint**|Minimale Anzahl von remote-Seitenserver liest, die diesem Plan immer eine einzelne Ausführung ausgeführt hat.<br /><br /> **Gilt für:** Azure SQL DB Hyperskalierung |  
|**max_page_server_reads**|**bigint**|Maximale Anzahl von remote-Seitenserver liest, die diesem Plan immer eine einzelne Ausführung ausgeführt hat.<br /><br /> **Gilt für:** Azure SQL DB Hyperskalierung |  
> [!NOTE]
> <sup>1</sup> für systemintern kompilierte gespeicherte Prozeduren bei der Sammlung von Statistiken aktiviert ist, wird worker_time in Millisekunden. Wenn die Abfrage in weniger als einer Millisekunde ausgeführt wird, wird der Wert 0 sein.  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
   
## <a name="remarks"></a>Hinweise  
 Statistiken in der Sicht werden nach Abschluss einer Abfrage aktualisiert.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-finding-the-top-n-queries"></a>A. Suchen der TOP-N-Abfragen  
 Das folgende Beispiel gibt Informationen zu den fünf Abfragen mit dem höchsten durchschnittlichen CPU-Zeitaufwand zurück. Die Abfragen werden in diesem Beispiel anhand des Abfragehashes aggregiert, sodass logisch identische Abfragen basierend auf dem kumulierten Ressourcenverbrauch gruppiert werden.  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>B. Zurückgeben der aggregierten Zeilenanzahlen für eine Abfrage  
 Im folgenden Beispiel werden Informationen zu aggregierten Zeilenanzahlen (Gesamtanzahl der Zeilen, minimale Anzahl der Zeilen, maximale Anzahl der Zeilen und letzte Zeilen) für Abfragen zurückgegeben.  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>Siehe auch  
[Ausführung bezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


