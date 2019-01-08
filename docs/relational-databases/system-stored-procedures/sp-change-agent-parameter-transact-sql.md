---
title: Sp_change_agent_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30b9216b2c33998b45a07c0b16d58f1b9c1139be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52819114"
---
# <a name="spchangeagentparameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Änderungen, die ein Parameter eines Replikations-Agentprofils, in gespeichert der [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) -Systemtabelle. Diese gespeicherte Prozedur wird auf dem Verteiler, auf dem der Agent ausgeführt wird, für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@profile_id=**] *Profile_id*,  
 Die ID des Profils. *Profile_id* ist **Int**, hat keinen Standardwert.  
  
 [  **@parameter_name=**] **"***Parameter_name***"**  
 Ist der Name des Parameters. *Parameter_name* ist **Sysname**, hat keinen Standardwert. Bei Systemprofilen hängen die veränderbaren Parameter vom Typ der Momentaufnahme ab. Um herauszufinden, welche von Agent dies Art *Profile_id* darstellt, suchen die *Profile_id* -Spalte in der **Msagent_profiles** Tabelle, und beachten die *agent_type-Wert*  Wert.  
  
> [!NOTE]  
>  Wenn für ein Parameter unterstützt wird eine bestimmte *Agent_type*, aber im Agentprofil nicht definiert wurde ein Fehler zurückgegeben. Zum Hinzufügen eines Parameters zu einem Agentprofil Sie ausführen müssen, [Sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Für eine Momentaufnahme-Agent (*Agent_type*=**1**), in das Profil definiert, die folgenden Eigenschaften können geändert werden:  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **Anmeldungstimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Für einen Protokolllese-Agent (*Agent_type*=**2**), in das Profil definiert, die folgenden Eigenschaften können geändert werden:  
  
-   **HistoryVerboseLevel**  
  
-   **Anmeldungstimeout**  
  
-   **Meldungsintervall**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 Für einen Verteilungs-Agent (*Agent_type*=**3**), in das Profil definiert, die folgenden Eigenschaften können geändert werden:  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **Anmeldungstimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **Meldungsintervall**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **"QuotedIdentifier"**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Für einen Merge-Agent (*Agent_type*=**4**), in das Profil definiert, die folgenden Eigenschaften können geändert werden:  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **Anmeldungstimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **Ausgabe**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **Überprüfen**  
  
-   **ValidateInterval darstellt**  
  
 Für einen Warteschlangenlese-Agent (*Agent_type*=**9**), in das Profil definiert, die folgenden Eigenschaften können geändert werden:  
  
-   **HistoryVerboseLevel**  
  
-   **Anmeldungstimeout**  
  
-   **Ausgabe**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Um festzustellen, welche Parameter für ein bestimmtes Profil definiert wurden, führen Sie **Sp_help_agent_profile** und notieren Sie sich die *Profile_name* zugeordneten der *Profile_id*. Mit dem entsprechenden *Profile_id*, führen Sie anschließend **Sp_help_agent_parameters** verwenden, die *Profile_id* , die dem Profil zugeordneten Parameter anzuzeigen. Parameter können einem Profil hinzugefügt werden, durch Ausführen [Sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 [  **@parameter_value=**] **"***Parameter_value***"**  
 Der neue Wert des Parameters. *Parameter_value* ist **nvarchar(255)**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_change_agent_parameter** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_change_agent_parameter**.  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations-Agent-Profile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replikationsprotokolllese-Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replikationsmerge-Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Warteschlangenlese-Agent der Microsoft SQL Server-Replikation](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [Sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [Sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [Sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
