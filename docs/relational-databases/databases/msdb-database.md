---
title: msdb-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, msdb database
- alerts [SQL Server], msdb database
- jobs [SQL Server], msdb database
- msdb database [SQL Server]
ms.assetid: 5032cb2d-65a0-40dd-b569-4dcecdd58ceb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ecbe9589a1219920847adf9af9aa99c24672d94d
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560187"
---
# <a name="msdb-database"></a>msdb-Datenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Die **msdb** -Datenbank wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Planen von Warnungen und Aufträgen sowie von weiteren Funktionen (z. B. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSB](../../includes/sssb-md.md)] und Datenbank-E-Mail) verwendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird beispielsweise in der **msdb**-Datenbank automatisch ein vollständiger Onlinesicherungs- und Wiederherstellungsverlauf in Tabellen verwaltet. Diese Informationen umfassen den Namen der Person, die die Sicherung ausgeführt hat, den Zeitpunkt der Sicherung und die Angabe, auf welchen Medien bzw. in welchen Dateien die Sicherung gespeichert wurde. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet diese Informationen, um einen Plan für das Wiederherstellen einer Datenbank und das Anwenden vorhandener Transaktionsprotokollsicherungen vorzuschlagen. Sicherungsvorgänge für alle Datenbanken werden auch dann aufgezeichnet, wenn sie mit benutzerdefinierten Anwendungen oder Tools von Drittanbietern erstellt wurden. Wenn Sie beispielsweise eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Anwendung verwenden, die zum Ausführen von Sicherungsvorgängen SMO-Objekte (SQL Server Management Objects) aufruft, wird das Ereignis in den **msdb** -Systemtabellen, im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll sowie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll protokolliert. Um die in der **msdb**-Datenbank gespeicherten Informationen zu schützen, empfiehlt es sich, das **msdb** -Transaktionsprotokoll auf einem fehlertoleranten Datenträger zu speichern.  
  
 Standardmäßig verwendet **msdb** das einfache Wiederherstellungsmodell. Wenn Sie die Tabellen mit dem [Sicherungs- und Wiederherstellungsverlauf](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md) verwenden, empfiehlt es sich, das vollständige Wiederherstellungsmodell für **msdb**zu verwenden. Weitere Informationen finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md). Beachten Sie Folgendes: Ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert oder aktualisiert oder wird **Setup.exe** zum Neuerstellen der Systemdatenbanken verwendet, wird das Wiederherstellungsmodell von msdb automatisch auf simple festgelegt.  
  
> [!IMPORTANT]  
>  Nach einem Vorgang, durch den **msdb**aktualisiert wird (beispielsweise nach dem Sichern oder Wiederherstellen von Datenbanken), empfiehlt es sich, eine Sicherung von **msdb**auszuführen. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="physical-properties-of-msdb"></a>Physische Eigenschaften der msdb-Datenbank  
 Die folgende Tabelle zeigt die Anfangskonfigurationswerte der **msdb** -Daten und -Protokolldateien. Die Größe dieser Dateien kann sich in den verschiedenen Editionen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]geringfügig unterscheiden.  
  
|File|Logischer Name (logical name)|Physischer Name (physical name)|Dateivergrößerung (file growth)|  
|----------|------------------|-------------------|-----------------|  
|Primäre Daten|MSDBData|MSDBData.mdf|Automatische Vergrößerung um 10 Prozent, bis der Speicherplatz auf dem Datenträger erschöpft ist.|  
|Log|MSDBLog|MSDBLog.ldf|Automatische Vergrößerung um 10 %, bis der Maximalwert von 2 TB erreicht wird.|  
  
 Informationen zum Verschieben der **msdb** -Datenbank oder -Protokolldateien finden Sie unter [Verschieben von Systemdatenbanken](../../relational-databases/databases/move-system-databases.md).  
  
### <a name="database-options"></a>Datenbankoptionen  
 Die folgende Tabelle zeigt den Standardwert jeder Datenbankoption in der **msdb** -Datenbank und gibt an, ob die Option geändert werden kann. Zum Anzeigen der aktuellen Einstellungen dieser Optionen verwenden Sie die Katalogsicht [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
|Datenbankoption|Standardwert|Kann geändert werden.|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|nein|  
|ANSI_NULL_DEFAULT|OFF|Benutzerkontensteuerung|  
|ANSI_NULLS|OFF|Benutzerkontensteuerung|  
|ANSI_PADDING|OFF|Benutzerkontensteuerung|  
|ANSI_WARNINGS|OFF|Benutzerkontensteuerung|  
|ARITHABORT|OFF|Benutzerkontensteuerung|  
|AUTO_CLOSE|OFF|Benutzerkontensteuerung|  
|AUTO_CREATE_STATISTICS|ON|Benutzerkontensteuerung|  
|AUTO_SHRINK|OFF|Benutzerkontensteuerung|  
|AUTO_UPDATE_STATISTICS|ON|Benutzerkontensteuerung|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Benutzerkontensteuerung|  
|CHANGE_TRACKING|OFF|nein|  
|CONCAT_NULL_YIELDS_NULL|OFF|Benutzerkontensteuerung|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Benutzerkontensteuerung|  
|CURSOR_DEFAULT|GLOBAL|Benutzerkontensteuerung|  
|Datenbankverfügbarkeitsoptionen|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|nein<br /><br /> Benutzerkontensteuerung<br /><br /> Benutzerkontensteuerung|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Benutzerkontensteuerung|  
|DB_CHAINING|ON|Benutzerkontensteuerung|  
|ENCRYPTION|OFF|nein|  
|MIXED_PAGE_ALLOCATION|ON|nein|  
|NUMERIC_ROUNDABORT|OFF|Benutzerkontensteuerung|  
|PAGE_VERIFY|CHECKSUM|Benutzerkontensteuerung|  
|PARAMETERIZATION|SIMPLE|Benutzerkontensteuerung|  
|QUOTED_IDENTIFIER|OFF|Benutzerkontensteuerung|  
|READ_COMMITTED_SNAPSHOT|OFF|nein|  
|RECOVERY|SIMPLE|Benutzerkontensteuerung|  
|RECURSIVE_TRIGGERS|OFF|Benutzerkontensteuerung|  
|Service Broker-Optionen|ENABLE_BROKER|Benutzerkontensteuerung|  
|TRUSTWORTHY|ON|Benutzerkontensteuerung|  
  
 Eine Beschreibung dieser Datenbankoptionen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="restrictions"></a>Restrictions  
 Die folgenden Operationen können an der **msdb** -Datenbank nicht ausgeführt werden:  
  
-   Ändern der Sortierung. Die Standardsortierung entspricht der Serversortierung.  
  
-   Löschen der Datenbank.  
  
-   Löschen des **guest** -Benutzers aus der Datenbank.  
  
-   Aktivieren von Change Data Capture  
  
-   Teilnehmen an der Datenbankspiegelung.  
  
-   Entfernen der primären Dateigruppe, der primären Datendatei oder der Protokolldatei.  
  
-   Umbenennen der Datenbank oder der primären Dateigruppe.  
  
-   Versetzen der Datenbank in den OFFLINE-Modus.  
  
-   Versetzen der primären Dateigruppe in den READ_ONLY-Modus.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Systemdatenbanken](../../relational-databases/databases/system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
 [Verschieben von Datenbankdateien](../../relational-databases/databases/move-database-files.md)  
  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
