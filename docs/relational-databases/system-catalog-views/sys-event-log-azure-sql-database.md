---
title: Sys. event_log (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/28/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- event_log
- sys.event_log_TSQL
- event_log_TSQL
- sys.event_log
dev_langs:
- TSQL
helpviewer_keywords:
- event_log
- sys.event_log
ms.assetid: ad5496b5-e5c7-4a18-b5a0-3f985d7c4758
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ced951c44680133ab1e1f96843269ce998edbf08
ms.sourcegitcommit: 97340deee7e17288b5eec2fa275b01128f28e1b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55421127"
---
# <a name="syseventlog-azure-sql-database"></a>sys.event_log (Azure SQL-Datenbank)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt erfolgreiche [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] -Verbindungen, Verbindungsfehler und Deadlocks. Sie können diese Informationen verwenden, um die Datenbankaktivität mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nachzuverfolgen oder um Fehler zu beheben.  
  
> [!CAUTION]  
> Für Installationen mit einer großen Anzahl von Datenbanken oder hohe Anzahl von Anmeldungen kann Aktivitäten in Sys. event_log dazu führen, dass Einschränkungen in Bezug auf Leistung, hohe CPU-Auslastung, und möglicherweise Anmeldefehler führen. Abfragen von Sys. event_log können für das Problem beitragen. Microsoft arbeitet daran, um dieses Problem zu beheben. In der Zwischenzeit um die Auswirkungen dieses Problem zu verringern, beschränken Sie Abfragen von Sys. event_log an. Sollten Benutzer die NewRelic SQL Server-Plug-Ins finden Sie unter [-Plug-in "Microsoft Azure SQL-Datenbank" die Anpassungen für Optimierung und Leistung](https://discuss.newrelic.com/t/microsoft-azure-sql-database-plugin-tuning-performance-tweaks/30729) Konfigurationsinformationen.  
  
 Die `sys.event_log`-Sicht enthält die folgenden Spalten.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Der Name der Datenbank. Wenn die Verbindung nicht hergestellt werden kann und der Benutzer keinen Datenbanknamen angegeben hat, ist diese Spalte leer.|  
|**start_time**|**datetime2**|UTC-Datum und -Zeit des Beginns des Aggregationsintervalls. Für aggregierte Ereignisse ist die Zeit immer ein Vielfaches von 5 Minuten. Zum Beispiel:<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|UTC-Datum und -Zeit des Endes des Aggregationsintervalls. Für aggregierte Ereignisse ist **End_time** liegt immer genau 5 Minuten später als die entsprechende **Start_time** in derselben Zeile. Für Ereignisse, die nicht aggregiert werden, **Start_time** und **End_time** gleich der tatsächlichen UTC-Datum und Uhrzeit des Ereignisses.|  
|**event_category**|**nvarchar(64)**|Die Komponente auf hoher Ebene, die dieses Ereignis generiert hat.<br /><br /> Finden Sie unter [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) eine Liste von möglichen Werten.|  
|**event_type**|**nvarchar(64)**|Der Typ des Ereignisses.<br /><br /> Finden Sie unter [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) eine Liste von möglichen Werten.|  
|**event_subtype**|**int**|Der Untertyp des eintretenden Ereignisses.<br /><br /> Finden Sie unter [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) eine Liste von möglichen Werten.|  
|**event_subtype_desc**|**nvarchar(64)**|Die Beschreibung des Ereignisuntertyps.<br /><br /> Finden Sie unter [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) eine Liste von möglichen Werten.|  
|**severity**|**int**|Der Schweregrad des Fehlers. Dabei sind folgende Werte möglich:<br /><br /> 0 = Information<br />1 = Warning<br />2 = Fehler|  
|**event_count**|**int**|Die Anzahl der Versuche, die dieses Ereignis aufgetreten ist für die angegebene Datenbank innerhalb des angegebenen Zeitintervalls (**Start_time** und **End_time**).|  
|**description**|**nvarchar(max)**|Detaillierte Beschreibung des Ereignisses.<br /><br /> Finden Sie unter [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) eine Liste von möglichen Werten.|  
|**additional_data**|**XML**|*Hinweis: Dieser Wert ist immer NULL für Azure SQL-Datenbank V12. Finden Sie unter [Beispiele](#Deadlock) im Abschnitt zum Abrufen von Deadlockereignisse für V12.*<br /><br /> Für **Deadlock** Ereignisse, diese Spalte enthält das deadlockdiagramm. Bei anderen Ereignistypen enthält diese Spalte NULL. |  
  
##  <a name="EventTypes"></a> Ereignistypen

 Die Ereignisse, die von jeder Zeile in dieser Sicht aufgezeichnet werden identifiziert, nach einer Kategorie (**Event_category**), Ereignistyp (**Event_type**), und einem Untertyp (**Event_subtype**). In der folgenden Tabelle werden die Ereignistypen aufgeführt, die in dieser Sicht gesammelt werden.  
  
 Für Ereignisse in der **Konnektivität** Kategorie zusammenfassende Informationen finden Sie in der Sys. database_connection_stats-Sicht.  
  
> [!NOTE]  
> Diese Sicht enthält nicht alle [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Datenbankereignisse, die eintreten können, sondern nur die hier aufgeführten. Zusätzliche Kategorien, Ereignistypen und Untertypen werden in zukünftigen Versionen von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ggf. hinzugefügt.  
  
|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**description**|  
|-------------------------|---------------------|------------------------|------------------------------|------------------|---------------------|  
|**connectivity**|**connection_successful**|0|**connection_successful**|0|Die Verbindung mit der Datenbank war erfolgreich.|  
|**connectivity**|**connection_failed**|0|**invalid_login_name**|2|Der Anmeldename ist in dieser SQL Server-Version nicht gültig.|  
|**connectivity**|**connection_failed**|1|**windows_auth_not_supported**|2|Windows-Anmeldungen werden in dieser SQL Server-Version nicht unterstützt.|  
|**connectivity**|**connection_failed**|2|**attach_db_not_supported**|2|Der Benutzer hat das Anfügen einer Datenbankdatei angefordert, die nicht unterstützt wird.|  
|**connectivity**|**connection_failed**|3|**change_password_not_supported**|2|Der Benutzer hat angefordert, das Kennwort des angemeldeten Benutzers zu ändern. Dies wird nicht unterstützt.|  
|**connectivity**|**connection_failed**|4|**login_failed_for_user**|2|Fehler bei der Anmeldung für den Benutzer.|  
|**connectivity**|**connection_failed**|5|**login_disabled**|2|Die Anmeldung wurde deaktiviert.|  
|**connectivity**|**connection_failed**|6|**failed_to_open_db**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Datenbank konnte nicht geöffnet werden. Die Ursache hierfür kann darin liegen, dass die Datenbank nicht vorhanden ist oder keine Authentifizierung zum Öffnen der Datenbank vorhanden ist.|  
|**connectivity**|**connection_failed**|7|**blocked_by_firewall**|2|Client-IP-Adresse ist nicht berechtigt, auf den Server zuzugreifen.|  
|**connectivity**|**connection_failed**|8|**client_close**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Möglicher Timeout beim Client, als die Verbindung hergestellt wurde. Versuchen Sie, das Verbindungstimeout zu erhöhen.|  
|**connectivity**|**connection_failed**|9|**reconfiguration**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Verbindungsfehler, da die Datenbank zu diesem Zeitpunkt eine Neukonfiguration durchlaufen hat.|  
|**connectivity**|**connection_terminated**|0|**idle_connection_timeout**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Verbindung ist länger im Leerlauf, als der vom System definierte Schwellenwert angibt.|  
|**connectivity**|**connection_terminated**|1|**reconfiguration**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wurde aufgrund einer Neukonfiguration der Datenbank beendet.|  
|**connectivity**|**throttling**|*\<Ursachencode: >*|**reason_code**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Anforderung wird gedrosselt.  Ursachencode für Drosselung:  *\<Ursachencode >*. Weitere Informationen finden Sie unter [Moduleinschränkung](https://msdn.microsoft.com/library/windowsazure/dn338079.aspx).|  
|**connectivity**|**throttling_long_transaction**|40549|**long_transaction**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wird aufgrund einer Transaktion mit langer Laufzeit beendet. Verkürzen Sie die Transaktion. Weitere Informationen finden Sie unter [Ressourceneinschränkungen](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**connectivity**|**throttling_long_transaction**|40550|**excessive_lock_usage**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wurde beendet, da zu viele Sperren abgerufen wurden. Reduzieren Sie die Anzahl der in einer einzelnen Transaktion gelesenen oder geänderten Zeilen. Weitere Informationen finden Sie unter [Ressourceneinschränkungen](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**connectivity**|**throttling_long_transaction**|40551|**excessive_tempdb_usage**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wurde aufgrund übermäßiger TEMPDB-Auslastung beendet. Ändern Sie die Abfrage, um die Verwendung des temporären Tabellenbereichs zu verringern. Weitere Informationen finden Sie unter [Ressourceneinschränkungen](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**connectivity**|**throttling_long_transaction**|40552|**excessive_log_space_usage**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wurde aufgrund übermäßiger Verwendung des Speicherplatzes für das Transaktionsprotokoll beendet. Reduzieren Sie die Anzahl der in einer einzelnen Transaktion geänderten Zeilen. Weitere Informationen finden Sie unter [Ressourceneinschränkungen](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**connectivity**|**throttling_long_transaction**|40553|**excessive_memory_usage**|2|*Hinweis: Gilt nur für Azure SQL-Datenbank V11.*<br /><br /> Die Sitzung wurde aufgrund übermäßiger Speicherauslastung beendet. Ändern Sie die Abfrage, damit weniger Zeilen verarbeitet werden. Weitere Informationen finden Sie unter [Ressourceneinschränkungen](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**engine**|**deadlock**|0|**deadlock**|2|Deadlock ist aufgetreten.|  
  
## <a name="permissions"></a>Berechtigungen

 Benutzer mit Berechtigung zum Zugriff auf die **master** Datenbank haben schreibgeschützten Zugriff auf diese Sicht.  
  
## <a name="remarks"></a>Hinweise  
  
### <a name="event-aggregation"></a>Ereignisaggregation

 Die Ereignisinformationen für diese Sicht werden gesammelt und innerhalb von 5-minütigen Intervallen aggregiert. Die **Event_count** Spalte darstellt, wie oft ein bestimmter **Event_type** und **Event_subtype** für eine bestimmte Datenbank innerhalb eines angegebenen Zeitintervalls aufgetreten.  
  
> [!NOTE]  
> Einige Ereignisse wie Deadlocks werden nicht aggregiert. Für diese Ereignisse ist **Event_count** 1 und **Start_time** und **End_time** ist gleich der tatsächlichen UTC-Datum und Uhrzeit, wann das Ereignis aufgetreten ist.  
  
 Wenn ein Benutzer zum Beispiel aufgrund eines ungültigen Anmeldenamens sieben Mal zwischen 11:00 und 11:05 Uhr am 05.02.2012 (UTC) keine Verbindung mit der Datenbank Database1 herstellen kann, sind diese Informationen in dieser Sicht in einer einzelnen Zeile verfügbar:  
  
|**database_name**|**start_time**|**end_time**|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**event_count**|**description**|**additional_data**|  
|------------------------|---------------------|-------------------|-------------------------|---------------------|------------------------|------------------------------|------------------|----------------------|---------------------|--------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`connectivity`|`connection_failed`|`4`|`login_failed_for_user`|`2`|`7`|`Login failed for user.`|`NULL`|  
  
### <a name="interval-starttime-and-endtime"></a>start_time und end_time des Intervalls  
 Ein Ereignis wird in ein aggregationsintervall eingefügt, wenn das Ereignis tritt auf, *auf* oder _nach_**Start_time** und _vor_  **End_time** für dieses Intervall. Beispielsweise würde ein Ereignis, das genau zum Zeitpunkt `2012-10-30 19:25:00.0000000` eintritt, nur im zweiten unten gezeigten Intervall aufgenommen werden:  
  
```
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```

### <a name="data-updates"></a>Datenupdates

 Die Daten in dieser Sicht werden im Zeitverlauf gesammelt. Normalerweise werden die Daten innerhalb einer Stunde nach Beginn des Aggregationsintervalls gesammelt, es kann aber maximal 24 Stunden dauern, bis alle Daten in der Sicht angezeigt werden. Während dieser Zeit werden die Informationen in einer einzelnen Zeile möglicherweise gelegentlich aktualisiert.  
  
### <a name="data-retention"></a>Datenbeibehaltung

 Die Daten in dieser Ansicht werden beibehalten, für bis zu 30 Tage oder kürzer abhängig von der Anzahl der Datenbanken und die Anzahl der eindeutigen Ereignisse, die jede Datenbank generiert. Um diese Informationen für einen längeren Zeitraum beizubehalten, kopieren Sie die Daten in eine separate Datenbank. Nachdem Sie eine erste Kopie der Sicht erstellt haben, werden die Zeilen in der Sicht möglicherweise aktualisiert, während die Daten gesammelt werden. Damit die Kopie der Daten aktuell bleibt, führen Sie regelmäßig einen Tabellenscan der Zeilen aus, um nach einer Erhöhung der Ereignisanzahl für vorhandene Zeilen zu suchen und um neue Zeilen zu ermitteln (eindeutige Zeilen bestimmen Sie anhand der Start- und Endzeiten). Aktualisieren Sie dann die Kopie der Daten mit diesen Änderungen.  
  
### <a name="errors-not-included"></a>Fehler nicht enthalten

 Diese Sicht enthält möglicherweise nicht alle Verbindungs- und Fehlerinformationen:  
  
- In dieser Ansicht enthält nicht alle [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Fehler, die auftreten können, sondern nur die Datenbank [Ereignistypen](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) in diesem Thema.  
- Es ist ein Computerfehler innerhalb der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Datacenter, ist eine kleine Menge Daten möglicherweise in der Ereignistabelle fehlt.  
- Wenn eine IP-Adresse von DoSGuard blockiert wurde, können Verbindungsversuchsereignisse von dieser IP-Adresse nicht gesammelt werden. Diese werden in dieser Sicht nicht angezeigt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="simple-examples"></a>Einfache Beispiele

 Die folgende Abfrage gibt alle Ereignisse zurück, die zwischen 12 Uhr mittags am 25.09.2011 und 12 Uhr mittags am 28.09.2011 (UTC) eingetreten sind. Standardmäßig werden die Abfrageergebnisse nach sortiert **Start_time** (aufsteigende Reihenfolge).  

```sql
SELECT * FROM sys.event_log
WHERE start_time >= '2011-09-25 12:00:00'
    AND end_time <= '2011-09-28 12:00:00';  
```

Die folgende Abfrage gibt alle Deadlockereignisse für die Datenbank "database1" (gilt nur für Azure SQL-Datenbank V11).  

```sql
SELECT * FROM sys.event_log
WHERE event_type = 'deadlock'
    AND database_name = 'Database1';  
```

<a name="Deadlock"></a> Die folgende Abfrage gibt alle Deadlockereignisse für die Datenbank "database1" (gilt nur für Azure SQL-Datenbank V12).  

```sql
WITH CTE AS (  
       SELECT CAST(event_data AS XML)  AS [target_data_XML]  
   FROM sys.fn_xe_telemetry_blob_target_read_file('dl', null, null, null)  
)  
SELECT target_data_XML.value('(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
target_data_XML.query('/event/data[@name=''xml_report'']/value/deadlock') AS deadlock_xml,  
target_data_XML.query('/event/data[@name=''database_name'']/value').value('(/value)[1]', 'nvarchar(100)') AS db_name  
FROM CTE  
```

Die folgende Abfrage gibt harte Drosselungen für SQL-Arbeitsthreadereignisse zurück, die zwischen 10:00 und 11:00 Uhr am 25.09.2011 (UTC) eingetreten sind.  

```sql
SELECT * FROM sys.event_log
WHERE event_type = 'throttling'
    AND event_subtype = 4194307
    AND start_time >= '2011-09-25 10:00:00'
    AND end_time <= '2011-09-25 11:00:00';  
```

### <a name="db-scoped-extended-event"></a>DB-Gültigkeitsbereich erweiterte Ereignisse

 Verwenden Sie im folgenden Beispielcode, um die Db-Gültigkeitsbereich erweiterte Ereignisse (XEvent)-Sitzung festzulegen:  

```sql
IF EXISTS  
    (SELECT * from sys.database_event_sessions  
        WHERE name = 'azure_monitor_deadlock_session')  
BEGIN  
    ALTER EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE  
        DROP TARGET package0.ring_buffer;  
  
    DROP EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE;  
END  
  
CREATE EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    ADD EVENT sqlserver.database_xml_deadlock_report  
    ADD TARGET package0.ring_buffer  
    (  
        SET max_memory = 2048, max_events_limit = 10  
    )  
    WITH (STARTUP_STATE = ON,  
          EVENT_RETENTION_MODE = ALLOW_SINGLE_EVENT_LOSS);  
  
ALTER EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    STATE = START;  
```

### <a name="check-for-deadlock"></a>Kontrollkästchen für Deadlocks

Verwenden Sie die folgende Abfrage um zu überprüfen, ob ein Deadlock vorhanden ist.  

```sql
WITH CTE AS (  
    SELECT CAST(xet.target_data AS XML)  AS [target_data_XML]  
        FROM            sys.dm_xe_database_session_targets AS xet  
             INNER JOIN sys.dm_xe_database_sessions        AS xe  
                 ON (xe.address = xet.event_session_address)  
        WHERE xe.name = 'azure_monitor_deadlock_session'  
)  
, CTE2 AS (  
    SELECT  
            T2.EventData.query('.').value(  
                '(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
            T2.EventData.query('.').query(  
                '(/event/data/value/deadlock)[1]')     AS deadlock_xml  
        FROM CTE  
            CROSS Apply [target_data_XML].nodes(  
                '/RingBufferTarget/event') AS T2(EventData)  
)  
SELECT * FROM CTE2;  
```

## <a name="see-also"></a>Siehe auch

 [Erweiterte Ereignisse in Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
 