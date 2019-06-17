---
title: Sys. dm_db_missing_index_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fc72e290bf1aa495493eb09d5e0db8cf305202e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62508249"
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt detaillierte Informationen zu fehlenden Indizes, außer räumlichen Indizes, zurück.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, diese Informationen bereitstellen, wird jede Zeile, die Daten enthält, die zum verbundenen Mandanten gehören nicht herausgefiltert.  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Identifiziert einen bestimmten fehlenden Index. Der Bezeichner ist innerhalb des Servers eindeutig. **Index_handle** ist der Schlüssel dieser Tabelle.|  
|**database_id**|**smallint**|Identifiziert die Datenbank, in der sich die Tabelle mit dem fehlenden Index befindet.|  
|**object_id**|**int**|Identifiziert die Tabelle, in der der Index fehlt.|  
|**equality_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zu Gleichheitsprädikaten der folgenden Form beitragen:<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zu Ungleichheitsprädikaten beispielsweise der folgenden Form beitragen:<br /><br /> *table.column* > *constant_value*<br /><br /> Jeder Vergleichsoperator außer "=" drückt Ungleichheit aus.|  
|**included_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zur Abdeckung der Abfrage benötigt werden. Weitere Informationen zu abdeckenden oder eingeschlossenen Spalten finden Sie unter [Erstellen von Indizes mit eingeschlossenen Spalten](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Für Speicheroptimierte Indizes (sowohl Hashindizes als auch Speicheroptimierte nicht gruppierte), ignorieren **Included_columns**. Alle Spalten der Tabelle werden in jeden speicheroptimierten Index eingeschlossen.|  
|**statement**|**nvarchar(4000)**|Der Name der Tabelle, in der der Index fehlt.|  
  
## <a name="remarks"></a>Hinweise  
 Informationen, die vom **Sys. dm_db_missing_index_details** wird aktualisiert, wenn eine Abfrage vom Abfrageoptimierer optimiert wird, und wird nicht beibehalten. Informationen zu fehlenden Indizes werden nur bis zum Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbewahrt. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Informationen zu fehlenden Indizes erstellen, wenn Sie sie nach dem Wiederverwenden des Servers beibehalten möchten.  
  
 Um zu bestimmen, welche fehlender Index einen bestimmten fehlenden Index gruppiert ist Teil, Sie können Abfragen, die **Sys. dm_db_missing_index_groups** dynamische verwaltungssicht von gleichheitsjoin mit **Sys. dm_db_missing_index_details**  basierend auf den **Index_handle** Spalte.  

  >[!NOTE]
  >Das Resultset für diese DMV wird auf 600 Zeilen beschränkt. Jede Zeile enthält einen fehlenden Index. Wenn Sie mehr als 600 fehlende Indizes verfügen, sollten Sie die vorhandenen fehlende Indizes behandeln, damit Sie Sie dann die neuere anzeigen können. 
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Verwenden von Informationen zu fehlenden Indizes in CREATE INDEX-Anweisungen  
 Konvertieren von zurückgegebene Informationen **Sys. dm_db_missing_index_details** in eine CREATE INDEX-Anweisung für sowohl Speicheroptimierte und datenträgerbasierte Indizes gleichheitsspalten vor die ungleichheitsspalten und zusammen gesetzt werden soll Diese sollten den Schlüssel des Indexes bilden. Eingeschlossene Spalten sollten der CREATE INDEX-Anweisung mithilfe der INCLUDE-Klausel hinzugefügt werden. Für eine effektive Reihenfolge der Gleichheitsspalten sortieren Sie sie nach ihrer Selektivität, wobei Sie die ausgewählten Spalten zuerst (am weitesten links in der Spaltenliste) aufführen.  
  
 Weitere Informationen zu speicheroptimierten Indizes finden Sie unter [Indizes für Speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Transaktionskonsistenz  
 Wenn durch eine Transaktion eine Tabelle erstellt oder gelöscht wird, werden die Zeilen mit Informationen zu fehlenden Indizes bezüglich der gelöschten Objekte aus diesem dynamischen Verwaltungsobjekt entfernt, damit die Transaktionskonsistenz erhalten bleibt.  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="see-also"></a>Siehe auch  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
