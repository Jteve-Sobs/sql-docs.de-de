---
title: sp_flush_log (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fba195d53911264716c73b54ea8c639ca37951e6
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418311"
---
# <a name="sysspflushlog-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Leert das Transaktionsprotokoll der aktuellen Datenbank auf den Datenträger, wodurch alle verzögert dauerhaften Transaktionen, für die zuvor ein Commit ausgeführt wurde, festgeschrieben werden.  
  
 Wenn Sie die verzögerte Transaktionsdauerhaftigkeit aufgrund der Leistungsvorteile verwenden, gleichzeitig aber auch eine Zusicherung im Hinblick auf den maximalen Datenverlust benötigen, der bei einem Serverabsturz oder Failover auftreten darf, sollten Sie in regelmäßigen Abständen `sys.sp_flush_log` ausführen. Z. B. Wenn Sie sicherstellen, möchten Sie verlieren Sie nicht mehr als X Sekunden einen Zeitraum von Daten, führen Sie `sp_flush_log` alle x Sekunden.  
  
 Durch die Ausführung von `sys.sp_flush_log` wird sichergestellt, dass alle verzögert dauerhaften Transaktionen, für die zuvor ein Commit ausgeführt wurde, in dauerhafte Transaktionen konvertiert werden. Finden Sie unter dem Thema [Steuern der Transaktionsdauerhaftigkeit](../../relational-databases/logs/control-transaction-durability.md) für Weitere Informationen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Der Rückgabecode 1 steht für Erfolg.  Alle anderen Werte geben einen Fehler an.  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="sample-code"></a>Beispielcode  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
