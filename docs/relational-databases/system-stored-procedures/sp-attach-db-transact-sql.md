---
title: Sp_attach_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_db_TSQL
- sp_attach_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_db
ms.assetid: 59bc993e-7913-4091-89cb-d2871cffda95
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b0a6fdf71643f438201aae39010f25d2e43d15c
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588834"
---
# <a name="spattachdb-transact-sql"></a>sp_attach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt eine Datenbank an einen Server an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Es wird empfohlen, dass die Verwendung von CREATE DATABASE *Database_name* FOR ATTACH stattdessen. Weitere Informationen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
> [!NOTE]  
>  Um mehrere Protokolldateien neu zu erstellen, wenn eine oder mehrere einen neuen Speicherort aufweisen, verwenden Sie CREATE DATABASE *Database_name* FOR ATTACH_REBUILD_LOG.  
  
> [!IMPORTANT]  
>  Das Anfügen oder Wiederherstellen von Datenbanken aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Datenbanken können bösartigen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code ausführt oder Fehler verursacht, indem er das Schema oder die physische Datenbankstruktur ändert. Bevor Sie eine Datenbank aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, führen Sie auf einem Nichtproduktionsserver [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) für die Datenbank aus. Überprüfen Sie außerdem den Code in der Datenbank, z.B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_attach_db [ @dbname= ] 'dbname'  
    , [ @filename1= ] 'filename_n' [ ,...16 ]   
```  
  
## <a name="arguments"></a>Argumente  
 [  **@dbname=** ] **"**_Dbnam_ **"**  
 Der Name der Datenbank, die an den Server angefügt werden soll. Der Name muss eindeutig sein. *Dbname* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@filename1=** ] **"**_Filename_n_**"**  
 Der physische Name der Datenbankdatei, einschließlich des Pfads. *Filename_n* ist **nvarchar(260)**, hat den Standardwert NULL. Sie können bis zu 16 Dateinamen angeben. Die Parameternamen beginnen mit **@filename1** und werden bis **@filename16**. Die Liste der Dateinamen muss mindestens die primäre Datei einschließen. Die primäre Datei enthält die Systemtabellen, die auf andere Dateien in der Datenbank zeigen. Die Liste muss außerdem alle Dateien enthalten, die nach dem Trennen der Datenbank verschoben wurden.  
  
> [!NOTE]  
>  Dieses Argument entspricht dem FILENAME-Parameter der CREATE DATABASE-Anweisung. Weitere Informationen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
>   
>  Wenn Sie eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank mit Volltextkatalogdateien an eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Serverinstanz anfügen, werden die Katalogdateien von ihrem vorherigen Speicherort aus zusammen mit den anderen Datenbankdateien angefügt. Dies entspricht der Vorgehensweise in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Weitere Informationen finden Sie unter [Upgrade der Volltextsuche](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die **Sp_attach_db** gespeicherte Prozedur sollte nur ausgeführt werden, für Datenbanken, die zuvor vom Datenbankserver getrennt wurden, mithilfe eines expliziten **Sp_detach_db** Vorgang oder für kopierte Datenbanken. Wenn Sie mehr als 16 Dateien angeben müssen, verwenden Sie CREATE DATABASE *Database_name* FOR ATTACH oder CREATE DATABASE *Database_name* FOR_ATTACH_REBUILD_LOG. Weitere Informationen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Wird für eine Datei kein Pfad angegeben, wird davon ausgegangen, dass sie sich am zuletzt bekannten Speicherort befindet. Wenn Sie eine Datei an einem anderen Speicherort verwenden möchten, müssen Sie den neuen Speicherort angeben.  
  
 Eine Datenbank, die in einer neueren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurde, kann in früheren Versionen nicht angefügt werden.  
  
> [!NOTE]  
>  Eine Datenbankmomentaufnahme kann nicht getrennt oder angefügt werden.  
  
 Berücksichtigen Sie Folgendes, wenn Sie eine replizierte Datenbank anfügen, die kopiert statt getrennt wurde:  
  
-   Wenn Sie die Datenbank an die gleiche Serverinstanz und -version wie die ursprüngliche Datenbank anfügen, sind keine weiteren Schritte erforderlich.  
  
-   Wenn Sie die Datenbank an die gleiche Serverinstanz mit einer aktualisierten Version anfügen, müssen Sie [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) ausführen, um die Replikation zu aktualisieren, nachdem der Anfügevorgang abgeschlossen wurde.  
  
-   Wenn Sie die Datenbank an eine andere Serverinstanz unabhängig von der Version anfügen, müssen Sie [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) ausführen, um die Replikation zu entfernen, nachdem der Anfügevorgang abgeschlossen wurde.  
  
 Wird eine Datenbank zum ersten Mal an eine neue Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angefügt oder wiederhergestellt, ist noch keine Kopie des Datenbank-Hauptschlüssels (verschlüsselt vom Diensthauptschlüssel) auf dem Server gespeichert. Der Datenbank-Hauptschlüssel (Database Master Key, DMK) muss mithilfe der Anweisung **OPEN MASTER KEY** entschlüsselt werden. Nachdem der Datenbank-Hauptschlüssel entschlüsselt wurde, können Sie für die Zukunft die automatische Entschlüsselung aktivieren, indem Sie die Anweisung **ALTER MASTER KEY REGENERATE** verwenden. Auf diese Weise können Sie eine Kopie des mit dem Diensthauptschlüssel (Service Master Key, SMK) verschlüsselten Datenbank-Hauptschlüssels für den Server bereitstellen. Wenn eine Datenbank von einer früheren Version aktualisiert wurde, sollte der DMK neu generiert werden, damit er den neueren AES-Algorithmus verwendet. Weitere Informationen zum Neugenerieren des DMK finden Sie unter [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md). Die zum Neugenerieren des DMK zum Upgrade auf AES erforderliche Zeit hängt von der Anzahl der Objekte ab, die durch den DMK geschützt werden. Der DMK muss nur einmal auf AES aktualisiert und neu generiert werden. Dies hat keine Auswirkungen auf zukünftige Neugenerierungen im Rahmen einer Schlüsselrotationsstrategie.  
  
## <a name="permissions"></a>Berechtigungen  
 Weitere Informationen dazu, wie Berechtigungen behandelt werden, wenn eine Datenbank angefügt wird, finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Dateien von [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] an den aktuellen Server angefügt.  
  
```  
EXEC sp_attach_db @dbname = N'AdventureWorks2012',   
    @filename1 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf',   
    @filename2 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
