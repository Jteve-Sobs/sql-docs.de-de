---
title: QUOTENAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- QUOTENAME_TSQL
- QUOTENAME
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- input strings [SQL Server]
- Unicode [SQL Server], delimited identifiers
- QUOTENAME function
- valid identifiers [SQL Server]
ms.assetid: 34d47f1e-2ac7-4890-8c9c-5f60f115e076
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 761e6f43f1199d4eb16060cd769a30ebba220ef8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67914252"
---
# <a name="quotename-transact-sql"></a>QUOTENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Unicode-Zeichenfolge mit hinzugefügten Trennzeichen zurück, sodass die Eingabezeichenfolge ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
QUOTENAME ( 'character_string' [ , 'quote_character' ] )   
```  
  
## <a name="arguments"></a>Argumente  
 '*character_string*'  
 Eine Zeichenfolge von Unicode-Zeichendaten. *character_string* ist vom Datentyp **sysname** und auf 128 Zeichen beschränkt. Eingaben, die größer als 128 Zeichen sind, geben NULL zurück.  
  
 '*quote_character*'  
 Eine Zeichenfolge mit einem Zeichen, das als Trennzeichen verwendet wird. Dies kann ein einfaches Anführungszeichen ( **'** ) sein, eine linke oder recht eckige Klammer ( **[]** ), ein doppeltes Anführungszeichen ( **"** ), eine linke oder recht runde Klammer ( **()** ), ein größer als- oder kleiner als-Zeichen ( **><** ), eine linke oder rechte geschweifte Klammer ( **{}** ) oder ein Hochkomma/Backtick ( **\`** ). NULL wird zurückgegeben, wenn ein unzulässiges Zeichen angegeben wird. Wenn *quote_character* nicht angegeben wird, werden eckige Klammern verwendet.  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(258)**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mit der Zeichenfolge `abc[]def` und den Zeichen `[` und `]` ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner erstellt.  
  
```  
SELECT QUOTENAME('abc[]def');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc[]]def]  
  
(1 row(s) affected)  
```  
  
 Beachten Sie, dass die rechte Klammer in der Zeichenfolge `abc[]def` verdoppelt wurde, um ein Escapezeichen anzugeben.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Im folgenden Beispiel wird mit der Zeichenfolge `abc def` und den Zeichen `[` und `]` ein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Begrenzungsbezeichner erstellt.  
  
```  
SELECT QUOTENAME('abc def');   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc def]  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PARSENAME &#40;Transact-SQL&#41;](../../t-sql/functions/parsename-transact-sql.md)  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

