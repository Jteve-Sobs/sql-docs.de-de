---
title: Sp_lock (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_lock_TSQL
- sp_lock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_lock
ms.assetid: 9eaa0ec2-2ad9-457c-ae48-8da92a03dcb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: eb2c193b975d46eedf5139771ffe261bd6bfe93d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029990"
---
# <a name="splock-transact-sql"></a>sp_lock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu Sperren bereit.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Zum Abrufen von Informationen zu Sperren in der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], verwenden Sie die [Sys. dm_tran_locks](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md) dynamische verwaltungssicht.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_lock [ [ @spid1 = ] 'session ID1' ] [ , [@spid2 = ] 'session ID2' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @spid1 = ] 'session ID1'` Ist eine [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sitzungs-ID von **Sys. dm_exec_sessions** für die der Benutzer Sperrinformationen möchte. *Session ID1* ist **Int** hat den Standardwert NULL. Führen Sie **Sp_who** um Prozessinformationen zur Sitzung zu erhalten. Wenn *Session ID1* nicht angegeben ist, Informationen zu allen Sperren angezeigt wird.  
  
`[ @spid2 = ] 'session ID2'` Eine andere [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sitzungs-ID von **Sys. dm_exec_sessions** gesperrt sein, die zur gleichen Zeit wie *Session ID1* und darüber, welche die Benutzer ebenfalls Informationen möchte. *Sitzung "id2"* ist **Int** hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Die **Sp_lock** Resultset enthält eine Zeile für jede Sperre frei, die Sitzungen, die im angegebenen die **@spid1** und **@spid2** Parameter. Wenn weder **@spid1** noch **@spid2** angegeben ist, meldet das Resultset der Sperren für alle Sitzungen, die derzeit aktiven in der Instanz von der [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**spid**|**smallint**|Die Sitzungs-ID von [!INCLUDE[ssDE](../../includes/ssde-md.md)] für den Prozess, der die Sperre anfordert.|  
|**dbid**|**smallint**|Die ID der Datenbank, in der die Sperre aufrechterhalten wird. Sie können die DB_NAME()-Funktion zum Identifizieren der Datenbank verwenden.|  
|**ObjId**|**int**|Die ID des Objekts, auf dem die Sperre aufrechterhalten wird. Sie können die OBJECT_NAME()-Funktion in der verbundenen Datenbank zum Identifizieren des Objekts verwenden. Der Wert 99 ist ein Sonderfall, der auf eine Sperre auf einer der Systemseiten, die zum Aufzeichnen der Seitenzuordnungen in einer Datenbank verwendet wird, hinweist.|  
|**IndId**|**smallint**|Die ID des Indexes, auf dem die Sperre aufrechterhalten wird.|  
|**Typ**|**NCHAR(4)**|Der Sperrentyp:<br /><br /> RID = Eine Sperre einer einzelnen Zeile in einer Tabelle, die durch eine Zeilen-ID (Row Identifier, RID) gekennzeichnet ist.<br /><br /> KEY = Eine Sperre in einem Index, die einen Bereich von Schlüsselwerten in serialisierbaren Transaktionen schützt.<br /><br /> PAG = Sperre auf einer Daten- oder Indexseite.<br /><br /> EXT = Sperre auf einem Block.<br /><br /> TAB = Sperre für eine gesamte Tabelle, einschließlich aller Daten und Indizes.<br /><br /> DB = Sperre für eine Datenbank.<br /><br /> FIL = Sperre für eine Datenbankdatei.<br /><br /> APP = Sperre für eine anwendungsspezifische Ressource.<br /><br /> MD = Sperre für Metadaten oder Kataloginformationen.<br /><br /> HBT = Sperre für einen Heap oder B-Struktur-Index. Diese Informationen sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unvollständig.<br /><br /> AU = Sperre für eine Zuordnungseinheit. Diese Informationen sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unvollständig.|  
|**Ressource**|**NCHAR(32)**|Der Wert, der die gesperrte Ressource identifiziert. Das Format des Werts hängt von den Typ der Ressource identifiziert, die der **Typ** Spalte:<br /><br /> **Typ** Wert: **Ressource** Wert<br /><br /> LOS: Ein Bezeichner in das Format FileID: PageNumber: rid, wobei Fileid die Datei mit der Seite identifiziert Pagenumber die Seite identifiziert, die die Zeile enthält, und rid die Zeile auf der Seite. FileID entspricht der **File_id** -Spalte in der **Sys. database_files** -Katalogsicht angezeigt.<br /><br /> SCHLÜSSEL: Eine hexadezimale Zahl, die intern vom die [!INCLUDE[ssDE](../../includes/ssde-md.md)].<br /><br /> PAG: Eine Zahl in das Format FileID: PageNumber, wobei FileID die Datei, die Seite enthält, und Pagenumber die Seite identifiziert.<br /><br /> EXT: Eine Zahl, die erste Seite im Block. Die Zahl weist das Format fileid:pagenumber auf.<br /><br /> REGISTERKARTE ": Keine Informationen bereitgestellt, da die Tabelle bereits, in identifiziert wird der **ObjId** Spalte.<br /><br /> DB: Keine Informationen bereitgestellt, da Sie bereits in die Datenbank identifiziert wird die **Dbid** Spalte.<br /><br /> FIL: Der Bezeichner der Datei, die erfüllt die **File_id** -Spalte in der **Sys. database_files** -Katalogsicht angezeigt.<br /><br /> APP: Ein Bezeichner, der für die gesperrte Anwendungsressource eindeutig ist. Im Format DbPrincipleId:\<erste zwei bis 16 Zeichen der Ressourcenzeichenfolge >\<Hashwert >.<br /><br /> MD: Variiert je nach Ressourcentyp. Weitere Informationen finden Sie unter der Beschreibung der **Resource_description** -Spalte in [Sys. dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md).<br /><br /> HBT: Keine Informationen verfügbar. Verwenden der **Sys. dm_tran_locks** dynamische verwaltungssicht.<br /><br /> AU: Keine Informationen verfügbar. Verwenden der **Sys. dm_tran_locks** dynamische verwaltungssicht.|  
|**Mode**|**nvarchar(8)**|Der angeforderte Sperrmodus. Mögliche Werte sind:<br /><br /> NULL = Auf die Ressource wird kein Zugriff erteilt. Dient als Platzhalter.<br /><br /> Sch-S = Schemastabilität. Stellt sicher, dass ein Schemaelement, wie z. B. eine Tabelle oder ein Index, nicht gelöscht wird, während eine Sitzung eine Schemastabilitätssperre für das Schemaelement aufrechterhält.<br /><br /> Sch-M = Schemaänderung. Muss von jeder Sitzung aufrechterhalten werden, die das Schema der angegebenen Ressource ändern möchte. Stellt sicher, dass keine anderen Sitzungen auf das angegebene Objekt verweisen.<br /><br /> S = Freigegebene Sperre. Der haltenden Sitzung wird der gemeinsame Zugriff auf die Ressource erteilt.<br /><br /> U = Updatesperre. Zeigt eine Updatesperre an, die für Ressourcen ausgegeben wurde, die möglicherweise aktualisiert werden. Es wird verwendet, um eine gängige Form des Deadlocks zu vermeiden, das auftritt, wenn mehrere Sitzungen Ressourcen für potenzielle Updates zu einem späteren Zeitpunkt sperren.<br /><br /> X = Exklusive Sperre. Der haltenden Sitzung wird exklusiver Zugriff auf die Ressource erteilt.<br /><br /> IS = Beabsichtigte freigegebene Sperre. Gibt die Absicht an, S-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.<br /><br /> IU = Beabsichtigte Updatesperre. Gibt die Absicht an, U-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.<br /><br /> IX = Beabsichtigte exklusive Sperre. Gibt die Absicht an, X-Sperren für eine untergeordnete Ressource in der Sperrhierarchie zu platzieren.<br /><br /> SIU = Freigegebene Sperre mit beabsichtigter Updatesperre. Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, Updatesperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.<br /><br /> SIX = Freigegebene Sperre mit beabsichtigter exklusiver Sperre. Zeigt den gemeinsamen Zugriff auf eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.<br /><br /> UIX = Updatesperre mit beabsichtigter exklusiver Sperre. Zeigt eine aufrechterhaltene Updatesperre für eine Ressource mit der Absicht an, exklusive Sperren für untergeordnete Ressourcen in der Sperrhierarchie zu erhalten.<br /><br /> BU = Massenupdatesperre. Wird von Massenvorgängen verwendet.<br /><br /> RangeS_S = Freigegebene Sperren für Schlüsselbereich und Ressource. Zeigt serialisierbaren Bereichsscan an.<br /><br /> RangeS_U = Freigegebene Sperre für Schlüsselbereich und Updatesperre für Ressource. Zeigt serialisierbaren Updatescan an.<br /><br /> RangeI_N = Einfügungssperre für Schlüsselbereich und NULL-Sperre für Ressource. Wird zum Testen von Bereichen verwendet, bevor ein neuer Schlüssel in einen Index eingefügt wird.<br /><br /> RangeI_S = Konvertierungssperre für Schlüsselbereich (RangeI_S). Wird durch eine Überschneidung von RangeI_N und RangeS_S-Sperren erstellt.<br /><br /> RangeI_U = Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N und U-Sperren erstellt wurde.<br /><br /> RangeI_X = Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N und X-Sperren erstellt wurde.<br /><br /> RangeX_S = Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N- und RangeS_S.-Sperren erzeugt wurde.<br /><br /> RangeX_U = Konvertierungssperre für Schlüsselbereich, die durch eine Überschneidung von RangeI_N und RangeS_U-Sperren erstellt wurde.<br /><br /> RangeX_X = Exklusive Sperren für Schlüsselbereich und Ressource. Dies ist eine Konvertierungssperre, die für das Update eines Schlüssels in einem Bereich verwendet wird.|  
|**Status**|**nvarchar(5)**|Der Status der Sperranforderung:<br /><br /> CNVRT: Die Sperre aus einem anderen Modus konvertiert wird, aber die Konvertierung wird blockiert, von einem anderen Prozess, der eine Sperre mit einem inkompatiblen Modus aufrechterhält.<br /><br /> GRANT: Die Sperre abgerufen wurde.<br /><br /> WARTE: Die Sperre wird von einem anderen Prozess, der eine Sperre mit einem inkompatiblen Modus aufrechterhält blockiert.|  
  
## <a name="remarks"></a>Hinweise  
 Benutzer können das Sperren von Lesevorgängen wie folgt steuern:  
  
-   Mit SET TRANSACTION ISOLATION LEVEL die Sperrebene für eine Sitzung angeben. Syntax und zu Einschränkungen finden Sie unter [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
-   Mithilfe von Sperrhinweisen die Sperrebene für einen bestimmten Tabellenverweis in einer FROM-Klausel angeben. Syntax und zu Einschränkungen finden Sie unter [Tabellenhinweise &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Alle verteilten Transaktionen, denen keine Sitzung zugeordnet ist, sind verwaiste Transaktionen. [!INCLUDE[ssDE](../../includes/ssde-md.md)] weist allen verwaisten verteilten Transaktionen den SPID-Wert -2 zu, wodurch ein Benutzer blockierende verteilte Transaktionen leichter identifizieren kann. Weitere Informationen finden Sie unter [Wiederherstellen von verwandten Datenbanken mithilfe von markierten Transaktionen &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-locks"></a>A. Auflisten aller Sperren  
 Im folgenden Beispiel werden Informationen zu allen Sperren angezeigt, die zurzeit in einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] bestehen.  
  
```  
USE master;  
GO  
EXEC sp_lock;  
GO  
```  
  
### <a name="b-listing-a-lock-from-a-single-server-process"></a>B. Auflisten einer Sperre von einem Prozess mit einem einzelnen Server  
 Im folgenden Beispiel werden Informationen, einschließlich der Sperren, zur Prozess-ID `53` angezeigt.  
  
```  
USE master;  
GO  
EXEC sp_lock 53;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md)   
 [OBJECT_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)  
  
  
