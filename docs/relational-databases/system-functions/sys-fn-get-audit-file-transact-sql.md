---
title: sys.fn_get_audit_file (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_audit_file_TSQL
- sys.fn_get_audit_file_TSQL
- fn_get_audit_file
- sys.fn_get_audit_file
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_get_audit_file function
- fn_get_audit_file function
ms.assetid: d6a78d14-bb1f-4987-b7b6-579ddd4167f5
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 571ed8140e408577626c437d38080ccabb6c241f
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852955"
---
# <a name="sysfngetauditfile-transact-sql"></a>sys.fn_get_audit_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen von einer Überwachungsdatei zurück, die von einer Serverüberwachung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurde. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
fn_get_audit_file ( file_pattern,   
    { default | initial_file_name | NULL },   
    { default | audit_record_offset | NULL } )  
```  
  
## <a name="arguments"></a>Argumente  
 *file_pattern*  
 Gibt das Verzeichnis oder den Pfad und den Dateinamen für den zu lesenden Überwachungsdateisatz an. Der Typ ist **nvarchar(260)**. 
 
 - **SQL Server**:
    
    Dieses Argument muss sowohl einen Pfad (Laufwerksbuchstabe oder Netzwerkfreigabe) als auch einen Dateinamen umfassen. Diese können ein Platzhalterzeichen enthalten. Ein einzelnes Sternchen (*) kann verwendet werden, mehrere Dateien von einem überwachungsdateisatz gesammelt werden. Zum Beispiel:  
  
    -   **\<Pfad >\\ \***  – sammelt alle Überwachungsdateien am angegebenen Speicherort.  
  
    -   **\<Pfad > \LoginsAudit_{GUID}** – sammelt alle Überwachungsdateien, die dem angegebenen Namen und GUID-Paar aufweisen.  
  
    -   **\<path>\LoginsAudit_{GUID}_00_29384.sqlaudit** - Collect a specific audit file.  
  
 - **Azure SQL-Datenbank**:
 
    Dieses Argument wird verwendet, eine Blob-URL (einschließlich der Storage-Endpunkt und Container) an. Während sie einen Sternchen-Platzhalter nicht unterstützt, können Sie einen partielle Datei (Blob)-Namenspräfix (anstelle der vollständigen Blob-Name) verwenden, um mehrere Dateien (Blobs) zu sammeln, die mit diesem Präfix beginnen. Zum Beispiel:
 
      - **\<Storage_endpoint\>/\<Container\>/\<ServerName\>/\<DatabaseName\> /**  – sammelt alle Überwachungsdateien (Blobs) für die jeweilige Datenbank.    
      
      - **\<Storage_endpoint\>/\<Container\>/\<ServerName\>/\<DatabaseName\> / \< AuditName\>/\<CreationDate\>/\<FileName\>xel** – sammelt eine bestimmte Überwachungsdatei (Blob).
  
> [!NOTE]  
>  Einen Pfad ohne ein Dateinamenmuster zu übergeben generiert einen Fehler.  
  
 *initial_file_name*  
 Gibt den Pfad und den Namen einer bestimmten Datei im Überwachungsdateisatz an, von der an die Überwachungsdatensätze gelesen werden sollen. Der Typ ist **nvarchar(260)**.  
  
> [!NOTE]  
>  Die *' initial_file_name '* -Argument muss gültige Einträge enthalten, oder muss entweder die standardmäßige enthalten | NULL-Wert.  
  
 *audit_record_offset*  
 Gibt einen bekannten Speicherort mit der für initial_file_name angegebenen Datei an. Wenn dieses Argument verwendet wird, beginnt die Funktion mit dem Lesen beim ersten Datensatz des Puffers, der direkt nach dem festgelegten Offset folgt.  
  
> [!NOTE]  
>  Die *' audit_record_offset ' stellen* -Argument muss gültige Einträge enthalten, oder muss entweder die standardmäßige enthalten | NULL-Wert. Der Typ ist **Bigint**.  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 In der folgenden Tabelle wird der Inhalt der Überwachungsdatei beschrieben, die von dieser Funktion zurückgegeben werden kann.  
  
| Spaltenname | Typ | Description |  
|-------------|------|-------------|  
| action_id | **varchar(4)** | ID der Aktion. Lässt keine NULL-Werte zu. |  
| additional_information | **nvarchar(4000)** | Eindeutige Informationen, die nur für ein einzelnes Ereignis gelten, werden als XML zurückgegeben. Eine kleine Anzahl überwachbarer Aktionen enthält diese Art von Informationen.<br /><br /> Eine Ebene des TSQL-Stapels wird im XML-Format für Aktionen angezeigt, denen ein TSQL-Stapel zugeordnet ist. Das XML-Format sieht folgendermaßen aus:<br /><br /> `<tsql_stack><frame nest_level = '%u' database_name = '%.*s' schema_name = '%.*s' object_name = '%.*s' /></tsql_stack>`<br /><br /> Frame nest_level gibt die aktuelle Schachtelungsebene des Frames an. Der Modulname (database_name, schema_name und object_name) wird in einem aus drei Teilen bestehenden Format dargestellt.  Der Modulname wird analysiert, wie ungültige XML-Escapezeichen `'\<'`, `'>'`, `'/'`, `'_x'`. Werden sie als mit Escapezeichen versehen werden `_xHHHH\_`. HHHH steht für den vierstelligen hexadezimalen UCS 2-Code für das Zeichen<br /><br /> Lässt NULL-Werte zu. Gibt NULL zurück, wenn keine zusätzlichen vom Ereignis gemeldeten Informationen vorliegen. |
| affected_rows | **bigint** | **Gilt für**: Azure SQL-Datenbank<br /><br /> Die Anzahl der von der ausgeführten Anweisung betroffenen Zeilen. |  
| application_name | **nvarchar(128)** | **Gilt für**: Azure SQL-Datenbank und SQL Server (ab 2017)<br /><br /> Name der Clientanwendung, die die Anweisung ausgeführt, die das Überwachungsereignis ausgelöst hat. |  
| audit_file_offset | **bigint** | **Gilt für**: Nur SQLServer<br /><br /> Der Pufferoffset in der Datei, die den Überwachungsdatensatz enthält. Lässt keine NULL-Werte zu. |  
| audit_schema_version | **int** | Immer 1 |  
| class_type | **varchar(2)** | Der Typ der überwachbaren Entität, bei der die Überwachung auftritt. Lässt keine NULL-Werte zu. |  
| client_ip | **nvarchar(128)** | **Gilt für**: Azure SQL-Datenbank und SQL Server (ab 2017)<br /><br />    Quell-IP von der Clientanwendung |  
| connection_id | GUID | **Gilt für**: Azure SQL-Datenbank und die verwaltete Instanz<br /><br /> ID der Verbindung auf dem server |
| data_sensitivity_information | nvarchar(4000) | **Gilt für**: Azure SQL-Datenbank<br /><br /> Informationstypen und die vertraulichkeitsbezeichnungen, die von der überwachten Abfrage basierend auf den klassifizierten Spalten in der Datenbank zurückgegeben. Erfahren Sie mehr über [Azure SQL-Datenbank, die Daten zu ermitteln und Klassifizierung](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification) |
| database_name | **sysname** | Der Datenbankkontext, in dem die Aktion aufgetreten ist. Lässt NULL-Werte zu. Gibt NULL zurück, für die Überwachungen auf Serverebene ausgeführt wird. |  
| database_principal_id | **int** |ID des Datenbankbenutzerkontexts, in dem die Aktion ausgeführt wird. Lässt keine NULL-Werte zu. Wenn dies nicht anwendbar ist, wird 0 zurückgegeben. Zum Beispiel bei einem Servervorgang.|
| database_principal_name | **sysname** | Aktueller Benutzer. Lässt NULL-Werte zu. Gibt NULL zurück, wenn nicht verfügbar. |  
| duration_milliseconds | **bigint** | **Gilt für**: Azure SQL-Datenbank und die verwaltete Instanz<br /><br /> Abfrageausführungsdauer in Millisekunden |
| event_time | **datetime2** | Datum und Uhrzeit, wann die überwachbare Aktion ausgelöst wird. Lässt keine NULL-Werte zu. |  
| file_name | **varchar(260)** | Der Pfad und der Name der Überwachungsprotokolldatei, aus der der Datensatz stammt. Lässt keine NULL-Werte zu. |
| is_column_permission | **bit** | Flag, das angibt, ob dies eine Berechtigung auf Spaltenebene ist. Lässt keine NULL-Werte zu. Gibt 0 zurück wenn permission_bitmask = 0.<br /> 1 = TRUE<br /> 0 = False |
| object_id | **int** | Die ID der Entität, bei der die Überwachung aufgetreten ist. Dazu gehören:<br /> Server-Objekte<br /> Datenbanken<br /> Datenbankobjekte<br /> Schemaobjekte<br /> Lässt keine NULL-Werte zu. Gibt 0 zurück, wenn die Entität der Server selbst ist oder die Überwachung nicht auf Objektebene durchgeführt wird. Zum Beispiel bei der Authentifizierung. |  
| object_name | **sysname** | Der Name der Entität, bei der die Überwachung aufgetreten ist. Dazu gehören:<br /> Server-Objekte<br /> Datenbanken<br /> Datenbankobjekte<br /> Schemaobjekte<br /> Lässt NULL-Werte zu. Gibt NULL zurück, wenn die Entität der Server selbst ist oder die Überwachung nicht auf Objektebene durchgeführt wird. Zum Beispiel bei der Authentifizierung. |
| permission_bitmask | **varbinary(16)** | In einigen Aktionen sind dies die Berechtigungen, die gewährt, verweigert oder widerrufen wurden. |
| response_rows | **bigint** | **Gilt für**: Azure SQL-Datenbank und die verwaltete Instanz<br /><br /> Anzahl der Zeilen im Resultset zurückgegeben. |  
| schema_name | **sysname** | Der Schemakontext, in dem die Aktion aufgetreten ist. Lässt NULL-Werte zu. Gibt NULL für Überwachungen, die außerhalb eines Schemas auftreten. |  
| sequence_group_id | **varbinary** | **Gilt für**: Nur SQL Server (ab 2016)<br /><br />  Eindeutiger Bezeichner |  
| sequence_number | **int** | Hält die Reihenfolge der Datensätze innerhalb eines einzelnen Überwachungsdatensatzes fest, der zu groß für den Schreibpuffer für Überwachungen ist. Lässt keine NULL-Werte zu. |  
| server_instance_name | **sysname** | Der Name der Serverinstanz, in der die Überwachung aufgetreten ist. Das Standardformat Server\Instanz wird verwendet. |  
| server_principal_id | **int** | ID des Anmeldekontexts, in dem die Aktion ausgeführt wird. Lässt keine NULL-Werte zu. |  
| server_principal_name | **sysname** | Aktuelle Anmeldung. Lässt NULL-Werte zu. |  
| server_principal_sid | **varbinary** | Aktuelle Anmeldungs-SID. Lässt NULL-Werte zu. |  
| session_id | **smallint** | Die ID der Sitzung, in der das Ereignis aufgetreten ist. Lässt keine NULL-Werte zu. |  
| session_server_principal_name | **sysname** | Der Serverprinzipal für die Sitzung. Lässt NULL-Werte zu. |  
| statement | **nvarchar(4000)** | TSQL-Anweisung, falls vorhanden. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| succeeded | **bit** | Gibt an, ob die Aktion, die das Ereignis ausgelöst wurde erfolgreich erstellt wurde. Lässt keine NULL-Werte zu. Für alle Ereignisse außer Anmeldeereignisse meldet dies nur, ob die Berechtigungsüberprüfung erfolgreich war oder fehlgeschlagen ist, nicht der Vorgang.<br /> 1 = Erfolg<br /> 0 = Fehler |
| target_database_principal_id | **int** | Der Datenbankprinzipal, auf dem der GRANT/DENY/REVOKE-Vorgang ausgeführt wird. Lässt keine NULL-Werte zu. Falls nicht zutreffend, wird 0 zurückgegeben. |  
| target_database_principal_name | **sysname** | Der Zielbenutzer der Aktion. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| target_server_principal_id | **int** | Serverprinzipal, auf dem der GRANT/DENY/REVOKE-Vorgang ausgeführt wird. Lässt keine NULL-Werte zu. Falls nicht zutreffend, wird 0 zurückgegeben. |  
| target_server_principal_name | **sysname** | Zielanmeldung der Aktion. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| target_server_principal_sid | **varbinary** | SID der zielanmeldung. Lässt NULL-Werte zu. Falls nicht zutreffend, wird NULL zurückgegeben. |  
| transaction_id | **bigint** | **Gilt für**: Nur SQL Server (ab 2016)<br /><br /> Eindeutiger Bezeichner zur Identifizierung in einer Transaktion mehrere Überwachungsereignisse zu |  
| user_defined_event_id | **smallint** | **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Azure SQL-Datenbank und die verwaltete Instanz<br /><br /> Benutzerdefinierte Ereignis-Id als Argument übergebenen **Sp_audit_write**. **NULL** für Systemereignisse (Standard) und ungleich 0 für ein benutzerdefiniertes Ereignis. Weitere Informationen finden Sie unter [Sp_audit_write &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md). |  
| user_defined_information | **nvarchar(4000)** | **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Azure SQL-Datenbank und die verwaltete Instanz<br /><br /> Verwendet, um zusätzliche Informationen zu erfassen, der Benutzer im Überwachungsprotokoll aufzeichnen möchte, die **Sp_audit_write** gespeicherte Prozedur. |  

  
## <a name="remarks"></a>Hinweise  
 Wenn die *File_pattern* Argument übergeben wird, um **Fn_get_audit_file** verweist auf einen Pfad oder die Datei, die nicht vorhanden ist, oder wenn die Datei nicht um eine Überwachungsdatei ist die **MSG_INVALID_AUDIT_FILE**Fehlermeldung wird zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen

- **SQL Server**: Erfordert die **CONTROL SERVER** -Berechtigung.  
- **Azure SQL DB**: Erfordert die **CONTROL DATABASE** Berechtigung.     
  - Server-Administratoren können die Überwachungsprotokolle aller Datenbanken auf dem Server zugreifen.
  - Nicht-Server-Administratoren können die Überwachungsprotokolle nur aus der aktuellen Datenbank zugreifen.
  - BLOBs, die die oben genannten Kriterien nicht erfüllen übersprungen werden (eine Liste der übersprungenen Blobs werden in der Ausgabenachricht der Abfrage angezeigt werden), und die Funktion zurück Protokolle nur aus Blobs, die für die der Zugriff ist zulässig.  
  
## <a name="examples"></a>Beispiele

- **SQL Server**

  Dieses Beispiel liest aus einer Datei namens `\\serverName\Audit\HIPAA_AUDIT.sqlaudit`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('\\serverName\Audit\HIPAA_AUDIT.sqlaudit',default,default);  
  GO  
  ```  

- **Azure SQL-Datenbank**

  Dieses Beispiel liest aus einer Datei mit dem Namen `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`:  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Dieses Beispiel liest aus derselben Datei wie oben, jedoch mit zusätzlichen T-SQL-Klauseln (**oben**, **ORDER BY**, und **, in denen** Klausel zum Filtern die Überwachungsdatensätze, die zurückgegeben werden, indem Sie die (Funktion):
  
  ```  
  SELECT TOP 10 * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default)
  WHERE server_principal_name = 'admin1'
  ORDER BY event_time
  GO
  ```  

  Dieses Beispiel liest alle Überwachungsprotokolle von Servern, die mit beginnen `Sh`: 
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```

Ein vollständiges Beispiel für das Erstellen einer Überwachung finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).

Informationen zum Einrichten der Überwachung von Azure SQL-Datenbank finden Sie unter [erste Schritte mit SQL-datenbanküberwachung](https://docs.microsoft.com/azure/sql-database/sql-database-auditing).
  
## <a name="see-also"></a>Siehe auch  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
