---
title: Sysmail_configure_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_configure_sp_TSQL
- sysmail_configure_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_configure_sp
ms.assetid: 73b33c56-2bff-446a-b495-ae198ad74db1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abe47df497b61d35c66bfebfb3ba5a75fad0e183
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588554"
---
# <a name="sysmailconfiguresp-transact-sql"></a>sysmail_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert Konfigurationseinstellungen für Datenbank-E-Mail. Die Konfigurationseinstellungen, die mit angegebenen **Sysmail_configure_sp** gelten für die gesamte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_configure_sp [ [ @parameter_name = ] 'parameter_name' ]  
    [ , [ @parameter_value = ] 'parameter_value' ]  
    [ , [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [**@parameter_name** =] **"**_Parameter_name_**"**  
 Der Name des Parameters, der geändert werden soll  
  
 [**@parameter_value** =] **"**_Parameter_value_**"**  
 Der neue Wert des Parameters  
  
 [**@description** =] **"**_Beschreibung_**"**  
 Eine Beschreibung des Parameters  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-E-Mail verwendet die folgenden Parameter:  
  
||||  
|-|-|-|  
|Parametername|Description|Standardwert|  
|*AccountRetryAttempts*|Gibt an, wie oft der externe E-Mail-Prozess versucht, die E-Mail-Nachricht zu senden, wobei jedes Konto im angegebenen Profil verwendet wird.|**1**|  
|*AccountRetryDelay*|Gibt an, wie lange (in Sekunden) der externe E-Mail-Prozess zwischen zwei Versuchen, eine Nachricht zu senden, warten soll.|**5000**|  
|*DatabaseMailExeMinimumLifeTime*|Gibt an, wie lange (in Sekunden) der externe E-Mail-Prozess mindestens aktiv bleibt. Wenn Datenbank-E-Mail viele Nachrichten sendet, sollten Sie diesen Wert erhöhen, damit Datenbank-E-Mail aktiv bleibt und unnötiger Aufwand durch häufiges Starten und Beenden vermieden wird.|**600**|  
|*DefaultAttachmentEncoding*|Die Standardcodierung für E-Mail-Anlagen|MIME|  
|*MaxFileSize*|Die maximale Größe einer Anlage in Bytes.|**1000000**|  
|*ProhibitedExtensions*|Eine durch Trennzeichen getrennte Liste mit Erweiterungen, die nicht als Anlagen einer E-Mail-Nachricht gesendet werden können.|**EXE, Dll, Vbs, js**|  
|*LoggingLevel*|Gibt an, welche Nachrichten im Datenbank-E-Mail-Protokoll aufgezeichnet werden. Eine der folgenden numerischen Werte:<br /><br /> 1 - Dies ist der normale Modus. Es werden nur Fehler protokolliert.<br /><br /> 2 - Dies ist der erweiterte Modus. Es werden Fehler-, Warn- und Informationsmeldungen protokolliert.<br /><br /> 3 - Dies ist der ausführliche Modus. Es werden Fehler-, Warn-, Informations-, Erfolgs- sowie zusätzliche interne Meldungen protokolliert. Verwenden Sie diesen Modus zur Problembehandlung.|**2**|  
  
 Die gespeicherte Prozedur **Sysmail_configure_sp** befindet sich in der **Msdb** -Datenbank und im Besitz der **Dbo** Schema. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Festlegen von Datenbank-e-Mails, um jedes Konto 10 Wiederholungsversuche unternimmt**  
  
 Im folgenden Beispiel wird gezeigt, wie Datenbank-E-Mail so konfiguriert wird, dass für jedes Konto 10 Wiederholungsversuche unternommen werden, bevor das jeweilige Konto als nicht erreichbar eingestuft wird.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'AccountRetryAttempts', '10' ;  
```  
  
 **B. Festlegen der maximalen Anlagengröße auf 2 MB**  
  
 Im folgenden Beispiel wird gezeigt, wie die maximale Anlagengröße auf 2 MB festgelegt wird.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'MaxFileSize', '2097152' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_help_configure_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql.md)   
 [Datenbank-e-Mails gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
