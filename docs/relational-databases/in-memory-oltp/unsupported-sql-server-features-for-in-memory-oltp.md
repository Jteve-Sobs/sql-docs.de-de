---
title: 'Nicht unterstützte Features: In-Memory-OLTP'
ms.custom: ''
ms.date: 05/29/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7427f7ccc70db68d1403cc1a92c7d7dafef82f5c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74412514"
---
# <a name="unsupported-sql-server-features-for-in-memory-oltp"></a>Nicht unterstützte SQL Server-Funktionen für In-Memory OLTP
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

In diesem Thema werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen erläutert, bei denen die Verwendung mit speicheroptimierten Objekten nicht unterstützt wird.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen, die für In-Memory-OLTP nicht unterstützt werden  

Die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen werden in einer Datenbank nicht unterstützt, die speicheroptimierte Objekte (einschließlich einer speicheroptimierten Dateigruppe) enthält.  

  
|Nicht unterstützte Funktion|Funktionsbeschreibung|  
|-------------------------|-------------------------|  
|Datenkomprimierung bei speicheroptimierten Tabellen|Sie können die Datenkomprimierungsfunktion verwenden, um die Komprimierung der Daten innerhalb einer Datenbank sowie die Reduzierung der Datenbankgröße zu vereinfachen. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|Partitionierung von speicheroptimierten Tabellen und HASH-Indizes sowie nicht gruppierten Indizes.|Die Daten partitionierter Tabellen und Indizes werden in Einheiten aufgeteilt, die über mehrere Dateigruppen in einer Datenbank verteilt sein können. Weitere Informationen finden Sie unter [partitionierte Tabellen und Indizes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).|  
| Replikation | Replikationskonfigurationen, die keine Transaktionsreplikation in speicheroptimierten Tabellen von Abonnenten darstellen, sind mit Tabellen oder Ansichten, die auf speicheroptimierte Tabellen verweisen, nicht kompatibel.<br /><br />Die Replikation mit sync_mode='database snapshot' wird bei Vorhandensein speicheroptimierter Dateigruppen nicht unterstützt.<br /><br />Weitere Informationen finden Sie unter [Replikation mit Abonnenten von speicheroptimierten Tabellen](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).|
|Spiegelung|Die Datenbankspiegelung wird für Datenbanken mit einer MEMORY_OPTIMIZED_DATA-Dateigruppe nicht unterstützt. Weitere Informationen zur Spiegelung finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|Protokollneuerstellung|Die Neuerstellung des Protokolls, entweder durch Anfügen oder mithilfe von ALTER DATABASE, wird für Datenbanken mit einer MEMORY_OPTIMIZED_DATA-Dateigruppe nicht unterstützt.|  
|Verknüpfter Server|Sie können auf verknüpfte Server nicht in der gleichen Abfrage oder Transaktion als speicheroptimierte Tabellen zugreifen. Weitere Informationen finden Sie unter [Verbindungsserver &#40;Datenbank-Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).|  
|Massenprotokollierung|Unabhängig vom Wiederherstellungsmodell der Datenbank werden alle Vorgänge in dauerhaften speicheroptimierten Tabellen immer vollständig protokolliert.|  
|Minimale Protokollierung|Die minimale Protokollierung wird für speicheroptimierte Tabellen nicht unterstützt. Weitere Informationen zur minimalen Protokollierung finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md) und [Voraussetzungen für die minimale Protokollierung beim Massenimport](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).|  
|Änderungsnachverfolgung|Die Änderungsnachverfolgung kann für eine Datenbank mit In-Memory-OLTP-Objekten nicht aktiviert werden. |
| DDL-Trigger | DDL-Trigger auf Datenbankebene und Serverebene werden sowohl bei speicherinternen OLTP-Tabellen als auch bei nativ kompilierten Modulen nicht unterstützt. |  
| Change Data Capture (CDC) | SQL Server 2017 CU15 und höher unterstützt die Aktivierung von CDC für eine Datenbank mit arbeitsspeicheroptimierten Tabellen. Dies gilt nur für die Datenbank und Tabellen auf dem Datenträger in der Datenbank. In früheren Versionen von SQL Server kann CDC nicht mit einer Datenbank mit speicheroptimierten Tabellen verwendet werden, da CDC intern einen DDL-Trigger für DROP TABLE verwendet. |  
| Fibermodus | Der Fibermodus wird für speicheroptimierte Tabellen nicht unterstützt:<br /><br />Wenn der Fibermodus aktiviert ist, können keine Datenbanken mit speicheroptimierten Dateigruppen erstellt oder speicheroptimierte Dateigruppen zu vorhandenen Datenbanken hinzugefügt werden.<br /><br />Sie können den Fibermodus aktivieren, wenn Datenbanken mit speicheroptimierten Dateigruppen vorhanden sind. Allerdings erfordert das Aktivieren des Fibermodus einen Serverneustart. In einem solchen Fall können Datenbanken mit speicheroptimierten Dateigruppen nicht wiederhergestellt werden. Dann wird eine Fehlermeldung angezeigt, die Ihnen empfiehlt, den Fibermodus zu deaktivieren, um Datenbanken mit speicheroptimierten Dateigruppen nutzen zu können.<br /><br />Das Anfügen und Wiederherstellen von Datenbanken mit speicheroptimierten Dateigruppen schlägt fehl, wenn der Fibermodus aktiviert ist. Die Datenbanken werden als fehlerverdächtig gekennzeichnet.<br /><br />Weitere Informationen finden Sie unter [Lightweightpooling (Serverkonfigurationsoption)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md). |  
|Service Broker-Einschränkung|Kann über eine systemintern kompilierte gespeicherte Prozedur nicht auf eine Warteschlange zugreifen.<br /><br /> Kann in einer Transaktion, die auf speicheroptimierte Tabellen zugreift, nicht auf eine Warteschlange in einer Remotedatenbank zugreifen.|  
|Replikation auf Abonnenten|Die Transaktionsreplikation in speicheroptimierte Tabellen von Abonnenten wird nur eingeschränkt unterstützt. Weitere Informationen finden Sie unter [Replikation mit Abonnenten von speicheroptimierten Tabellen](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).|  


