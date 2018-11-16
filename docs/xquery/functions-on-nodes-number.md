---
title: Number-Funktion (XQuery) | Microsoft-Dokumentation
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
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 44ab042814b95886faa9f632fb58d7a809c9e458
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666959"
---
# <a name="functions-on-nodes---number"></a>Funktionen für Knoten – number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den numerischen Wert des Knotens, der angegebenen *$arg*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Knoten, dessen Wert als Zahl zurückgegeben wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *$arg* ist nicht angegeben ist, wird der numerische Wert des Kontextknotens aus, konvertiert in einen Double-Wert zurückgegeben. In SQL Server **Fn:Number()** ohne Argument nur im Kontext eines kontextabhängigen Prädikats verwendet werden kann. Insbesondere kann die Funktion nur innerhalb von Klammern ([ ]) verwendet werden. Beispielsweise gibt der folgende Ausdruck das <`ROOT`>-Element zurück.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Wenn der Wert des Knotens keine gültige lexikalische Darstellung eines numerischen simple-Typs, gemäß **XML Schema Part 2: Datatypes, W3C-Empfehlung**, gibt die Funktion eine leere Sequenz zurück. NaN wird nicht unterstützt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen in verschiedenen gespeicherten **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. Verwenden der number()-Funktion von XQuery zum Abrufen des numerischen Werts eines Attributs  
 Die folgende Abfrage ruft den numerischen Wert des LotSize-Attributs aus dem ersten Arbeitsplatzstandort im Fertigungsvorgang von Produktmodell 7 ab.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die **number()** Funktion ist nicht erforderlich, wie durch die Abfrage für die **LotSizeA** Attribut. Es handelt sich dabei um eine XPath 1.0-Funktion, die hauptsächlich aus Gründen der Abwärtskompatibilität enthalten ist.  
  
-   Die XQuery für **LotSizeB** gibt an, die Number-Funktion und ist redundant.  
  
-   Die Abfrage für **LotSizeD** veranschaulicht die Verwendung eines Number-Werts in einer arithmetischen Operation.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **number()** -Funktion nimmt nur Knoten. Sie nimmt keine atomaren Werte an.  
  
-   Wenn Werte als Zahl zurückgegeben werden, können die **number()** Funktion gibt die leere Sequenz statt NaN zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
