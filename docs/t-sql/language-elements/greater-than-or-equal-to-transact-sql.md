---
title: '&gt;= (größer oder gleich) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Greater
- '>='
- '>= (Greater Than or Equal To)'
- Equal To
- '>=_TSQL'
- Greater Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- greater than or equal to operator (>=)
- '>= (greater than or equal to operator)'
ms.assetid: 641ee28d-7536-46dd-a48a-6c63c2d59278
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8a661006b04f5af7116d03bf736bdabc70cf421c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075164"
---
# <a name="gt-greater-than-or-equal-to-transact-sql"></a>&gt;= (größer oder gleich) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Vergleicht zwei Ausdrücke nach dem Kriterium größer als oder gleich (ein Vergleichsoperator).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein beliebiger gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md). Beide Ausdrücke müssen implizit konvertierbare Datentypen besitzen. Die Konvertierung folgt den [Rangfolge der Datentypen](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Boolean  
  
## <a name="remarks"></a>Bemerkungen  
 Beim Vergleich von Ausdrücken, die ungleich NULL sind, ist das Ergebnis TRUE, wenn der linke Operand einen größeren Wert besitzt als der rechte Operand oder einen Wert, der gleich groß ist; andernfalls ist das Ergebnis FALSE.  
  
 Im Gegensatz zum Vergleichsoperator = (gleich) ist das Ergebnis des Vergleichs zweier NULL-Werte mit dem Operator >= nicht von der ANSI_NULLS-Einstellung abhängig.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using--in-a-simple-query"></a>A. Verwenden von >= in einer einfachen Abfrage  
 Im folgenden Beispiel werden alle Zeilen in der `HumanResources.Department` -Tabelle zurückgegeben, die in `DepartmentID` über einen Wert größer oder gleich 13 verfügen.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID >= 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
13           Quality Assurance  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(4 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [= &#40;Equals&#41; &#40;Transact-SQL&#41; (= &#40;ist gleich&#41; &#40;Transact-SQL&#41;)](../../t-sql/language-elements/equals-transact-sql.md)   
 [&#62; &#40;Greater Than&#41; &#40;Transact-SQL&#41; (&#62; &#40;größer als&#41; &#40;Transact-SQL&#41;)](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
