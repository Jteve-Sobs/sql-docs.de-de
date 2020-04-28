---
title: Zeichen folgen Suche in XQuery | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Text in XML-Dokumenten durchsuchen, indem Sie ein Beispiel für die Zeichen folgen Suche in XQuery anzeigen.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- strings [SQL Server], search
- XML [SQL Server], searching text
- searches [SQL Server], XML documents
- XQuery, string search
ms.assetid: edc62024-4c4c-4970-b5fa-2e54a5aca631
author: rothja
ms.author: jroth
ms.openlocfilehash: 33f68a55cb627099150ec14941fe5de81de53fc8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388054"
---
# <a name="string-search-in-xquery"></a>Zeichenfolgensuche in XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Thema werden Beispielabfragen bereitgestellt, die zeigen, wie in XML-Dokumenten nach Text gesucht werden kann.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-find-feature-descriptions-that-contain-the-word-maintenance-in-the-product-catalog"></a>A. Suchen von Funktionsbeschreibungen mit dem Wort "maintenance" im Produktkatalog  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    for $f in /p1:ProductDescription/p1:Features/*  
     where contains(string($f), "maintenance")  
     return  
           $f ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 In der vorherigen Abfrage filtert `where` der im FLOWR-Ausdruck das Ergebnis des `for` Ausdrucks und gibt nur die Elemente zurück, die die **enthält ()** -Bedingung erfüllen.  
  
 Dies ist das Ergebnis:  
  
```  
<p1:Maintenance     
      xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
 <p1:NoOfYears>10</p1:NoOfYears>  
 <p1:Description>maintenance contact available through your   
               dealer or any AdventureWorks retail store.</p1:Description>  
</p1:Maintenance>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server der XML-Daten &#40;&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
