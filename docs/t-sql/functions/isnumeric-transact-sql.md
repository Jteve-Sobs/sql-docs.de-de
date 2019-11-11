---
title: ISNUMERIC (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ISNUMERIC
- ISNUMERIC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], valid numeric type
- numeric data
- ISNUMERIC function
- verifying valid numeric type
- valid numeric type [SQL Server]
- checking valid numeric type
ms.assetid: 7aa816de-529a-4f6c-a99f-4d5a9ef599eb
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 75693068e1aa030f9027b1918becd27e8ec9cc5c
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843610"
---
# <a name="isnumeric-transact-sql"></a>ISNUMERIC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Ermittelt, ob ein Ausdruck ein gültiger numerischer Typ ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
ISNUMERIC ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Stellt den auszuwertenden [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) dar.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Remarks  
 ISNUMERIC gibt 1 zurück, wenn der Eingabeausdruck zu einem gültigen numerischen Datentyp ausgewertet wird; andernfalls wird 0 zurückgegeben. Beispiele für gültige [numerische Datentypen](../../t-sql/data-types/numeric-types.md):  

|||
|-|-|
| [Genaue numerische Werte](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) | **bigint**, **int**, **smallint**, **tinyint**, **bit** |
| [Feste Genauigkeit](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) | **decimal**, **numeric** |
| [Ungefähr](../../t-sql/data-types/float-and-real-transact-sql.md) | **float**, **real** |
| [Monetäre Werte](../../t-sql/data-types/money-and-smallmoney-transact-sql.md) | **money**, **smallmoney** |

  
> [!NOTE]  
>  ISNUMERIC gibt für einige Zeichen, die keine Zahlen darstellen, 1 zurück, beispielsweise für Plus (+), Minus (-) und für die gültigen Währungssymbole, z. B. das Dollarzeichen ($). Eine vollständige Liste der Währungssymbole finden Sie unter [money und smallmoney &#40;Transact-SQL&#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden mit `ISNUMERIC` alle Postleitzahlen zurückgegeben, die keine numerischen Werte sind.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, PostalCode  
FROM Person.Address   
WHERE ISNUMERIC(PostalCode)<> 1;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Im folgenden Beispiel werden mit `ISNUMERIC` alle Postleitzahlen zurückgegeben, die keine numerischen Werte sind.  
  
```  
USE master;  
GO  
SELECT name, isnumeric(name) AS IsNameANumber, database_id, isnumeric(database_id) AS IsIdANumber   
FROM sys.databases;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

