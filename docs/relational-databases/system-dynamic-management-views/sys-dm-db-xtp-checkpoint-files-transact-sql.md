---
title: Sys. dm_db_xtp_checkpoint_files (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_files
- sys.dm_db_xtp_checkpoint_files_TSQL
- dm_db_xtp_checkpoint_files_TSQL
- sys.dm_db_xtp_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_files dynamic management view
ms.assetid: ac8e6333-7a9f-478a-b446-5602283e81c9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2c7f7f4296b3cbed025303f58cf07717db06c8e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510866"
---
# <a name="sysdmdbxtpcheckpointfiles-transact-sql"></a>sys.dm_db_xtp_checkpoint_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Zeigt Informationen zu Prüfpunktdateien, einschließlich Dateigröße, physischem Speicherort und der Transaktions-ID an.  
  
> **HINWEIS:** Für den aktuellen Prüfpunkt, der nicht die Zustandsspalte von s geschlossen, verfügt über`ys.dm_db_xtp_checkpoint_files` werden für neue Dateien UNDER CONSTRUCTION. Ein Prüfpunkt wird automatisch geschlossen, wenn ausreichend Wachstumsrate des Transaktionsprotokolls seit dem letzten Prüfpunkt vorhanden ist oder Sie geben die `CHECKPOINT` Befehl ([PRÜFPUNKT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)).  
  
 Eine Speicheroptimierte Dateigruppe verwendet intern nur-Anhängen-Dateien zum eingefügte und gelöschte Zeilen für speicherinterne Tabellen zu speichern. Es gibt zwei Typen von Dateien. Eine Datendatei enthält eingefügte Zeilen an, während eine Änderungsdatei Verweise auf gelöschte Zeilen enthält. 
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterscheidet sich deutlich von neueren Versionen und wird im Thema zur niedriger erläutert [SQL Server 2014](#bkmk_2014).  
  
 Weitere Informationen finden Sie unter [erstellen und Verwalten von Speicher für arbeitsspeicheroptimierte Objekte](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
##  <a name="bkmk_2016"></a> [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher  
 Die folgende Tabelle beschreibt die Spalten für `sys.dm_db_xtp_checkpoint_files`ab **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]**.  
  
|Spaltenname|Typ|Description|  
|-----------------|----------|-----------------|  
|container_id|**int**|Die ID des Containers (in sys.database_files als Datei vom Typ FILESTREAM dargestellt), dem die Daten- oder Änderungsdatei angehört. Joins mit File_id in [Sys. database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|GUID des Containers, in dem das Stammverzeichnis, Daten- oder Änderungsdatei angehört. Joins mit File_guid in der Sys. database_files-Tabelle.|  
|checkpoint_file_id|**uniqueidentifier**|Die GUID der Prüfpunktdatei.|  
|relative_file_path|**nvarchar(256)**|Pfad der Datei relativ zum Container, den er zugeordnet ist.|  
|file_type|**smallint**|-1 für FREE<br /><br /> 0 für die Datendatei.<br /><br /> 1 für die Änderungsdatei.<br /><br /> 2 für Stammdatei<br /><br /> 3 für große Datendatei|  
|file_type_desc|**nvarchar(60)**|FREE - All-Dateien, die verwaltet werden, als frei sind für die Zuordnung verfügbar. Kostenlose Dateien können vom System Größe sich je nach Voraussichtlicher Anforderungen variieren. Die maximale Größe beträgt 1GB.<br /><br /> Daten per Push –-Datendateien enthalten Zeilen, die in speicheroptimierten Tabellen eingefügt wurden.<br /><br /> DELTA - Delta-Dateien enthalten Verweise auf Zeilen in Dateien, die gelöscht wurden.<br /><br /> ROOT - Stammdateien enthalten die Metadaten des Dateisystems für den speicheroptimierten und systemintern kompilierten Objekte.<br /><br /> GROßE - Videodaten große Datendateien Werte eingefügt ((n)varchar(max) und varbinary(max) Spalten, sowie die spaltensegmente, die Teil des columnstore-Indizes für Speicheroptimierte Tabellen sind.|  
|internal_storage_slot|**int**|Der Index der Datei im internen Speicherarray. NULL für Stamm- oder anderen Zustand als 1.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Datei der entsprechenden Daten- oder ÄNDERUNGSDATEI. NULL für den Stamm.|  
|file_size_in_bytes|**bigint**|Die Größe der Datei auf dem Datenträger.|  
|file_size_used_in_bytes|**bigint**|Bei Prüfpunktdateipaaren, die noch mit Daten aufgefüllt werden, wird diese Spalte nach dem nächsten Prüfpunkt aktualisiert.|  
|logical_row_count|**bigint**|Für Daten, die Anzahl der eingefügten Zeilen.<br /><br /> Delta Anzahl der Zeilen nach Berücksichtigung Drop Table gelöscht.<br /><br /> Für den Stamm, NULL-Wert.|  
|state|**smallint**|0 – VORAB ERSTELLTE<br /><br /> 1 – IN BEARBEITUNG<br /><br /> 2 - ACTIVE<br /><br /> 3 - MERGE-ZIEL<br /><br /> 8: AUF PROTOKOLLKÜRZUNG WARTENDE|  
|state_desc|**nvarchar(60)**|PRECREATED - werden eine Reihe von Prüfpunktdateien vorab zugeordnet ist, zu minimieren oder eliminieren Wartezeiten bei der Zuordnung neue Dateien während der Ausführung von Transaktionen. Diese im Voraus erstellten Dateien können variieren, je nach den geschätzten Anforderungen der Workload, die Größe, aber sie enthalten keine Daten. Dies ist eine speichermehraufwand in Datenbanken mit einer MEMORY_OPTIMIZED_DATA-Dateigruppe.<br /><br /> IN Bearbeitung – diese Prüfpunktdateien befinden sich in Bearbeitung, was bedeutet, dass sie basierend auf den Protokolldatensätzen, die von der Datenbank generiert aufgefüllt werden und sind noch nicht Bestandteil eines Prüfpunkts.<br /><br /> ACTIVE – diese enthalten, dass die eingefügten/gelöschten Zeilen aus den vorherigen geschlossenen Prüfpunkten. Sie enthalten den Inhalt der Tabellen, die Bereich in den Arbeitsspeicher gelesen werden, bevor der aktive Teil des Transaktionsprotokolls beim Neustart Datenbank angewendet. Wir erwarten, dass dieser Größe diese Prüfpunktdateien sein, dass etwa 2 X, der in-Memory-Größe der speicheroptimierten Tabellen verwendet werden, vorausgesetzt des Zusammenführungsvorgangs mit der transaktionsarbeitslast Schritt halten kann.<br /><br /> MERGE TARGET – das Ziel von zusammenführungsvorgängen: Diese Prüfpunktdateien speichern die konsolidierten Datenzeilen aus den Quelldateien, die von der Zusammenführungsrichtlinie identifiziert wurden. Nachdem die Zusammenführung installiert wurde, befinden sich die MERGE TARGET-Übergänge im Status ACTIVE.<br /><br /> Auf PROTOKOLLKÜRZUNG WARTENDE – sobald die Zusammenführung installiert wurde und das MERGE TARGET-CFP Bestandteil eines dauerhaften Prüfpunkts, Merge Source-Prüfpunktdateien in diesen Zustand. Dateien in diesem Zustand werden für den ordnungsgemäßen Betrieb der Datenbank mit einer speicheroptimierten Tabelle benötigt.  Dies gilt beispielsweise für die Wiederherstellung von einem dauerhaften Prüfpunkt, um zu einem früheren Zustand zurückzukehren.|  
|lower_bound_tsn|**bigint**|Untere Grenze der Transaktion in der Datei; NULL, wenn nicht im Status (1, 3).|  
|upper_bound_tsn|**bigint**|Obere Grenze der Transaktion in der Datei; NULL, wenn nicht im Status (1, 3).|  
|begin_checkpoint_id|**bigint**|Die ID des Prüfpunkts Begin.|  
|end_checkpoint_id|**bigint**|Die ID des Prüfpunkts End.|  
|last_updated_checkpoint_id|**bigint**|Die ID des letzten Prüfpunkts, die diese Datei aktualisiert.|  
|encryption_status|**smallint**|0, 1, 2|  
|encryption_status_desc|**nvarchar(60)**|0 = &GT; UNENCRTPTED<br /><br /> 1 = &GT; VERSCHLÜSSELT MIT SCHLÜSSEL 1<br /><br /> 2 = &GT; MIT SCHLÜSSEL 2 VERSCHLÜSSELT. Dies gilt nur für aktive Dateien.|  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 Die folgende Tabelle beschreibt die Spalten für `sys.dm_db_xtp_checkpoint_files`, für die **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]**.  
  
|Spaltenname|Typ|Description|  
|-----------------|----------|-----------------|  
|container_id|**int**|Die ID des Containers (in sys.database_files als Datei vom Typ FILESTREAM dargestellt), dem die Daten- oder Änderungsdatei angehört. Joins mit File_id in [Sys. database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|Die GUID des Containers, dem die Daten- oder Änderungsdatei angehört.|  
|checkpoint_file_id|**GUID**|Die ID der Daten- oder Änderungsdatei.|  
|relative_file_path|**nvarchar(256)**|Der Pfad zu der Daten- oder Änderungsdatei relativ zum Speicherort des Containers.|  
|file_type|**tinyint**|0 für die Datendatei.<br /><br /> 1 für die Änderungsdatei.<br /><br /> NULL, wenn die Zustandsspalte auf 7 festgelegt ist.|  
|file_type_desc|**nvarchar(60)**|Dateityp: DATA_FILE, DELTA_FILE oder NULL, wenn die Zustandsspalte auf 7 festgelegt ist.|  
|internal_storage_slot|**int**|Der Index der Datei im internen Speicherarray. NULL, wenn die Zustandsspalte auf 2 oder 3 festgelegt ist.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Die entsprechende Daten- oder Änderungsdatei.|  
|file_size_in_bytes|**bigint**|Die Größe der Datei, die verwendet wird. NULL, wenn die Zustandsspalte auf 5, 6 oder 7 festgelegt ist.|  
|file_size_used_in_bytes|**bigint**|Die verwendete Größe der betreffenden Datei. NULL, wenn die Zustandsspalte auf 5, 6 oder 7 festgelegt ist.<br /><br /> Bei Prüfpunktdateipaaren, die noch mit Daten aufgefüllt werden, wird diese Spalte nach dem nächsten Prüfpunkt aktualisiert.|  
|inserted_row_count|**bigint**|Die Anzahl der Zeilen in der Datendatei.|  
|deleted_row_count|**bigint**|Die Anzahl der gelöschten Zeilen in der Änderungsdatei.|  
|drop_table_deleted_row_count|**bigint**|Die Anzahl der Zeilen in den Datendateien, auf die sich die Tabellenlöschung auswirkt. Gilt für Datendateien, wenn die Zustandsspalte gleich 1 ist.<br /><br /> Zeigt die Anzahl der aus gelöschten Tabellen gelöschten Zeilen an. Statistiken drop_table_deleted_row_count werden kompiliert, nachdem die Arbeitsspeicher-Garbage Collection für die Zeilen aus gelöschten Tabellen abgeschlossen und ein Prüfpunkt erstellt wurde. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu starten, bevor die Statistiken zu gelöschten Tabellen in dieser Spalte angezeigt werden, werden sie im Rahmen der Wiederherstellung aktualisiert. Bei der Wiederherstellung werden keine Zeilen aus gelöschten Tabellen geladen. Statistiken zu gelöschten Tabellen werden während der Ladephase kompiliert und in dieser Spalte wiedergegeben, sobald die Wiederherstellung abgeschlossen ist.|  
|state|**int**|0 – VORAB ERSTELLTE<br /><br /> 1 – IN BEARBEITUNG<br /><br /> 2 - ACTIVE<br /><br /> 3 - MERGE-ZIEL<br /><br /> 4 – ZUSAMMENGEFÜHRTE QUELLDATEIEN<br /><br /> 5 – ERFORDERLICHE FOR BACKUP/HA<br /><br /> 6 – ÜBERGANG ZU TOMBSTONE<br /><br /> 7 - TOMBSTONING|  
|state_desc|**nvarchar(60)**|PRECREATED – eine kleine Gruppe von Daten / änderungsdateipaaren, auch bekannt als prüfpunktdateipaare (CFPs) wird dauerhaft vorab zugeordnet, zu minimieren bzw. eliminieren Wartezeiten bei der Zuordnung neue Dateien während der Ausführung von Transaktionen. Dabei handelt es sich um Datendateien mit der vollständigen Größe von 128 MB und 8 MB große Änderungsdateien, die jedoch keine Daten enthalten. Die Anzahl der CFPs wird aus der Anzahl von logischen Prozessoren oder Zeitplanungsmodulen (einer pro Kern, kein Höchstwert) berechnet und beträgt mindestens 8. Dies ist ein fester Speichermehraufwand in Datenbanken mit speicheroptimierten Tabellen.<br /><br /> IN Bearbeitung - Satz von CFPs zur Speicherung neu eingefügt und möglicherweise gelöschter Datenzeilen seit dem letzten Prüfpunkt.<br /><br /> ACTIVE – Diese enthalten die eingefügten und gelöschten Zeilen aus den vorherigen geschlossenen Prüfpunkten. Diese CFPs enthalten alle erforderlichen eingefügten und gelöschten Zeilen, bevor der aktive Teil des Transaktionsprotokolls beim Neustart der Datenbank angewendet wird. Diese CFPs sind etwa doppelt so groß wie die In-Memory-Größe speicheroptimierter Tabellen, vorausgesetzt, die Zusammenführung hält mit der Transaktionsarbeitsauslastung mit.<br /><br /> MERGE TARGET – das CFP speichert die konsolidierten Datenzeilen aus den cfps, die von der Zusammenführungsrichtlinie identifiziert wurden. Nachdem die Zusammenführung installiert wurde, befinden sich die MERGE TARGET-Übergänge im Status ACTIVE.<br /><br /> MERGED SOURCE – nachdem der Zusammenführungsvorgang installiert ist, werden die Quell-CFPs als MERGED SOURCE gekennzeichnet. Beachten Sie, dass die Auswertung der Zusammenführungsrichtlinie mehrere Zusammenführungen identifizieren kann, ein CFP jedoch nur an einem Zusammenführungsvorgang beteiligt sein darf.<br /><br /> Ist erforderlich FOR BACKUP/HA – sobald die Zusammenführung installiert wurde und das MERGE TARGET-CFP Bestandteil eines dauerhaften Prüfpunkts, der zusammenführungsquelle Übergang von CFPs in diesem Zustand. CFPs in diesem Zustand werden benötigt, um die nahtlose Verwendung der Datenbank mit der speicheroptimierten Tabelle sicherzustellen.  Dies gilt beispielsweise für die Wiederherstellung von einem dauerhaften Prüfpunkt, um zu einem früheren Zustand zurückzukehren. Ein CFP kann für die Garbage Collection gekennzeichnet werden, sobald der Protokollkürzungspunkt hinter dem Transaktionsbereich liegt.<br /><br /> IN TRANSITION TO TOMBSTONE – können diese CFPs werden nicht von der In-Memory-OLTP-Engine benötigt und sie können Garbage collection. Dieser Status gibt an, dass diese CFPs warten, bis sie vom Hintergrundthread in den nächsten Zustand (d. h. TOMBSTONE) versetzt werden.<br /><br /> TOMBSTONE – diese CFPs Garbage Collection durch den Filestream-Garbage Collector bereinigt werden sollen. ([Sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md))|  
|lower_bound_tsn|**bigint**|Die untere Grenze für Transaktionen, die in der Datei enthalten sind. NULL, wenn die Zustandsspalte ungleich 2, 3 oder 4 ist.|  
|upper_bound_tsn|**bigint**|Die obere Grenze für Transaktionen, die in der Datei enthalten sind. NULL, wenn die Zustandsspalte ungleich 2, 3 oder 4 ist.|  
|last_backup_page_count|**int**|Die logische Seitenanzahl, die bei der letzten Sicherung bestimmt wird. Diese gilt, wenn die Zustandsspalte auf 2, 3, 4 oder 5 festgelegt ist. NULL, wenn die Seitenanzahl unbekannt ist.|  
|delta_watermark_tsn|**int**|Die Transaktion des letzten Prüfpunkts, von dem in diese Änderungsdatei geschrieben wurde. Dies ist das Wasserzeichen der Änderungsdatei.|  
|last_checkpoint_recovery_lsn|**nvarchar(23)**|Die Wiederherstellungs-Protokollfolgenummer des letzten Prüfpunkts, von dem die Datei noch benötigt wird.|  
|tombstone_operation_lsn|**nvarchar(23)**|Die Datei wird gelöscht, sobald tombstone_operation_lsn hinter der Protokollfolgenummer des Protokollkürzungspunkts zurückfällt.|  
|logical_deletion_log_block_id|**bigint**|Gilt nur für Zustand 5.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung auf dem Server.  
  
## <a name="use-cases"></a>Anwendungsfälle  
 Sie können die speichernutzung In-Memory OLTP wie folgt schätzen:  
  
```  
-- total storage used by In-Memory OLTP  
SELECT SUM (file_size_in_bytes)/(1024*1024) as file_size_in_MB  
FROM sys.dm_db_xtp_checkpoint_files  
```  
  
  
So zeigen eine Aufschlüsselung der speicherauslastung nach Status und die Datei die folgende Abfrage ausführen:
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(file_size_in_bytes) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  

  
## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
