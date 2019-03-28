---
title: Sp_who (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_who_TSQL
- sp_who
dev_langs:
- TSQL
helpviewer_keywords:
- sp_who
ms.assetid: 132dfb08-fa79-422e-97d4-b2c4579c6ac5
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dbed86af1415f89a59b7de85061a6db1db324307
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536345"
---
# <a name="spwho-transact-sql"></a>sp_who (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu aktuellen Benutzern, Sitzungen und Prozessen in einer Instanz von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Die Informationen können gefiltert werden, damit nur die Prozesse zurückgegeben werden, die sich nicht im Leerlauf befinden, die zu einem bestimmten Benutzer gehören oder die zu einer bestimmten Sitzung gehören.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_who [ [ @loginame = ] 'login' | session ID | 'ACTIVE' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login' | session ID | 'ACTIVE'` Dient zum Filtern des Resultsets.  
  
 *Anmeldung* ist **Sysname** , Prozessen, deren Besitzer eines bestimmten Anmeldenamens identifiziert.  
  
 *Sitzungs-ID* ist eine Sitzungs-ID, die zu gehören die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz. *Sitzungs-ID* ist **Smallint**.  
  
 **AKTIVE** schließt Sitzungen, die auf den nächsten Befehl vom Benutzer warten.  
  
 Wenn kein Wert angegeben ist, meldet die Prozedur alle zur Instanz gehörenden Sitzungen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 **Sp_who** gibt ein Resultset mit den folgenden Informationen zurück.  
  
|Spalte|Datentyp|Description|  
|------------|---------------|-----------------|  
|**spid**|**smallint**|Sitzungs-ID.|  
|**ecid**|**smallint**|Ausführungskontext-ID für einen bestimmten Thread, der einer bestimmten Sitzungs-ID zugeordnet ist.<br /><br /> ECID = {0, 1, 2, 3,... *n*}, wobei 0 immer stellt dar, den Hauptknoten oder übergeordneten Thread und {1, 2, 3,... *n*} die Subthreads.|  
|**status**|**nchar(30)**|Prozessstatus. Die folgenden Werte sind möglich:<br /><br /> **dormant**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setzt die Sitzung zurück.<br /><br /> **running**. Die Sitzung führt einen oder mehrere Batches aus. Wenn MARS (Multiple Active Result Sets) aktiviert ist, kann eine Sitzung mehrere Batches ausführen. Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **Hintergrund**. Die Sitzung führt einen Hintergrundtask aus, z. B. Deadlockerkennung.<br /><br /> **rollback**. Die Sitzung führt gerade einen Transaktionsrollback aus.<br /><br /> **ausstehende**. Die Sitzung wartet, dass ein Arbeitsthread verfügbar wird.<br /><br /> **runnable**. Der Task der Sitzung wartet in der ausführbaren Warteschlange eines Zeitplanungsmoduls darauf, ein Zeitquantum zu erhalten.<br /><br /> **spinloop**. Der Task der Sitzung wartet darauf, dass ein Spinlock frei wird.<br /><br /> **angehalten**. Die Sitzung wartet, dass ein Ereignis, z. B. E/A, abgeschlossen wird.|  
|**loginame**|**nchar(128)**|Dem entsprechenden Prozess zugeordneter Benutzername.|  
|**hostname**|**nchar(128)**|Host- oder Computername für den Prozess.|  
|**blk**|**char(5)**|Sitzungs-ID für den blockierenden Prozess, falls vorhanden. Andernfalls ist diese Spalte 0.<br /><br /> Wenn eine Transaktion einer bestimmten Sitzungs-ID zugeordnet ist und durch eine verwaiste verteilte Transaktion blockiert wird, gibt diese Spalte den Wert -2 für die blockierende verwaiste Transaktion zurück.|  
|**dbname**|**nchar(128)**|Vom Prozess verwendete Datenbank.|  
|**cmd**|**nchar(16)**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]-Befehl ([!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung, interner [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Prozess usw.), der für den Prozess ausgeführt wird.|  
|**request_id**|**int**|ID für Anforderungen, die in einer bestimmten Sitzung ausgeführt werden.|  
  
 Bei paralleler Verarbeitung werden für die bestimmte Sitzungs-ID Subthreads erstellt. Der Hauptthread wird mit `spid = <xxx>` und `ecid =0` angegeben. Die anderen Subthreads verfügen über denselben `spid = <xxx>`, jedoch mit **Ecid** > 0.  
  
## <a name="remarks"></a>Hinweise  
 Ein blockierender Prozess, möglicherweise mit einer exklusiven Sperre, hat Ressourcen, die von einem anderen Prozess benötigt werden.  
  
 Allen verwaisten verteilten Transaktionen wird der Sitzungs-ID-Wert '-2' zugewiesen. Verwaiste verteilte Transaktionen sind verteilte Transaktionen, denen keine Sitzungs-ID zugeordnet ist. Weitere Informationen finden Sie unter [Wiederherstellen von verwandten Datenbanken mithilfe von markierten Transaktionen &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
 Abfrage der **Is_user_process** Spalte der Sys. dm_exec_sessions, um Systemprozesse von Benutzerprozessen zu trennen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server, um alle zurzeit ausgeführten Sitzungen in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuzeigen. Andernfalls wird dem Benutzer nur die aktuelle Sitzung angezeigt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-current-processes"></a>A. Auflisten aller aktuellen Prozesse  
 Im folgenden Beispiel wird `sp_who` ohne Parameter verwendet, um alle aktuellen Benutzer zurückzugeben.  
  
```  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
### <a name="b-listing-a-specific-users-process"></a>B. Auflisten des Prozesses eines bestimmten Benutzers  
 Das folgende Beispiel veranschaulicht das Anzeigen von Informationen zu einem einzelnen aktuellen Benutzer anhand des Benutzernamens.  
  
```  
USE master;  
GO  
EXEC sp_who 'janetl';  
GO  
```  
  
### <a name="c-displaying-all-active-processes"></a>C. Anzeigen aller aktiven Prozesse  
  
```  
USE master;  
GO  
EXEC sp_who 'active';  
GO  
```  
  
### <a name="d-displaying-a-specific-process-identified-by-a-session-id"></a>D. Anzeigen eines von einer Sitzungs-ID identifizierten bestimmten Prozesses  
  
```  
USE master;  
GO  
EXEC sp_who '10' --specifies the process_id;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
