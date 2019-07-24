---
title: Sp_prepexecrpc (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fea210183ae67179dcc6f686e25f939cd00713b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056334"
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Bereitet einen Aufruf einer parametrisierten, mithilfe eines RPC-Bezeichners angegebenen gespeicherten Prozedur vor und führt sie aus. Sp_prepexecrpc wird aufgerufen, indem ID = 14 in einem tabular Data Stream (TDS)-Paket.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argumente  
 *Handle*  
 Der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]generierte, vorbereitete Handlebezeichner. *handle* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *RPCCall*  
 Definiert den Aufruf für die gespeicherte Prozedur mit kanonischer ODBC-Syntax. *RPCCall* ist ein erforderlicher Parameter, der einen Eingabewert für eine **ntext** -Zeichenfolge erfordert.  
  
 *bound_param*  
 Gibt die optionale Verwendung zusätzlicher Parameter an. *bound_param* erfordert einen Eingabewert eines beliebigen Datentyps, um die zusätzlichen verwendeten Parameter festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
