---
title: Sp_add_agent_profile (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: edb5fc6c24ce8e59c82b35ac10e6dddb67adeaf4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52752152"
---
# <a name="spaddagentprofile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt für einen Replikations-Agent ein neues Profil. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@profile_id=** ] *profile_id*  
 Die dem neu eingefügten Profil zugeordnete ID. *Profile_id* ist **Int** und ist ein optionaler OUTPUT-Parameter. Wenn profile_id angegeben wird, wird der Wert auf die ID des neuen Profils festgelegt.  
  
 [  **@profile_name=** ] **"**_Profile_name_**"**  
 Der Name des Profils. *profile_name* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [  **@agent_type=** ] **"**_Agent_type_**"**  
 Der Typ des Replikations-Agents. *Agent_type* ist **Int**und hat keinen Standardwert und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Momentaufnahme-Agent|  
|**2**|Protokolllese-Agent|  
|**3**|Verteilungs-Agent|  
|**4**|Merge-Agent|  
|**9**|Warteschlangenlese-Agent|  
  
 [  **@profile_type=** ] *Profile_type*  
 Ist der Typ des Profils. *Profile_type* ist **Int**, hat den Standardwert **1**.  
  
 **0** bezeichnet ein Systemprofil. **1** bezeichnet ein benutzerdefiniertes Profil. Mit dieser gespeicherten Prozedur können nur benutzerdefinierte Profile erstellt werden. aus diesem Grund ist der einzige gültige Wert **1**. Nur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt Systemprofile.  
  
 [  **@description=** ] **"**_Beschreibung_**"**  
 Eine Beschreibung des Profils. *Beschreibung* ist **nvarchar(3000)**, hat keinen Standardwert.  
  
 [  **@default=** ] *Standard*  
 Gibt an, ob das Profil das Standardprofil für ist *Agent_type **.* *standardmäßige* ist **Bit**, hat den Standardwert **0**. **1** gibt an, dass das hinzuzufügende Profil zum neuen Standardprofil für den Agent gemäß wird *Agent_type*.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_agent_profile** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
 Benutzerdefinierte Agentprofile werden mit den standardmäßigen Agentparameterwerten hinzugefügt. Verwendung [Sp_change_agent_parameter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) so ändern Sie diese Standardwerte oder [Sp_add_agent_parameter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) zusätzliche Parameter hinzufügen.  
  
 Wenn **Sp_add_agent_profile** wird ausgeführt, für das neue benutzerdefinierte Profil in eine Zeile hinzugefügt wird die [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) Tabelle und die zugehörigen Standardparameter für diese Profil werden hinzugefügt, um die [MSagent_parameters &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) Tabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_add_agent_profile**.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Replikations-Agent-Profilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Replikations-Agent-Profile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [Sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [Sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [Sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [Sp_drop_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [Sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
