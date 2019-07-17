---
title: Sp_copysubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71027fb060a5085289aed4c8a637bc76a71bbd2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108679"
---
# <a name="spcopysubscription-transact-sql"></a>sp_copysubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Die Funktion für anfügbare Abonnements ist als veraltet markiert und wird in einer zukünftigen Version entfernt. Diese Funktion sollte bei neuen Entwicklungen nicht verwendet werden. Für Mergeveröffentlichungen, die mithilfe von parametrisierten Filtern partitioniert werden, ist es empfehlenswert, die neuen Funktionen von partitionierten Momentaufnahmen zu verwenden. Diese vereinfachen die Initialisierung zahlreicher Abonnements. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Für nicht partitionierte Veröffentlichungen können Sie ein Abonnement mit einer Sicherung initialisieren. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
 Kopiert eine Abonnementdatenbank, die über Pullabonnements, nicht jedoch über Pushabonnements verfügt. Es können nur einzelne Dateidatenbanken kopiert werden. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @filename = ] 'file_name'` Ist die Zeichenfolge, die den vollständigen Pfad einschließlich des Dateinamens gibt an, in dem eine Kopie der Datendatei (MDF) gespeichert wird. *Dateiname* ist **nvarchar(260)** , hat keinen Standardwert.  
  
`[ @temp_dir = ] 'temp_dir'` Ist der Name des Verzeichnisses, das die temporären Dateien enthält. *Temp_dir* ist **nvarchar(260)** , hat den Standardwert NULL. Wenn der Wert NULL ist, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standarddatenverzeichnis verwendet werden. Das Verzeichnis sollte über ausreichenden Speicherplatz verfügen, um eine Datei aufzunehmen, die der Größe aller Datenbankdateien auf dem Abonnenten zusammen entspricht.  
  
`[ @overwrite_existing_file = ] 'overwrite_existing_file'` Ist ein optionales boolesches Flag, der angibt, ob eine vorhandene Datei mit dem gleichen Namen im angegebenen überschrieben **@filename** . *Overwrite_existing_file*ist **Bit**, hat den Standardwert **0**. Wenn **1**, überschreibt er die angegebene Datei **@filename** , sofern vorhanden. Wenn **0**, die gespeicherte Prozedur fehlschlägt, wenn die Datei vorhanden ist, und die Datei nicht überschrieben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_copysubscription** wird bei allen Replikationstypen zum Kopieren einer Abonnementdatenbank in einer Datei als Alternative zum Anwenden einer Momentaufnahme auf dem Abonnenten verwendet. Die Datenbank muss so konfiguriert sein, dass ausschließlich Pullabonnements unterstützt werden. Benutzer mit entsprechenden Berechtigungen können Kopien der Abonnementdatenbank erstellen und die Abonnementdatei (MSF) dann per E-Mail, durch Kopieren oder Übertragen an einen anderen Abonnenten senden. Dort kann die Datei dann als Abonnement angefügt werden.  
  
 Die Größe der kopierten Abonnementdatenbank muss weniger als 2 Gigabyte (GB) betragen.  
  
 **Sp_copysubscription** wird nur für Datenbanken mit Clientabonnements unterstützt und kann nicht ausgeführt werden, wenn die Datenbank serverabonnements hat.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_copysubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../../relational-databases/replication/snapshot-options.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
