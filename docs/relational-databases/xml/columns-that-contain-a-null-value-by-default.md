---
title: Spalten, die standardmäßig einen NULL-Wert enthalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d2b56355b21043f37e8d5991a453cc038064dce
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674979"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Spalten, die standardmäßig einen NULL-Wert enthalten
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  In der Standardeinstellung wird ein NULL-Wert in einer Spalte der Abwesenheit des Attributs, Knotens oder Elements zugeordnet. Dieses Standardverhalten kann durch das Anfordern eines elementzentrierten XML-Codes mithilfe der ELEMENTS-Direktive und der Angabe von XSINIL zum Hinzufügen von Elementen für NULL-Werte überschrieben werden, wie in der folgenden Abfrage gezeigt:  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Im Folgenden wird das Ergebnis gezeigt. Beachten Sie, dass das <`Middle`>-Element abwesend sein wird, wenn XSINIL nicht angegeben wird.  
  
```  
<row xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
