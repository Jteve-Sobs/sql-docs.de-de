---
title: Hinweise (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Join Hint
- Join_Hint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HASH join hint
- REMOTE join hint
- LOOP join hint
- join hints
- MERGE join hint
- hints [SQL Server], join
ms.assetid: 09069f4a-f2e3-4717-80e1-c0110058efc4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: f1c99da1106f366e50d7c02bcc666a4e0c167bb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719439"
---
# <a name="hints-transact-sql---join"></a>Hinweise (Transact-SQL) - Join
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Joinhinweise geben an, dass der Abfrageoptimierer eine Joinstrategie zwischen zwei Tabellen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erzwingt. Allgemeine Informationen zu Joins und zur Joinsyntax finden Sie unter [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
> [!CAUTION]  
>  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer in der Regel den optimalen Ausführungsplan für eine Abfrage auswählt, wird empfohlen, dass erfahrene Entwickler und Datenbankadministratoren Hinweise nur dann verwenden, wenn alle anderen Möglichkeiten sich als unzureichend erwiesen haben.
  
 **Gilt für:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<join_hint> ::=   
     { LOOP | HASH | MERGE | REMOTE }  
```  
  
## <a name="arguments"></a>Argumente  
 LOOP | HASH | MERGE  
 Legt fest, dass der Join in der Abfrage Schleifen, Hashing oder Zusammenführen verwenden soll. Durch die Verwendung von LOOP | HASH | MERGE JOIN wird ein bestimmter Join zwischen zwei Tabellen erzwungen. LOOP kann nicht zusammen mit RIGHT oder FULL als Jointyp angegeben werden.  
  
 REMOTE  
 Gibt an, dass der Joinvorgang am Standort der rechten Tabelle ausgeführt wird. Dies ist hilfreich, falls die linke Tabelle eine lokale und die rechte eine Remotetabelle ist. REMOTE sollte nur dann verwendet werden, wenn die linke Tabelle weniger Datensätze als die rechte Tabelle enthält.  
  
 Ist die rechte Tabelle lokal, wird der Join lokal ausgeführt. Falls beide Tabellen Remotetabellen sind, aber aus verschiedenen Datenquellen stammen, bewirkt REMOTE den Join am Standort der rechten Tabelle. Wenn beide Tabellen Remotetabellen aus der gleichen Datenquelle sind, ist die Angabe von REMOTE nicht notwendig.  
  
 REMOTE kann nicht verwendet werden, wenn einer der Werte, die im Joinprädikat verglichen werden, mithilfe der COLLATE-Klausel in eine andere Sortierung umgewandelt wird.  
  
 REMOTE kann nur für INNER JOIN-Vorgänge verwendet werden.  
  
## <a name="remarks"></a>Remarks  
 Joinhinweise werden in der FROM-Klausel einer Abfrage angegeben. Sie erzwingen eine Joinstrategie zwischen zwei Tabellen. Falls ein Joinhinweis für zwei beliebige Tabellen angegeben ist, erzwingt der Abfrageoptimierer automatisch die Joinreihenfolge für alle verknüpften Tabellen der Abfrage abhängig von der Position der ON-Schlüsselwörter. Wird CROSS JOIN ohne die ON-Klausel verwendet, kann die Joinreihenfolge mithilfe von Klammern angegeben werden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-hash"></a>A. Verwenden von HASH  
 Im folgenden Beispiel wird der `JOIN`-Vorgang in der Abfrage durch einen `HASH`-Join ausgeführt. Im Beispiel wird die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank verwendet.  
  
```  
SELECT p.Name, pr.ProductReviewID  
FROM Production.Product AS p  
LEFT OUTER HASH JOIN Production.ProductReview AS pr  
ON p.ProductID = pr.ProductID  
ORDER BY ProductReviewID DESC;  
```  
  
### <a name="b-using-loop"></a>B. Verwenden von LOOP  
 Im folgenden Beispiel wird der `JOIN`-Vorgang in der Abfrage durch einen `LOOP`-Join ausgeführt. Im Beispiel wird die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank verwendet.  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
    INNER LOOP JOIN Sales.SalesPerson AS sp  
    ON spqh.SalesPersonID = sp.SalesPersonID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
### <a name="c-using-merge"></a>C. Verwenden von MERGE  
 Im folgenden Beispiel wird der `JOIN`-Vorgang in der Abfrage durch einen `MERGE`-Join ausgeführt. Im Beispiel wird die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank verwendet.  
  
```  
SELECT poh.PurchaseOrderID, poh.OrderDate, pod.ProductID, pod.DueDate, poh.VendorID   
FROM Purchasing.PurchaseOrderHeader AS poh  
INNER MERGE JOIN Purchasing.PurchaseOrderDetail AS pod   
    ON poh.PurchaseOrderID = pod.PurchaseOrderID;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hints &#40;Transact-SQL&#41; (Hinweise (Transact-SQL))](../../t-sql/queries/hints-transact-sql.md)  
  
  
