---
title: Xp_loginconfig (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs:
- TSQL
helpviewer_keywords:
- xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8590a33f870dc14ac34118ce5e655acc6e67f257
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645102"
---
# <a name="xploginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Meldet die Anmeldesicherheitskonfiguration einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>Argumente  
 **'** *config_name* **'**  
 Der anzuzeigende Konfigurationswert. Wenn *Config_name* ist nicht angegeben ist, werden alle Konfigurationswerte gemeldet. *Config_name* ist **Sysname**, hat den Standardwert NULL und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Anmeldemodus**|Der Anmeldungssicherheitsmodus. Mögliche Werte sind **gemischt** und **Windows-Authentifizierung**.<br /><br /> Ersetzt durch:<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**Anmeldung**|Der Name der standardmäßigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmelde-ID für autorisierte Benutzer vertrauenswürdiger Verbindungen (für Benutzer ohne entsprechenden Anmeldenamen). Der Standardanmeldename ist **Gast**. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**Standarddomäne**|Der Name der standardmäßigen Windows-Domäne für Netzwerkbenutzer vertrauenswürdiger Verbindungen. Die Standarddomäne ist die Domäne des Computers, auf dem Windows und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**Überwachungsebene**|Die Überwachungsebene. Mögliche Werte sind **keine**, **Erfolg**, **Fehler**, und **alle**. Überwachungen werden in das Fehlerprotokoll und in die Windows-Ereignisanzeige geschrieben.|  
|**Set-hostname**|Gibt an, ob der Hostname aus dem Clientanmeldedatensatz durch den Windows-Netzwerk-Benutzernamen ersetzt wird. Mögliche Werte sind **"true"** oder **"false"** . Wenn dies festgelegt ist, der Netzwerknamen für den Benutzer angezeigt wird, in der Ausgabe von **Sp_who**.|  
|**map _**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Unterstrich (_) zugeordnet sind. Mögliche Werte sind **Trennzeichen für Domäne** (Standard), **Speicherplatz**, **null**, oder ein beliebiges einzelnes Zeichen. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**map $**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dollarzeichen ($) zugeordnet sind. Mögliche Werte sind **Trennzeichen für Domäne**, **Speicherplatz**, **null**, oder ein beliebiges einzelnes Zeichen. Der Standardwert ist **Speicherplatz**. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
|**# zuordnen**|Meldet, welche Windows-Sonderzeichen dem gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Nummernzeichen (#) zugeordnet sind. Mögliche Werte sind **Trennzeichen für Domäne**, **Speicherplatz**, **null**, oder ein beliebiges einzelnes Zeichen. Der Standard ist der Bindestrich. Dieser Wert wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Konfigurationswert|  
|**Konfigurationswert**|**sysname**|Die Einstellung für den Konfigurationswert|  
  
## <a name="remarks"></a>Hinweise  
 **Xp_loginconfig** kann nicht zum Festlegen von Konfigurationswerten verwendet werden.  
  
 Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], um den Anmeldemodus und die Überwachungsebene festzulegen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die **master** Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. Ausgeben aller Konfigurationswerte  
 Das folgende Beispiel gibt alle derzeit konfigurierten Einstellungen aus.  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>B. Ausgeben eines bestimmten Konfigurationswerts  
 Das folgende Beispiel gibt nur die Einstellung für den Anmeldemodus aus.  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
