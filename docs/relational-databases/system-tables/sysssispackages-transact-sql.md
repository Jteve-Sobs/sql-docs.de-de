---
title: Sysssispackages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3e25d69b4ba7887d20ef86ff771a3f10864ddbd6
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65489808"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Paket, das gespeichert wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der eindeutige Bezeichner des Pakets.|  
|**id**|**uniqueidentifier**|GUID des Pakets|  
|**description**|**nvarchar**|Eine optionale Beschreibung des Pakets.|  
|**createdate**|**datetime**|Erstellungsdatum des Pakets|  
|**folderid**|**uniqueidentifier**|Die GUID des logischen Ordners, in dem das Paket von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aufgelistet ist.|  
|**ownersid**|**varbinary**|Die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat|  
|**packagedata**|**image**|Das Paket.|  
|**packageformat**|**int**|Das Format, in dem das Paket gespeichert wird:<br /><br /> Ein Wert von 2 Gibt an, dass das Paket, in gespeichert wird der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Format.<br /><br /> Der Wert 3 gibt an, dass das Paket, im Format gespeichert wird [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]oder höher.|  
|**packagetype**|**int**|Der Client, der das Paket erstellt hat. Die folgenden Werte sind möglich:<br /><br /> 0 (Standardwert)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import/Export-Assistent)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replikation)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer)<br /><br /> 6 (Wartungsplan-Designer oder -Assistent).<br /><br /> <br /><br /> Beachten Sie, die die Werte in dieser Spalte entsprechen der <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> Enumeration.|  
|**vermajor**|**int**|Die aktuelle Hauptversion des Pakets.|  
|**verminor**|**int**|Die aktuelle Nebenversion des Pakets.|  
|**verbuild**|**int**|Das letzte Build des Pakets.|  
|**vercomments**|**nvarchar**|Kommentare zur Paketversion|  
|**verid**|**uniqueidentifier**|GUID der Paketversion|  
|**isencrypted**|**bit**|Ein boolescher Wert, der angibt, ob das Paket verschlüsselt ist|  
|**readrolesid**|**varbinary**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rolle, die Pakete laden kann|  
|**writerolesid**|**varbinary**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rolle, die Pakete speichern kann|  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Pakete &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)  
  
  
