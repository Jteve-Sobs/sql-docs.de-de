---
title: Sp_helpmergealternatepublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0ff0acfc4e3eff25b4281637d1f707ce925a7df
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802252"
---
# <a name="sphelpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste aller Server zurück, die als alternative Verleger für Mergeveröffentlichungen aktiviert sind. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publisher=**] **'***publisher***'**  
 Ist der Name des alternativen Verlegers. *Verleger* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publication=**] **'***publication***'**  
 Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Name des alternativen Verlegers.|  
|**alternate_publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**alternate_publication**|**sysname**|Name der Veröffentlichung.|  
|**alternate_distributor**|**sysname**|Der Name des Verteilers.|  
|**friendly_name wurde**|**nvarchar(255)**|Die Beschreibung des alternativen Verlegers.|  
|**aktiviert**|**bit**|Gibt an, ob der Server ein alternativer Verleger ist. **1** gibt an, dass der Verleger als alternativer Verleger aktiviert ist. **0** gibt an, dass sie nicht aktiviert ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergealternatepublisher** wird bei der Mergereplikation verwendet.  
  
 Während jeder Mergesitzung fragt das System sowohl den Verleger als auch den Abonnenten nach ihren Listen alternativer Verleger ab. Der Mergeprozess fügt der Liste der alternativen Verleger Einträge hinzu bzw. entfernt Einträge aus der Liste, sodass die Liste der alternativen Verleger auf dem Abonnenten mit derjenigen auf dem Verleger übereinstimmt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der veröffentlichungszugriffsliste für die Veröffentlichung können ausführen **Sp_helpmergealternatepublisher**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
