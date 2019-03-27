---
title: Sp_add_operator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1a6a9e45b1640a82cd15074373f162a97d9a0a6
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494078"
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Operator (Benachrichtigungsempfänger) für Warnungen und Aufträge.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]   
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]   
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]   
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name eines Operators (Benachrichtigungsempfänger). Dieser Name muss eindeutig sein und darf nicht die Prozentzeichen enthalten (**%**) Zeichen. *Namen* ist **Sysname**, hat keinen Standardwert.  
  
`[ @enabled = ] enabled` Gibt den aktuellen Status des Operators an. *aktiviert* ist **Tinyint**, hat den Standardwert **1** (aktiviert). Wenn **0**, der Operator ist nicht aktiviert und empfängt keine Benachrichtigungen.  
  
`[ @email_address = ] 'email_address'` Die e-Mail-Adresse des Operators. Diese Zeichenfolge wird direkt an das E-Mail-System übergeben. *Email_address* ist **nvarchar(100)**, hat den Standardwert NULL.  
  
 Sie können angeben, entweder eine physische e-Mail-Adresse oder einen Alias für *Email_address*. Zum Beispiel:  
  
 "**Jdoe**'oder'**jdoe@xyz.com**"  
  
> [!NOTE]  
>  Für Datenbank-E-Mail muss die E-Mail-Adresse verwendet werden.  
  
`[ @pager_address = ] 'pager_address'` Die Pageradresse des Operators. Diese Zeichenfolge wird direkt an das E-Mail-System übergeben. *Pager_address* ist **narchar(100)**, hat den Standardwert NULL.  
  
`[ @weekday_pager_start_time = ] weekday_pager_start_time` Die Uhrzeit, nach der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent sendet Pagerbenachrichtigungen an den angegebenen Operator an Wochentagen, von Montag bis Freitag. *Weekday_pager_start_time*ist **Int**, hat den Standardwert **090000**, womit 9:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @weekday_pager_end_time = ] weekday_pager_end_time` Die Uhrzeit, nach der **SQLServerAgent** Dienst nicht mehr sendet Pagerbenachrichtigungen an den angegebenen Operator an Wochentagen, von Montag bis Freitag. *Weekday_pager_end_time*ist **Int**, hat den Standardwert 180000, womit 18:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @saturday_pager_start_time = ] saturday_pager_start_time` Die Uhrzeit, nach der **SQLServerAgent** -Dienst samstags Pagerbenachrichtigungen an den angegebenen Operator sendet. *Saturday_pager_start_time* ist **Int**, hat den Standardwert 090000, womit 9:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @saturday_pager_end_time = ] saturday_pager_end_time` Die Uhrzeit, nach der **SQLServerAgent** Dienst sendet nicht mehr Pagerbenachrichtigungen an den angegebenen Operator an Samstagen am stärksten. *Saturday_pager_end_time*ist **Int**, hat den Standardwert **180000**, womit 18:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @sunday_pager_start_time = ] sunday_pager_start_time` Die Uhrzeit, nach der **SQLServerAgent** -Dienst an Sonntagen Pagerbenachrichtigungen an den angegebenen Operator sendet. *Sunday_pager_start_time*ist **Int**, hat den Standardwert **090000**, womit 9:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @sunday_pager_end_time = ] sunday_pager_end_time` Die Uhrzeit, nach der **SQLServerAgent** Dienst sendet nicht mehr Pagerbenachrichtigungen an den angegebenen Operator an Sonntagen. *Sunday_pager_end_time*ist **Int**, hat den Standardwert **180000**, womit 18:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @pager_days = ] pager_days` Ist eine Zahl, die die Tage, an denen der Operator für Pagerbenachrichtigungen (je nach den angegebenen Start-und Endzeit) verfügbar ist. *Pager_days*ist **Tinyint**, hat den Standardwert **0** , der angibt, des Operators kann nie eine Seite angezeigt. Gültige Werte reichen von **0** über **127**. *Pager_days*wird durch Addition der einzelnen Werte für die erforderlichen Tage berechnet. Beispielsweise wird von Montag bis Freitag **2**+**4**+**8**+**16** + **32** = **62**. In der folgenden Tabelle werden die Werte für die einzelnen Wochentage aufgelistet.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Sonntag|  
|**2**|Montag|  
|**4**|Dienstag|  
|**8**|Mittwoch|  
|**16**|Donnerstag|  
|**32**|Freitag|  
|**64**|Samstag|  
  
`[ @netsend_address = ] 'netsend_address'` Die Netzwerkadresse des Operators, an den die Netzwerknachricht gesendet wird. *Netsend_address*ist **nvarchar(100)**, hat den Standardwert NULL.  
  
`[ @category_name = ] 'category'` Der Name der Kategorie für diesen Operator. *Kategorie* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_operator** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
 Pagerbenachrichtigungen werden mithilfe des E-Mail-Systems durchgeführt. Daher muss das zugrunde liegende E-Mail-System in der Lage sein, Nachrichten an Pager zu senden.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_add_operator**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Operatorinformationen für `danwi` eingerichtet. Der Operator ist aktiviert. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent sendet montags bis freitags von 8 bis 17 Uhr Benachrichtigungen per Pager.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
