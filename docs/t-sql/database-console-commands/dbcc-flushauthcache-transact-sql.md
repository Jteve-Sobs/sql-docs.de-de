---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3f6d11a425da5daee9cb9caf0b64a2eefed117b8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025281"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Leert den Cache für die Datenbankauthentifizierung mit Informationen zu Anmeldungen und Firewallregeln für die aktuelle Benutzerdatenbank in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Diese Anweisung gilt nicht für logische Masterdatenbanken, da die Masterdatenbank den physischen Speicher enthält, der für Informationen zu Anmeldungen und Firewallregeln bestimmt ist. Für den Benutzer, der die Anweisung ausführt, und andere zum aktuellen Zeitpunkt verbundene Benutzer wird weiterhin keine Verbindung hergestellt. (DBCC FLUSHAUTHCACHE wird derzeit für [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] nicht unterstützt.)
 
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
Keine.
  
## <a name="remarks"></a>Remarks  
Der Authentifizierungscache erstellt eine Kopie von Anmeldungen und Serverfirewallregeln, die in der Masterdatenbank gespeichert sind, und überträgt diese in den Arbeitsspeicher der Benutzerdatenbank.  Da Informationen zu Benutzern eigenständiger Datenbanken bereits in der Benutzerdatenbank gespeichert sind, werden diese Benutzer nicht im Authentifizierungscache gespeichert.
Ständig aktive Verbindungen mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] erfordern alle 10 Stunden eine erneute Authentifizierung, die von [!INCLUDE[ssDE](../../includes/ssde-md.md)] durchgeführt. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] versucht, eine erneute Authentifizierung mit dem ursprünglich übermittelten Kennwort durchzuführen. Dabei ist keine Eingabe des Benutzers erforderlich. Aus Leistungsgründen wird die Verbindung nicht erneut authentifiziert, wenn ein Kennwort in der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] zurückgesetzt wird. Dies ist auch nicht der Fall, wenn die Verbindung aufgrund von Verbindungspooling zurückgesetzt wird. Dies unterscheidet sich von dem Verhalten eines lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn das Kennwort nach der ersten Authentifizierung der Verbindung geändert wurde, muss diese Verbindung beendet und eine neue unter Verwendung des neuen Kennworts hergestellt werden. Ein Benutzer mit der KILL DATABASE CONNECTION-Berechtigung kann eine Verbindung mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] explizit beenden, wenn er den Befehl [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md) verwendet.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert das [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Administratorkonto.
  
## <a name="example"></a>Beispiel  
Die folgende Anweisung entfernt den Authentifizierungscache für die aktuelle Datenbank.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
