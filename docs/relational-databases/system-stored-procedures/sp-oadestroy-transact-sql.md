---
title: Sp_OADestroy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OADestroy_TSQL
- sp_OADestroy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OADestroy
ms.assetid: 0bd1cff4-ceff-4095-9ae4-e1e65a80f5d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b4a7b238d3f7ade1706a78c3e595ec63ae2cce7
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449728"
---
# <a name="spoadestroy-transact-sql"></a>sp_OADestroy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zerstört ein zuvor erstelltes OLE-Objekt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OADestroy objecttoken      
```  
  
## <a name="arguments"></a>Argumente  
 *objecttoken*  
 Das Objekttoken eines zuvor mit **sp_OACreate**erstellten OLE-Objekts.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [OLE Automation Rückgabecodes und Fehlerinformationen](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Hinweise  
 Wird **sp_OADestroy** nicht aufgerufen, wird das erstellte OLE-Objekt am Ende des Batches automatisch gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** festen Serverrolle oder die execute-Berechtigung für diese gespeicherte Prozedur direkt. `Ole Automation Procedures` Konfiguration muss **aktiviert** mit einer beliebigen Systemprozedur, die im Zusammenhang mit der OLE-Automatisierung.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das zuvor erstellte **SQLServer** -Objekt zerstört.  
  
```  
EXEC @hr = sp_OADestroy @object;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte OLE-Automatisierung Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
