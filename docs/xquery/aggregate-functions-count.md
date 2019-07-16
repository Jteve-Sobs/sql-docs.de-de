---
title: Count-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:count function
- count function [XQuery]
ms.assetid: a9f7131f-23e1-4d4d-a36c-180447543926
author: rothja
ms.author: jroth
ms.openlocfilehash: a359251dbb2bd2a2685e5d9fb91d5c1603950c25
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986303"
---
# <a name="aggregate-functions---count"></a>Aggregatfunktionen – count
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Anzahl der enthaltenen Elemente in der angegebenen Sequenz *$arg*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:count($arg as item()*) as xs:integer  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Zu zählende Elemente.  
  
## <a name="remarks"></a>Hinweise  
 Gibt 0 zurück, wenn *$arg* eine leere Sequenz.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-count-xquery-function-to-count-the-number-of-work-center-locations-in-the-manufacturing-of-a-product-model"></a>A. Verwenden der count()-Funktion von XQuery zum Zählen der Arbeitsplatzstandorte im Fertigungsprozess eines Produktmodells  
 Die folgende Abfrage zählt die Anzahl der Arbeitsplatzstandorte im Fertigungsprozess eines Produktmodells (ProductModelID=7).  
  
```  
SELECT Production.ProductModel.ProductModelID,   
       Production.ProductModel.Name,   
       Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations>  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die **Namespace** -Schlüsselwort in [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) definiert ein Namespacepräfix. Dieses Präfix wird anschließend im Hauptteil der XQuery verwendet.  
  
-   Die Abfrage erstellt XML mit der <`NoOfWorkStations`> Element.  
  
-   Die **count()** -Funktion im Hauptteil der XQuery zählt die Anzahl der <`Location`> Elemente.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID   Name                 WorkCtrCount       
-------------- ---------------------------------------------------  
7             HL Touring Frame  <NoOfWorkStations>6</NoOfWorkStations>     
```  
  
 Sie können den XML-Code auch so konstruieren, dass er die ID und den Namen des Produktmodells enthält, wie in der folgenden Abfrage gezeigt:  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations  
             ProductModelID= "{ sql:column("Production.ProductModel.ProductModelID") }"   
             ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID= 7  
```  
  
 Dies ist das Ergebnis:  
  
```  
<NoOfWorkStations ProductModelID="7"   
                  ProductModelName="HL Touring Frame">6</NoOfWorkStations>  
```  
  
 Anstelle von XML können Sie die Werte auch so zurückgeben, dass sie nicht vom Typ XML sind, wie in der folgenden Abfrage gezeigt. Die Abfrage verwendet die [Value()-Methode (Xml-Datentyp)](../t-sql/xml/value-method-xml-data-type.md) um die Anzahl der Arbeitsaufgaben-Center-Speicherort abzurufen.  
  
```  
SELECT  ProductModelID,   
        Name,   
        Instructions.value('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
           count(/AWMI:root/AWMI:Location)', 'int' ) as WorkCtrCount  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID    Name            WorkCtrCount  
-------------- ---------------------------------  
7              HL Touring Frame        6     
```  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
