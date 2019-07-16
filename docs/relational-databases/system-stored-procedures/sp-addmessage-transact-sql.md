---
title: "\"sp_addmessage\" (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52d3db15c46af273e2f151e769a6b04be322ce5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061840"
---
# <a name="spaddmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert eine neue benutzerdefinierte Fehlermeldung in einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz. Mithilfe von gespeicherten Nachrichten **"sp_addmessage"** können angezeigt werden, mithilfe der **sys.messages** -Katalogsicht angezeigt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ \@msgnum = ] msg_id` Ist die ID der Nachricht. *Msg_id* ist **Int** hat den Standardwert NULL. *Msg_id* für benutzerdefinierte Fehler Nachrichten können eine ganze Zahl zwischen 50.001 und 2.147.483.647 sein. Die Kombination von *Msg_id* und *Sprache* muss eindeutig sein; wenn die ID für die angegebene Sprache bereits vorhanden ist, wird ein Fehler zurückgegeben.  
  
`[ \@severity = ]severity` Ist der Schweregrad des Fehlers an. *Schweregrad* ist **Smallint** hat den Standardwert NULL. Die gültigen Werte reichen von 1 bis 25. Weitere Informationen zu den Schweregraden finden Sie unter [Schweregrade von Datenbank-Engine-Fehlern](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ \@msgtext = ] 'msg'` Ist der Text der Fehlermeldung. *msg* ist **nvarchar(255)** hat den Standardwert NULL.  
  
`[ \@lang = ] 'language'` Ist die Sprache für diese Nachricht. *Sprache* ist **Sysname** hat den Standardwert NULL. Da mehrere Sprachen können, auf dem gleichen Server installiert werden *Sprache* gibt die Sprache, die in der jede Nachricht geschrieben wird. Wenn *Sprache* wird ausgelassen, die Sprache ist die Standardsprache für die Sitzung.  
  
`[ \@with_log = ] { 'TRUE' | 'FALSE' }` Ist, ob die Nachricht in das Windows-Anwendungsprotokoll geschrieben werden, wenn diese auftritt. **\@WITH_LOG** ist **varchar(5)** hat den Standardwert "false". Bei TRUE wird der Fehler immer in das Windows-Anwendungsprotokoll geschrieben. Bei FALSE wird der Fehler nicht immer in das Windows-Anwendungsprotokoll geschrieben, sondern in Abhängigkeit davon, wie er ausgelöst wurde. Nur Mitglieder der **Sysadmin** -Serverrolle kann diese Option verwenden.  
  
> [!NOTE]  
>  Wenn eine Meldung in das Windows-Anwendungsprotokoll geschrieben wird, wird sie auch in die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Fehlerprotokolldatei geschrieben.  
  
`[ \@replace = ] 'replace'` Wenn als Zeichenfolge angegeben *ersetzen*, wird eine vorhandene Fehlermeldung mit neuen Meldung und Schweregrad überschrieben. *Ersetzen Sie dies* ist **vom Datentyp varchar(7)** hat den Standardwert NULL. Diese Option muss angegeben werden, wenn *Msg_id* ist bereits vorhanden. Wenn Sie eine ersetzen Englischsprachige Meldung, die den Schweregrad wird für alle Nachrichten in allen anderen Sprachen, die die gleichen ersetzt *Msg_id*.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Für nicht englischsprachige Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], den USA Englische Version einer Nachricht muss bereits vorhanden sein, bevor die Nachricht mit einer anderen Sprache hinzugefügt werden kann. Der Schweregrad der beiden Versionen der Meldung muss übereinstimmen.  
  
 Verwenden Sie bei der Lokalisierung von Meldungen mit Parametern Parameternummern, die den Parametern der Originalmeldung entsprechen. Fügen Sie nach jeder Parameternummer ein Ausrufezeichen (!) ein.  
  
|Originalmeldung|Lokalisierte Meldung|  
|----------------------|-----------------------|  
|'Originalmeldung Parameter 1: %s,<br /><br /> Parameter 2: %d'|'Lokalisierte Meldung Parameter 1:<br /><br /> Parameter 2: %2! "|  
  
 Wegen Unterschieden in der Sprachsyntax weisen die Parameternummern in der lokalisierten Meldung möglicherweise eine andere Reihenfolge als in der Originalmeldung auf.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der **Sysadmin** oder **Serveradmin** festen Serverrollen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-defining-a-custom-message"></a>A. Definieren einer benutzerdefinierten Meldung  
 Im folgenden Beispiel wird eine benutzerdefinierte Meldung **sys.messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. Hinzufügen einer Meldung in zwei Sprachen  
 Im folgende Beispiel wird zuerst eine Nachricht in den USA Englisch, und fügt dann die gleiche Meldung in Französisch`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. Ändern der Reihenfolge der Parameter  
 Im folgende Beispiel wird zuerst eine Nachricht in den USA Englisch und fügt dann eine lokalisierte Meldung, die in der Reihenfolge der Parameter geändert wird.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
