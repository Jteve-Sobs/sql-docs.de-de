---
title: Schrägstrich-Stern (Blockkommentar) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0d6146d1890f69c5f3c2e17b5af22fee2c33bffa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676468"
---
# <a name="slash-star-block-comment-transact-sql"></a>Schrägstrich-Stern (Blockkommentar) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  Gibt vom Benutzer bereitgestellten Text an. Der Text zwischen den Kommentarzeichen /* und \* wird vom Server nicht ausgewertet.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
/*  
text_of_comment  
*/  
```  
  
## <a name="arguments"></a>Argumente  
 *text_of_comment*  
 Bezeichnet den Text des Kommentars. Dieser besteht aus einer oder mehreren Zeichenfolgen.  
  
## <a name="remarks"></a>Remarks  
 Kommentare können sowohl in einer gesonderten Zeile als auch innerhalb einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung eingefügt werden. Kommentare, die sich über mehrere Zeilen erstrecken, müssen in /* und \*/ eingeschlossen sein. Oft werden diese mehrzeiligen Kommentare folgendermaßen gekennzeichnet: Die erste Zeile beginnt mit /\*, die nachfolgenden Zeilen mit \*\*, und die letzte Zeile endet mit \*/.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
 Geschachtelte Kommentare werden unterstützt. Tritt das Zeichenmuster /* an einer beliebigen Stelle in einem vorhandenen Kommentar auf, wird es als Anfang eines geschachtelten Kommentars behandelt und benötigt deshalb das schließende Kommentarzeichen \*/. Fehlt das schließende Kommentarzeichen, wird ein Fehler generiert.  
  
 So generiert beispielsweise der folgende Code einen Fehler.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/   
SELECT @@VERSION;  
GO   
```  
  
 Nehmen Sie die folgende Änderung vor, um diesen Fehler zu vermeiden.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/ */  
SELECT @@VERSION;  
GO  
  
```  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Kommentare verwendet, um den Zweck des Codeabschnitts zu erläutern.  
  
```  
USE AdventureWorks2012;  
GO  
/*  
This section of the code joins the Person table with the Address table,   
by using the Employee and BusinessEntityAddress tables in the middle to   
get a list of all the employees in the AdventureWorks2012 database   
and their contact information.  
*/  
SELECT p.FirstName, p.LastName, a.AddressLine1, a.AddressLine2, a.City, a.PostalCode  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID   
JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
JOIN Person.Address AS a ON ea.AddressID = a.AddressID;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [-- &#40;Kommentar&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/comment-transact-sql.md)   
 [Control-of-Flow Language &#40;Transact-SQL&#41; (Sprachkonstrukte zur Ablaufsteuerung (Transact-SQL))](~/t-sql/language-elements/control-of-flow.md)  
  
  

