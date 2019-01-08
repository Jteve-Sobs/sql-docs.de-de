---
title: Sp_replcounters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords:
- sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 28fe1f158a34aa599fcadba2f8921aa5c4adacc2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822204"
---
# <a name="spreplcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Replikationsstatistiken über Latenz, Durchsatz und Transaktionsanzahl für alle veröffentlichten Datenbanken zurück. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Datenbank**|**sysname**|Der Name der Datenbank.|  
|**Replizierte Transaktionen**|**int**|Anzahl der Transaktionen im Protokoll, die darauf warten, an die Verteilungsdatenbank übermittelt zu werden.|  
|**Replikation Transaktionen/Sekunde**|**float**|Durchschnittliche Anzahl der Transaktionen, die pro Sekunde an die Verteilungsdatenbank übermittelt wurden.|  
|**Replikationswartezeit**|**float**|Durchschnittliche Zeit in Sekunden, für die Transaktionen im Protokoll verblieben, bevor sie verteilt wurden.|  
|**' Replbeginlsn '**|**binary(10)**|Protokollfolgenummer (LSN, Log Sequence Number) des aktuellen Abschneidepunkts im Protokoll.|  
|**Replnextlsn**|**binary(10)**|LSN des nächsten Commitdatensatzes, der auf die Übermittlung an die Verteilungsdatenbank wartet.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_replcounters** wird für die Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle **db_owner** oder der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Siehe auch  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [Sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [Sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
