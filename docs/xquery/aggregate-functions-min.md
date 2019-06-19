---
title: Min-Funktion (XQuery) | Microsoft-Dokumentation
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
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69381eb0ffdd3638079d824d8d4c150563375a6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046964"
---
# <a name="aggregate-functions---min"></a>Aggregatfunktionen – min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt aus einer Sequenz atomarer Werte *$arg*, das eine Element, dessen Wert kleiner als alle anderen Elemente ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Sequenz der Elemente, aus denen der Mindestwert zurückgegeben wird.  
  
## <a name="remarks"></a>Hinweise  
 Alle Typen der atomaren Werte, die übergeben werden **min()** müssen Untertypen des gleichen Basistyps sein. Basistypen, die akzeptiert werden, sind die Typen, unterstützen die **Gt** Vorgang. Diese Typen sind z. B. die drei integrierten numerischen Basistypen, die date/time-Basistypen, xs:string, xs:boolean und xdt:untypedAtomic. Werte des Typs xdt:untypedAtomic werden in xs:double umgewandelt. Wenn eine Mischung dieser Typen ist, oder wenn andere Werte anderer Typen übergeben werden, wird ein statischer Fehler ausgelöst.  
  
 Das Ergebnis des **min()** erhält den Basistyp der übergebenen Typen, z. B. xs: Double im Fall von xdt: UntypedAtomic. Wenn die Eingabe statisch leer ist, wird dies angegeben und ein statischer Fehler zurückgegeben.  
  
 Die **min()** Funktion gibt den Wert 1 zurück, in der Sequenz, die kleiner als alle anderen Werte in der Eingabesequenz ist. Für xs:string-Werte wird die Unicode-Codepunkt-Standardsortierung verwendet. Wenn ein xdt: UntypedAtomic-Wert in xs: Double umgewandelt werden kann, wird der Wert in der Eingabesequenz, ignoriert *$arg*. Wenn die Eingabe eine dynamisch berechnete leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. Verwenden der min()-Funktion von XQuery zum Bestimmen der Arbeitsplatzstandorte, die die wenigsten Arbeitsstunden aufweisen  
 Die folgende Abfrage ruft alle Arbeitsplatzstandorte im Fertigungsprozess für das Produktmodell (ProductModelID=7) ab, die die wenigsten Arbeitsstunden aufweisen. Im Allgemeinen wird, wie im folgenden Beispiel gezeigt, ein einziger Arbeitsplatzstandort zurückgegeben. Wenn mehrere Standorte eine gleiche Anzahl von Mindestarbeitsstunden aufweisen, werden alle diese Standorte zurückgegeben.  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  for   $Location in /AWMI:root/AWMI:Location  
  where $Location/@LaborHours =  
          min( /AWMI:root/AWMI:Location/@LaborHours )  
return  
  <Location WCID=     "{ $Location/@LocationID }"   
              LaborHrs= "{ $Location/@LaborHours }" />  
  ') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die **Namespace** -Schlüsselwort im XQuery-Prolog definiert ein Namespacepräfix. Dieses Präfix wird anschließend im XQuery-Abfragetext verwendet.  
  
 Hauptteil der XQuery konstruiert die XML-Daten, die eine \<Location >-Element mit wcid-ATTRIBUT und **LaborHrs** Attribute.  
  
-   Die Abfrage ruft außerdem die ProductModelID- und Namenswerte ab.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **min()** -Funktion ordnet alle ganzzahligen Werte xs: Decimal.  
  
-   Die **min()** -Funktion für Werte des Typs xs: Duration nicht unterstützt.  
  
-   Sequenzen, die Typen über Basistypbegrenzungen hinweg mischen, werden nicht unterstützt.  
  
-   Die Option syntactic, die eine Sortierung bereitstellt, wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
