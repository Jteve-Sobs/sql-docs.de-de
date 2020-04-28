---
title: CEILING-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
author: rothja
ms.author: jroth
ms.openlocfilehash: fe18f488b83c1a8c9236c642751c1dc80bfe7e6c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946579"
---
# <a name="numeric-values-functions---ceiling"></a>Funktionen für numerische Werte – ceiling 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die kleinste Anzahl ohne Stellen hinter dem Dezimalpunkt zurück, die nicht geringer ist als der Wert des Funktionsarguments. Wenn das Argument eine leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Anzahl, auf die die Funktion angewendet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Typ *$arg* einer der drei numerischen Basis Typen ( **xs: float**, **xs: Double**oder **xs: Decimal**) ist, ist der Rückgabetyp identisch mit dem *$arg* Typ.  
  
 Wenn der Typ *$arg* ein Typ ist, der von einem der numerischen Typen abgeleitet ist, ist der Rückgabetyp der numerische Basistyp.  
  
 Wenn die Eingabe für die FN: Floor-, FN: ceiling-oder fn: Round-Funktionen **xdt: untypedAtomic**ist, wird Sie implizit in **xs: Double**umgewandelt.  
  
 Alle anderen Typen führen zum Generieren eines statischen Fehlers.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Verwenden der XQuery-Funktion ceiling()  
 Für Produktmodell 7 gibt die Abfrage eine Liste der Arbeitsplatzstandorte im Produktionsprozess des Produktmodells zurück. Für jeden einzelnen Arbeitsplatzstandort gibt die Abfrage die Standortkennung, die Arbeitsstunden sowie die Losgröße zurück, sofern diese dokumentiert ist. Die Abfrage verwendet die **Ceiling** -Funktion, um die Arbeitsstunden als Werte des Typs " **Decimal**" zurückzugeben.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
     for $i in /AWMI:root/AWMI:Location  
     return   
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ ceiling($i/@LaborHours) }" >  
                    {   
                      $i/@LotSize  
                    }    
       </Location>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Das AWMI-Namespacepräfix steht für Adventure Works Manufacturing Instructions. Dieses Präfix verweist auf denselben Namespace, der im abgefragten Dokument verwendet wird.  
  
-   Die **Anweisungen** sind eine Spalte vom Typ **XML** . Daher wird die [Query ()-Methode (XML-Datentyp)](../t-sql/xml/query-method-xml-data-type.md) zum Angeben von XQuery verwendet. Die XQuery-Anweisung wird als Argument der query-Methode angegeben.  
  
-   **für... Return** ist ein Schleifen Konstrukt. In der Abfrage identifiziert die **for** -Schleife eine Liste von \<Speicherort> Elementen. Für jeden Arbeitsplatz Standort beschreibt die **Return** -Anweisung in der **for** -Schleife den zu generierenden XML-Code:  
  
    -   Ein \<Speicherort> Element mit den Attributen LocationID und laborstd. Der entsprechende Ausdruck in den geschweiften Klammern ({ }) ruft die erforderlichen Werte aus dem Dokument ab.  
  
    -   Der {$i/@LotSize }-Ausdruck ruft das LotSize-Attribut aus dem Dokument ab, falls vorhanden.  
  
    -   Dies ist das Ergebnis:  
  
```  
ProductModelID Result    
-------------- ------------------------------------------------------  
7      <Location LocationID="10" LaborHrs="3" LotSize="100"/>  
       <Location LocationID="20" LaborHrs="2" LotSize="1"/>     
       <Location LocationID="30" LaborHrs="1" LotSize="1"/>     
       <Location LocationID="45" LaborHrs="1" LotSize="20"/>  
       <Location LocationID="60" LaborHrs="3" LotSize="1"/>     
       <Location LocationID="60" LaborHrs="4" LotSize="1"/>  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **Ceiling ()** -Funktion ordnet alle ganzzahligen Werte xs: Decimal zu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Floor-Funktion &#40;XQuery-&#41;](../xquery/numeric-values-functions-floor.md)   
 [Round-Funktion &#40;XQuery-&#41;](../xquery/numeric-values-functions-round.md)  
  
  
