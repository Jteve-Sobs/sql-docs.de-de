---
title: sysdbmaintplan_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6bd1622e898d6554d5eb9fbc66fae729f5a8e973
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130475"
---
# <a name="sysdbmaintplan_databases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Tabelle ist enthalten, um vorhandene Informationen für Instanzen beizubehalten, die von einer früheren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Version von aktualisiert wurden. 
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen ändern den Inhalt dieser Tabelle nicht. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**plan_id**|**Uniqueidentifier**|ID des Wartungsplans.|  
|**database_name**|**sysname**|Der Name der Datenbank, die dem Datenbank-Wartungsplan zugeordnet ist.|  
  
  
