---
title: Wiederherstellen zu einer Protokollfolgenummer (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/23/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46ab24ff86eb7a68e48f58e67f03a859d0c43aa7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72916035"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>Wiederherstellen zu einer Protokollfolgenummer (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dieses Thema ist nur für Datenbanken relevant, die das vollständige oder das massenprotokollierte Wiederherstellungsmodell verwenden.  
  
 Sie können eine Protokollfolgenummer (Log Sequence Number, LSN) zum Definieren des Wiederherstellungspunkts für einen Wiederherstellungsvorgang verwenden. Hierbei handelt es sich jedoch um eine auf Anbieter von Tools zugeschnittene Funktion, die nur in speziellen Fällen nutzbringend anzuwenden ist.  
  
##  <a name="LSNs"></a> Übersicht der Protokollfolgenummern  
 Mit LSNs wird intern während einer RESTORE-Sequenz der Zeitpunkt nachverfolgt, bis zu dem Daten wiederhergestellt wurden. Wenn eine Sicherung wiederhergestellt wird, werden die Daten bis zu der LSN wiederhergestellt, die dem Zeitpunkt entspricht, an dem die Sicherung erstellt wurde. Durch differenzielle Sicherungen und Protokollsicherungen wird ein späterer Status der Datenbank wiederhergestellt, was wiederum einer höheren LSN entspricht. Weitere Informationen zu LSNs finden Sie im [Handbuch zur Architektur und Verwaltung von Transaktionsprotokollen in SQL Server](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).  
  
> [!NOTE]  
> LSNs sind Werte vom Datentyp **numeric**(25,0). Arithmetische Operationen (z. B. Addition oder Subtraktion) sind ohne Bedeutung und dürfen für LSNs nicht verwendet.  
 
## <a name="viewing-lsns-used-by-backup-and-restore"></a>Anzeigen von LSNs, die von der Sicherung und Wiederherstellung verwendet werden  
 Die LSN eines Protokolldatensatzes, bei dem ein bestimmtes Sicherungs- und Wiederherstellungsereignis aufgetreten ist, kann mithilfe der folgenden Methoden angezeigt werden:  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md); [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
> [!NOTE]  
>  LSNs werden auch in manchen Meldungen im Fehlerprotokoll angezeigt.  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>Transact-SQL-Syntax für die Wiederherstellung bis zu einer LSN  
 Mithilfe einer [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) -Anweisung können Sie an oder direkt vor der LSN stoppen, wie im Folgenden gezeigt:  
  
-   Verwenden Sie die WITH STOPATMARK **='** lsn: _<LSN-Nummer>_ **'** -Klausel, wobei lsn: *\<LSN-Nummer>* eine Zeichenfolge darstellt, die angibt, dass der Protokolldatensatz mit der angegebenen LSN der Wiederherstellungspunkt ist.  
  
     Von STOPATMARK wird ein Rollforward zur LSN ausgeführt und dieser Protokolldatensatz im Rollforward eingeschlossen.  
  
-   Verwenden Sie die WITH STOPBEFOREMARK **= '** lsn: _<LSN-Nummer>_ **'** -Klausel, wobei lsn: *\<LSN-Nummer>* eine Zeichenfolge darstellt, die angibt, dass der Protokolldatensatz direkt vor dem Protokolldatensatz mit der angegebenen LSN der Wiederherstellungspunkt ist.  
  
     Von STOPBEFOREMARK wird ein Rollforward bis zur LSN ausgeführt und dieser Protokolldatensatz aus dem Rollforward ausgeschlossen.  
  
 Typischerweise wird eine bestimmte Transaktion zum Einschließen oder Ausschließen ausgewählt. Praktisch handelt es sich bei dem angegebenen Protokolldatensatz um einen Transaktionscommitdatensatz, wobei diese Angabe nicht zwingend erforderlich ist.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird davon ausgegangen, dass die `AdventureWorks` -Datenbank so geändert wurde, dass das vollständige Wiederherstellungsmodell verwendet wird.  
  
```sql  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Wiederherstellen einer Datenbank bis zu einer markierten Transaktion &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)     
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)     
 [Übersicht über Wiederherstellungsvorgänge (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery)       
 [Handbuch zur Architektur und Verwaltung von Transaktionsprotokollen in SQL Server](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)      
  