#### <a name="cross-database-queries-and-transcations"></a>Datenbankübergreifende Abfragen und Transaktionen

Datenbankübergreifende Transaktionen werden bis auf einige Ausnahmen nicht unterstützt. In der folgenden Tabelle werden unterstützte Szenarien und entsprechende Einschränkungen beschrieben. (Siehe auch [Datenbankübergreifende Abfragen](../../relational-databases/in-memory-oltp/cross-database-queries.md).)  


|Datenbanken|Zulässig|BESCHREIBUNG|  
|---------------|-------------|-----------------|  
| Benutzerdatenbanken, **Modell**- und **msdb**-Datenbanken | Nein | In den meisten Fällen werden datenbankübergreifende Abfragen und Transaktionen *nicht* unterstützt.<br /><br />Ein Abfrage kann nicht auf andere Datenbanken zugreifen, wenn die Abfrage eine speicheroptimierte Tabelle oder eine nativ kompilierte gespeicherte Prozedur verwendet. Diese Einschränkung gilt für Transaktionen und Abfragen.<br /><br />Ausgenommen sind die Systemdatenbanken **tempdb** und **master**. Hier steht die **master**-Datenbank nur für den schreibgeschützten Zugriff zur Verfügung. |
| Datenbank **Resource**, **tempdb** | Ja | Bei einer Transaktion, die speicherinterne OLTP-Objekte betrifft, können die Systemdatenbanken **Resource** und **tempdb** ohne zusätzliche Einschränkungen verwendet werden.


## <a name="scenarios-not-supported"></a>Nicht unterstützte Szenarien  
  
- Zugreifen auf speicheroptimierte Tabellen mithilfe der Kontextverbindung aus CLR-gespeicherten Prozeduren.  
  
- Keysetgesteuerte und dynamische Cursor für Abfragen, die auf speicheroptimierte Tabellen zugreifen. Diese Cursor werden auf "static" und "read-only" heruntergestuft.  
  
- Das Verwenden von **MERGE INTO** _target_, wobei *target* eine speicheroptimierte Tabelle ist, wird nicht unterstützt.
    - **MERGE USING** _source_ wird für speicheroptimierte Tabellen unterstützt.  
  
- Der Datentyp ROWVERSION (TIMESTAMP) wird nicht unterstützt. Weitere Informationen finden Sie unter [FROM &#40;Transact-SQL &#41;](../../t-sql/queries/from-transact-sql.md).
  
- Automatisches Schließen wird für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.  
  
- Datenbankmomentaufnahmen werden für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.  
  
- Transaktions-DDL, wie z.B. CREATE/ALTER/DROP von speicherinternen OLTP-Objekten wird innerhalb von Benutzertransaktionen nicht unterstützt.  
  
- Ereignisbenachrichtigung  
  
- Richtlinienbasierte Verwaltung.
    - Der "Prevent"- und der "Log Only"-Modus der richtlinienbasierten Verwaltung werden nicht unterstützt. Das Vorhandensein solcher Richtlinien auf dem Server verhindert möglicherweise, dass In-Memory OLTP-DDL erfolgreich ausgeführt wird. Der "On Demand"- und der "On Schedule"-Modus werden unterstützt.  

- Datenbankkapselung ([Eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md)) wird bei In-Memory-OLTP nicht unterstützt.
    - Die Authentifizierung eigenständiger Datenbanken wird unterstützt. Allerdings werden alle speicherinternen OLTP-Objekte in den **dm_db_uncontained_entities** der dynamischen Verwaltungssicht als „breaking containment“ gekennzeichnet.

  
## <a name="see-also"></a>Weitere Informationen  

- [SQL Server-Unterstützung für In-Memory OLTP](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)
