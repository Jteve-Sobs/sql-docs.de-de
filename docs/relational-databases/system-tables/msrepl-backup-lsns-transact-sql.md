---
title: MSrepl_backup_lsns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3c1870e9fba39995f7f8634076c658d8ef044999
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889528"
---
# <a name="msrepl_backup_lsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSrepl_backup_lsns** Tabelle enthält Transaktionsprotokoll-Sequenznummern (Log Sequence Number, LSN) zur Unterstützung der Option ' sync with Backup ' der Verteilungs Datenbank. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**valid_xact_id**|**varbinary(16)**|Die ID der Transaktion, die an den Verleger gesendet werden soll, um den Protokollkürzungspunkt zu markieren. Wird nur verwendet, wenn sich die Verteilungsdatenbank im Modus 'sync with backup' befindet. Enthält die ID der zuletzt in der Verteilungsdatenbank replizierten Transaktion, die gesichert wurde. Sie wird an den Verleger gesendet, damit der Protokollkürzungspunkt vom Protokollleser markiert werden kann.|  
|**valid_xact_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion, die an den Verleger gesendet werden soll, um den Protokollkürzungspunkt zu markieren. Sie wird nur verwendet, wenn sich die Verteilungsdatenbank im Modus 'sync with backup' befindet. Dies ist die Protokollfolgenummer (LSN, Log Sequence Number) der zuletzt in der Verteilungsdatenbank replizierten Transaktion, die gesichert wurde. Sie wird an den Verleger gesendet, damit der Protokollkürzungspunkt vom Protokollleser markiert werden kann.|  
|**next_xact_id**|**varbinary(16)**|Die temporäre Protokollfolgenummer (LSN, Log Sequence Number), die von Sicherungsvorgängen verwendet wird.|  
|**nextx_xact_seqno**|**varbinary(16)**|Die temporäre Protokollfolgenummer (LSN, Log Sequence Number), die von Sicherungsvorgängen verwendet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
