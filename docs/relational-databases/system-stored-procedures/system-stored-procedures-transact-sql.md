---
title: Gespeicherte System Prozeduren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.TSQLSysNoExpandPortal.f1
- sql13.TSQLSysNoExpandPortal.f1_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server]
- APIs [SQL Server]
- stored procedures [SQL Server], categories
- system stored procedures [SQL Server], categories
- system stored procedures [SQL Server]
ms.assetid: a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 020d75e780dcc2036b70348fa57cf1007ce0e401
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037320"
---
# <a name="system-stored-procedures-transact-sql"></a>Gespeicherte Systemprozeduren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] können viele Verwaltungs- und Informationsabläufe mithilfe gespeicherter Systemprozeduren ausgeführt werden. Die gespeicherten Systemprozeduren sind in die in der folgenden Tabelle gezeigten Kategorien unterteilt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Category|BESCHREIBUNG|  
|--------------|-----------------|  
|[Gespeicherte Prozeduren für die aktive georeplikation](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Dient zum Verwalten von zum Verwalten von Konfigurationen für die aktive georeplikation in Azure SQL-Datenbank.|  
|[Gespeicherte Katalogprozeduren](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Implementieren Funktionen ODBC-Datenwörterbüchern und isolieren ODBC-Anwendungen von Änderungen an den zugrunde liegenden Systemtabellen.|  
|[Gespeicherte Prozeduren für Change Data Capture](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Wird verwendet, um Change Data Capture-Objekte zu aktivieren, zu deaktivieren oder über sie zu berichten.|  
|[Gespeicherte Cursorprozeduren](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Werden zum Implementieren von Cursorvariablenfunktionen verwendet.|  
|[Gespeicherte Prozeduren für den Datensammler](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Wird zum Arbeiten mit dem Datensammler und folgenden Komponenten verwendet: Auflistsätze, Auflistelemente und Auflisttypen.|  
|[Gespeicherte Datenbank-Engine-Prozeduren](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Werden für die allgemeine Wartung von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwendet.|  
|[Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Werden zum Ausführen von E-Mail-Operationen innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.|  
|[Gespeicherte Prozeduren für Datenbank-Wartungspläne](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Werden zum Einrichten zentraler Wartungsaufgaben verwendet, die zur Optimierung der Datenbankleistung ausgeführt werden müssen.|  
|[Gespeicherte Prozeduren für verteilte Abfragen](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Werden zum Implementieren und Verwalten verteilter Abfragen verwendet.|  
|[Gespeicherte FILESTREAM-und FILETABLE-Prozeduren &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Werden zum Konfigurieren und Verwalten der FILESTREAM- und FileTable-Funktionen verwendet.|  
|[Gespeicherte Prozeduren für Firewallregeln &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Wird zum Konfigurieren der Firewall für die Azure SQL-Datenbank verwendet.|  
|[Gespeicherte Prozeduren für die Volltextsuche](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Werden zum Implementieren und Abfragen von Volltextindizes verwendet.|  
|[Gespeicherte allgemeine erweiterte Prozeduren](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Werden zur Bereitstellung einer Schnittstelle zwischen einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und externen Programmen für verschiedene Wartungsaktivitäten verwendet.|  
|[Gespeicherte Prozeduren für den Protokollversand](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Werden zum Konfigurieren, Ändern und Überwachen von Protokollversandkonfigurationen verwendet.|  
|[Gespeicherte Prozeduren für das Verwaltungs-Data Warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Wird verwendet, um die Verwaltungs Data Warehouse zu konfigurieren.|  
|[Gespeicherte OLE-Automatisierungs Prozeduren](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Werden zur Aktivierung standardmäßiger Automatisierungsobjekte für die Verwendung innerhalb eines [!INCLUDE[tsql](../../includes/tsql-md.md)]-Standardbatches verwendet.|  
|[Gespeicherte Prozeduren für die richtlinienbasierte Verwaltung](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Werden für die richtlinienbasierte Verwaltung verwendet.|  
|[Gespeicherte PolyBase-Prozeduren](https://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Hinzufügen oder Entfernen eines Computers aus einer polybase-Erweiterungsgruppe.|  
|[Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Dient zum Optimieren der Leistung.|  
|[Gespeicherte Replikations Prozedur](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Werden für die Replikation verwendet.|  
|[Gespeicherte Sicherheitsprozeduren](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Werden für die Verwaltung der Sicherheit verwendet.|  
|[Gespeicherte Momentaufnahme Sicherungs Prozeduren](https://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Wird verwendet, um die FILE_SNAPSHOT Sicherung zusammen mit allen zugehörigen Momentaufnahmen zu löschen oder eine einzelne Sicherungsdatei-Momentaufnahme zu löschen.|  
|[Gespeicherte Prozeduren für Räumlichkeitsindizes](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Wird verwendet, um die Indexleistung räumlicher Indizes zu analysieren und zu verbessern.|  
|[Gespeicherte SQL Server-Agent-Prozeduren](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Werden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwendet, um die Leistung und die Aktivitäten zu überwachen.|  
|[Gespeicherte Prozeduren für SQL Server Profiler](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent zum Verwalten geplanter und ereignisgesteuerter Aktivitäten verwendet.|  
|[Gespeicherte Prozeduren Stretch Database](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Wird zum Verwalten von Stretch-Datenbanken verwendet.|  
|[Temporale Tabellen gespeicherte Prozeduren](https://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Verwendung für temporale Tabellen|  
|[Gespeicherte XML-Prozeduren](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Werden für die XML-Textverwaltung verwendet.|  
  
> [!NOTE]  
>  Alle gespeicherten Systemprozeduren geben den Wert 0 für einen erfolgreichen Vorgang zurück, wenn nicht anders angegeben. Ein Wert ungleich 0 wird zurückgegeben, um einen Fehler anzuzeigen.  
  
## <a name="api-system-stored-procedures"></a>Gespeicherte API-Systemprozeduren  
 Benutzer, die [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] für ADO-, OLE DB- und ODBC-Anwendungen ausführen, werden möglicherweise feststellen, dass diese Anwendungen gespeicherte Systemprozeduren verwenden, die nicht in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenz behandelt werden. Diese gespeicherten Prozeduren werden vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Native Client-ODBC-Treiber verwendet, um die Funktionalität einer Datenbank-API zu implementieren. Diese gespeicherten Prozeduren sind lediglich der Mechanismus, mit dem der Anbieter oder Treiber Benutzeranforderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weitergeben. Sie sind ausschließlich für die interne Verwendung des Anbieters oder Treibers gedacht. Das explizite Aufrufen von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-basierten Anwendung wird nicht unterstützt.  
  
 Die gespeicherten Prozeduren sp_createorphan und sp_droporphans werden für die ODBC- **ntext**-, **Text**-und **Image** -Verarbeitung verwendet.  
  
 Die gespeicherte Prozedur sp_reset_connection wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Unterstützung von Aufrufen remote gespeicherter Prozeduren in Transaktionen verwendet. Durch diese gespeicherte Prozedur werden auch Audit Login- und Audit Logout-Ereignisse ausgelöst, wenn eine Verbindung in einem Verbindungspool wiederverwendet wird.  
  
 Die gespeicherten Systemprozeduren in den folgenden Tabellen werden nur innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über Client-APIs verwendet und sind nicht zur allgemeinen Verwendung durch die Benutzer gedacht. Sie können geändert werden, und ihre Kompatibilität wird nicht garantiert.  
  
 Die folgenden gespeicherten Prozeduren werden in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation beschrieben:  
  
|||  
|-|-|  
|sp_catalogs|sp_column_privileges|  
|sp_column_privileges_ex|sp_columns|  
|sp_columns_ex|sp_databases|  
|sp_cursor|sp_cursorclose|  
|sp_cursorexecute|sp_cursorfetch|  
|sp_cursoroption|sp_cursoropen|  
|sp_cursorprepare|sp_cursorprepexec|  
|sp_cursorunprepare|sp_execute|  
|sp_datatype_info|sp_fkeys|  
|sp_foreignkeys|sp_indexes|  
|sp_pkeys|sp_primarykeys|  
|sp_prepare|sp_prepexec|  
|sp_prepexecrpc|sp_unprepare|  
|sp_server_info|sp_special_columns|  
|sp_sproc_columns|sp_statistics|  
|sp_table_privileges|sp_table_privileges_ex|  
|sp_tables|sp_tables_ex|  
  
 Die folgenden gespeicherten Prozeduren sind nicht dokumentiert:  
  
|||  
|-|-|  
|sp_assemblies_rowset|sp_assemblies_rowset_rmt|  
|sp_assemblies_rowset2|sp_assembly_dependencies_rowset|  
|sp_assembly_dependencies_rowset_rmt|sp_assembly_dependencies_rowset2|  
|sp_bcp_dbcmptlevel|sp_catalogs_rowset|  
|sp_catalogs_rowset;2|sp_catalogs_rowset;5|  
|sp_catalogs_rowset_rmt|sp_catalogs_rowset2|  
|sp_check_constbytable_rowset|sp_check_constbytable_rowset;2|  
|sp_check_constbytable_rowset2|sp_check_constraints_rowset|  
|sp_check_constraints_rowset;2|sp_check_constraints_rowset2|  
|sp_column_privileges_rowset|sp_column_privileges_rowset;2|  
|sp_column_privileges_rowset;5|sp_column_privileges_rowset_rmt|  
|sp_column_privileges_rowset2|sp_columns_90|  
|sp_columns_90_rowset|sp_columns_90_rowset_rmt|  
|sp_columns_90_rowset2|sp_columns_ex_90|  
|sp_columns_rowset|sp_columns_rowset;2|  
|sp_columns_rowset;5|sp_columns_rowset_rmt|  
|sp_columns_rowset2|sp_constr_col_usage_rowset|  
|sp_datatype_info_90|sp_ddopen;1|  
|sp_ddopen;10|sp_ddopen;11|  
|sp_ddopen;12|sp_ddopen;13|  
|sp_ddopen;2|sp_ddopen;3|  
|sp_ddopen;4|sp_ddopen;5|  
|sp_ddopen;6|sp_ddopen;7|  
|sp_ddopen;8|sp_ddopen;9|  
|sp_foreign_keys_rowset|sp_foreign_keys_rowset;2|  
|sp_foreign_keys_rowset;3|sp_foreign_keys_rowset;5|  
|sp_foreign_keys_rowset_rmt|sp_foreign_keys_rowset2|  
|sp_foreign_keys_rowset3|sp_indexes_90_rowset|  
|sp_indexes_90_rowset_rmt|sp_indexes_90_rowset2|  
|sp_indexes_rowset|sp_indexes_rowset;2|  
|sp_indexes_rowset;5|sp_indexes_rowset_rmt|  
|sp_indexes_rowset2|sp_linkedservers_rowset|  
|sp_linkedservers_rowset;2|sp_linkedservers_rowset2|  
|sp_oledb_database|sp_oledb_defdb|  
|sp_oledb_deflang|sp_oledb_language|  
|sp_oledb_ro_usrname|sp_primary_keys_rowset|  
|sp_primary_keys_rowset;2|sp_primary_keys_rowset;3|  
|sp_primary_keys_rowset;5|sp_primary_keys_rowset_rmt|  
|sp_primary_keys_rowset2|sp_procedure_params_90_rowset|  
|sp_procedure_params_90_rowset2|sp_procedure_params_rowset|  
|sp_procedure_params_rowset;2|sp_procedure_params_rowset2|  
|sp_procedures_rowset|sp_procedures_rowset;2|  
|sp_procedures_rowset2|sp_provider_types_90_rowset|  
|sp_provider_types_rowset|sp_schemata_rowset|  
|sp_schemata_rowset;3|sp_special_columns_90|  
|sp_sproc_columns_90|sp_statistics_rowset|  
|sp_statistics_rowset;2|sp_statistics_rowset2|  
|sp_stored_procedures|sp_table_constraints_rowset|  
|sp_table_constraints_rowset;2|sp_table_constraints_rowset2|  
|sp_table_privileges_rowset|sp_table_privileges_rowset;2|  
|sp_table_privileges_rowset;5|sp_table_privileges_rowset_rmt|  
|sp_table_privileges_rowset2|sp_table_statistics_rowset|  
|sp_table_statistics_rowset;2|sp_table_statistics2_rowset|  
|sp_tablecollations|sp_tablecollations_90|  
|sp_tables_info_90_rowset|sp_tables_info_90_rowset_64|  
|sp_tables_info_90_rowset2|sp_tables_info_90_rowset2_64|  
|sp_tables_info_rowset|sp_tables_info_rowset;2|  
|sp_tables_info_rowset_64|sp_tables_info_rowset_64;2|  
|sp_tables_info_rowset2|sp_tables_info_rowset2_64|  
|sp_tables_rowset;2|sp_tables_rowset;5|  
|sp_tables_rowset_rmt|sp_tables_rowset2|  
|sp_usertypes_rowset|sp_usertypes_rowset_rmt|  
|sp_usertypes_rowset2|sp_views_rowset|  
|sp_views_rowset2|sp_xml_schema_rowset|  
|sp_xml_schema_rowset2||  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Gespeicherte Prozeduren &#40;Datenbank-Engine&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Ausführen gespeicherter Prozeduren &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Gespeicherte Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
