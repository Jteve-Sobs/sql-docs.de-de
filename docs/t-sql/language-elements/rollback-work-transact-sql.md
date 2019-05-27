---
title: ROLLBACK WORK (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROLLBACK WORK
- ROLLBACK_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- erasing data modifications [SQL Server]
- ROLLBACK WORK statement
- roll back transactions [SQL Server]
- rolling back transactions, ROLLBACK WORK
- savepoints [SQL Server]
ms.assetid: 2071dbd3-53d5-4510-be8d-26e80f2553b4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10a10b92a18566ca7a9ffaa8d5a4a80d69f3420b
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980306"
---
# <a name="rollback-work-transact-sql"></a>ROLLBACK WORK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Führt für eine benutzerdefinierte Transaktion einen Rollback zum Anfang der Transaktion aus.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROLLBACK [ WORK ]  
[ ; ]  
```  
  
## <a name="remarks"></a>Remarks  
 Diese Anweisung funktioniert genau wie ROLLBACK TRANSACTION, mit der Ausnahme, dass ROLLBACK TRANSACTION einen benutzerdefinierten Transaktionsnamen akzeptiert. Die ROLLBACK-Syntax ist ISO-kompatibel, unabhängig davon, ob das optionale WORK-Schlüsselwort angegeben wurde.  
  
 Wenn Transaktionen geschachtelt werden, führt ROLLBACK WORK immer einen Rollback bis zur äußersten BEGIN TRANSACTION-Anweisung durch und verringert die @@TRANCOUNT-Systemfunktion auf 0.  
  
## <a name="permissions"></a>Berechtigungen  
 Alle gültigen Benutzer erhalten standardmäßig ROLLBACK WORK-Berechtigungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [COMMIT WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
