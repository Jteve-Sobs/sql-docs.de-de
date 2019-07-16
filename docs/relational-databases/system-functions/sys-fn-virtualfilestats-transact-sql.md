---
title: Sys. fn_virtualfilestats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_virtualfilestats_TSQL
- fn_virtualfilestats
dev_langs:
- TSQL
helpviewer_keywords:
- I/O [SQL Server], statistics
- fn_virtualfilestats function
- sys.fn_virtualfilestats function
- statistical information [SQL Server], I/O
ms.assetid: 96b28abb-b059-48db-be2b-d60fe127f6aa
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aade9e02515e0d18e4edae188d72e5edafebbd3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059182"
---
# <a name="sysfnvirtualfilestats-transact-sql"></a>sys.fn_virtualfilestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt E/A-Statistiken für Datenbankdateien zurück, einschließlich Protokolldateien. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Informationen sind auch verfügbar, aus der [Sys. dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) dynamische verwaltungssicht.  

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_virtualfilestats ( { database_id | NULL } , { file_id | NULL } )  
```  
  
## <a name="arguments"></a>Argumente  
 *Database_id* | NULL  
 Ist die ID der Datenbank. *database_id* ist vom Datentyp **int**und hat keinen Standardwert. Geben Sie NULL an, wenn Informationen zu allen Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben werden sollen.  
  
 *FILE_ID* | NULL  
 Die ID der Datei. *file_id* ist vom Datentyp **int**und hat keinen Standardwert. Geben Sie NULL an, wenn Informationen zu allen Dateien in der Datenbank zurückgegeben werden sollen.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**DbId**|**smallint**|Datenbank-ID|  
|**FileId**|**smallint**|Die Datei-ID|  
|**TimeStamp**|**bigint**|Datenbanktimestamp für den Zeitpunkt, zu dem die Daten erhoben wurden **Int** in Versionen vor [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]. |  
|**NumberReads**|**bigint**|Die Anzahl der Lesevorgänge, die für die Datei ausgegeben wurden.|  
|**BytesRead**|**bigint**|Anzahl der Bytes, die aus der Datei gelesen wurden|  
|**IoStallReadMS**|**bigint**|Gesamtzeit in Millisekunden, die die Benutzer darauf gewartet haben, dass E/A-Leseoperationen für die Datei abgeschlossen wurden|  
|**NumberWrites**|**bigint**|Anzahl der Schreibvorgänge, die für die Datei ausgeführt wurden|  
|**BytesWritten**|**bigint**|Anzahl der Bytes, die in die Datei geschrieben wurden|  
|**IoStallWriteMS**|**bigint**|Gesamtzeit in Millisekunden, die die Benutzer darauf gewartet haben, dass E/A-Schreiboperationen für die Datei abgeschlossen wurden|  
|**IoStallMS**|**bigint**|Summe der **IoStallReadMS** und **IoStallWriteMS**.|  
|**FileHandle**|**bigint**|Wert des Dateihandles|  
|**BytesOnDisk**|**bigint**|Die physische Dateigröße (Anzahl der Bytes) auf dem Datenträger.<br /><br /> Für Datenbankdateien, ist dies der gleiche Wert wie **Größe** in **Sys. database_files**, aber in Byte anstatt in Seiten ausgedrückt wird.<br /><br /> Bei Sparsedateien von Datenbankmomentaufnahmen ist dies der Speicherplatz, den das Betriebssystem für die Datei in Anspruch nimmt.|  
  
## <a name="remarks"></a>Hinweise  
 **Fn_virtualfilestats** ist ein System-Tabellenwertfunktion, die statistische Informationen, z. B. die Gesamtanzahl der e/as zu erhalten, die für eine Datei ausgeführt. Diese Funktion hilft beim Verfolgen der Zeitdauer, die Benutzer warten müssen, um eine Datei zu lesen oder darin zu schreiben. Diese Funktion hilft außerdem beim Identifizieren der Dateien mit hoher E/A-Aktivität.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-statistical-information-for-a-database"></a>A. Anzeigen von statistischen Informationen zu einer Datenbank  
 Das folgende Beispiel zeigt statistische Informationen zur Datei ID 1 in der Datenbank an, die die ID `1` hat.  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(1, 1);  
GO  
```  
  
### <a name="b-displaying-statistical-information-for-a-named-database-and-file"></a>B. Anzeigen von statistischen Informationen zu einer benannten Datenbank und Datei  
 Das folgende Beispiel zeigt statistische Informationen zur Protokolldatei in der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] an. Die Systemfunktion `DB_ID` dient zum Angeben der *Database_id* Parameter.  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="c-displaying-statistical-information-for-all-databases-and-files"></a>C. Anzeigen von statistischen Informationen zu allen Datenbanken und Dateien  
 Das folgende Beispiel zeigt statistische Informationen zu allen Dateien in allen Datenbanken der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an.  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(NULL,NULL);  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DB_ID &#40;Transact-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md)   
 [FILE_IDEX &#40;Transact-SQL&#41;](../../t-sql/functions/file-idex-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
