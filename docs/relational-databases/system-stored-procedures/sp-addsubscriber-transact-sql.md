---
title: Sp_addsubscriber (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber
- sp_addsubscriber_TSQL
helpviewer_keywords:
- sp_addsubscriber
ms.assetid: b8a584ea-2a26-4936-965b-b84f026e39c0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cd59aae098a91a47e1137bd55cd97cf1066b02bf
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493372"
---
# <a name="spaddsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einen neuen Abonnenten zu einem Verleger hinzu, wobei dieser für den Empfang von Veröffentlichungen aktiviert wird. Diese gespeicherte Prozedur wird für Momentaufnahme- und Transaktionsveröffentlichungen auf dem Verleger in der Veröffentlichungsdatenbank ausgeführt. Für Mergeveröffentlichungen, die einen Remoteverteiler verwenden, wird diese gespeicherte Prozedur auf dem Verteiler ausgeführt.  
  
> [!IMPORTANT]  
>  Diese gespeicherte Prozedur wurde als veraltet markiert. Es ist nicht mehr erforderlich, einen Abonnenten ausdrücklich auf dem Verleger zu registrieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsubscriber [ @subscriber = ] 'subscriber'  
    [ , [ @type = ] type ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @commit_batch_size = ] commit_batch_size ]  
    [ , [ @status_batch_size = ] status_batch_size ]  
    [ , [ @flush_frequency = ] flush_frequency ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @security_mode = ] security_mode ]  
    [ , [ @encrypted_password = ] encrypted_password ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subscriber = ] 'subscriber'` Ist der Name des Servers, der den Veröffentlichungen auf diesem Server als gültiger Abonnent hinzugefügt werden soll. *Abonnenten* ist **Sysname**, hat keinen Standardwert.  
  
`[ @type = ] type` Ist der Typ des Abonnenten. *Typ* ist **Tinyint**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0** (Standardwert)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten|  
|**1**|ODBC-Datenquellenserver|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet-Datenbank|  
|**3**|OLE DB-Anbieter|  
  
`[ @login = ] 'login'` Ist die Anmelde-ID für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @password = ] 'password'` Das Kennwort für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *Kennwort* ist **nvarchar(524)**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @commit_batch_size = ] commit_batch_size` Dieser Parameter ist veraltet und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @status_batch_size = ] status_batch_size` Dieser Parameter ist veraltet und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @flush_frequency = ] flush_frequency` Dieser Parameter ist veraltet und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit für die Planung des Replikations-Agents. *Frequency_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64** (Standard)|Autostart|  
|**128**|Wiederholt|  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
 [**@frequency_interval=** ] *Frequency_interval*  
 Ist der Wert der Häufigkeit festgelegt angewendet *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert 1.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Replikations-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert **5**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der erste der Replikations-Agent ist, erfolgt Format: HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Replikations-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet*ist **Int**, hat den Standardwert 235959, womit 23:59:59 Uhr auf dem 24-Stunden-Format an.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Replikations-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert 0.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Replikations-Agent nicht mehr, geplant ist JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert 99991231, womit der 31. Dezember 9999.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @description = ] 'description'` Ist eine textbeschreibung des Abonnenten. *Beschreibung* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @security_mode = ] security_mode` Ist der implementierte Sicherheitsmodus. *Security_mode* ist **Int**, hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die Eigenschaft ist nun auf abonnementspezifischer Basis angegeben, beim Ausführen [Sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @encrypted_password = ] encrypted_password` Dieser Parameter ist veraltet und wird zur Abwärtskompatibilität bereitgestellt, nur das Festlegen von *Encrypted_password* auf einen beliebigen Wert aber **0** führt zu einem Fehler.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addsubscriber** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
 **Sp_addsubscriber** ist nicht erforderlich, wenn der Abonnent nur anonyme Abonnements von mergeveröffentlichungen haben.  
  
 **Sp_addsubscriber** schreibt in die [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) -Tabelle in der **Verteilung** Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_addsubscriber**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
