---
title: '[^] (Platzhalterzeichen – nicht zu suchende(s) Zeichen) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
author: rothja
ms.author: jroth
ms.openlocfilehash: eedf1db97477788489dd9b7c9c1789804ca064a1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086094"
---
# <a name="-wildcard---characters-not-to-match-transact-sql"></a>\[^\] (Platzhalterzeichen – nicht zu suchende(s) Zeichen) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Entspricht einem einzelnen Zeichen, das nicht dem Bereich oder der Menge angehört, der bzw. die zwischen den eckigen Klammern angegeben ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der [^]-Operator verwendet, um alle Personen in der `Contact`-Tabelle zu suchen, deren Vorname mit `Al` beginnt und als dritten Buchstaben nicht den Buchstaben `a` besitzt.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%'  
ORDER BY FirstName;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [% &#40;Wildcard - Character&#40;s&#41; to Match&#41; &#40;Transact-SQL&#41; (% (Platzhalterzeichen – zu suchende(s) Zeichen) (Transact-SQL))](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; &#40;Wildcard - Character&#40;s&#41; to Match&#41; &#40;Transact-SQL&#41; ([ ] (Platzhalterzeichen – zu suchende(s) Zeichen) (Transact-SQL))](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [\_ &#40;Wildcard - Match One Character&#41; &#40;Transact-SQL&#41; (_ (Platzhalterzeichen – einzelnes zu suchendes Zeichen) (Transact-SQL))](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
