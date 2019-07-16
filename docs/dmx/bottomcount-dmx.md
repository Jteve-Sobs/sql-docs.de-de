---
title: BottomCount-Funktion (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a7874168f5f3e6ebededd2ce75f5f762f7fbd1e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022571"
---
# <a name="bottomcount-dmx"></a>BottomCount (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die angegebene Anzahl von untersten Zeilen in der durch einen Ausdruck angegebenen aufsteigenden Rangreihenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein Ausdruck, der eine Tabelle, z. B. zurückgibt eine \<Tabelle Spaltenverweis >, oder eine Funktion, die eine Tabelle zurückgibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Tabellenausdruck >  
  
## <a name="remarks"></a>Hinweise  
 Der Wert, der vom bereitgestellt wird die \<rank Expression > Argument legt die aufsteigende Rangreihenfolge für die Zeilen, die im bereitgestellt werden die \<Tabellenausdruck > Argument und der Anzahl von untersten Zeilen, die im angegebenen die \<Count >-Argument zurückgegeben wird.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel erstellt eine Vorhersageabfrage für das Association-Modell, das Sie erstellen, indem Sie mit der [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Um zu verstehen, wie die BottomCount-Funktion funktioniert, ist es möglicherweise hilfreich, zunächst eine Vorhersageabfrage auszuführen, die lediglich die geschachtelte Tabelle zurückgibt.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  In diesem Beispiel enthält der als Eingabe bereitgestellte Wert ein einzelnes Anführungszeichen und muss daher mit Escapezeichen versehen werden, indem ihm ein weiteres einzelnes Anführungszeichen vorangestellt wird. Wenn Sie über die Syntax zum Einfügen von Escapezeichen nicht sicher sind, können Sie den Generator für Vorhersageabfragen verwenden, um die Abfrage zu erstellen. Wenn Sie den Wert aus der Dropdownliste auswählen, wird das erforderliche Escapezeichen automatisch eingefügt. Weitere Informationen finden Sie unter [erstellen Sie eine Singleton-Abfrage im Data Mining-Designer](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md).  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patchkit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Fender Set – Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 Die BottomCount-Funktion verwendet die Ergebnisse dieser Abfrage und gibt die Zeilen mit kleinsten Werten ergeben, die den angegebenen Prozentsatz.  
  
```  
SELECT   
BottomCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument für die BottomCount-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die geschachtelte Tabelle zurückgegeben, indem Sie die Predict-Funktion aufrufen und das INCLUDE_STATISTICS-Argument.  
  
 Das zweite Argument für die BottomCount-Funktion ist die Spalte in der geschachtelten Tabelle, die Sie zum Sortieren der Ergebnisse verwenden. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $SUPPORT verwendet, da diese Werte keine Bruchteile besitzen und daher leichter zu überprüfen sind.  
  
 Das dritte Argument für die BottomCount-Funktion gibt die Anzahl der Zeilen an. Um die drei Zeilen mit dem niedrigsten Rangfolgenwert sortiert nach $SUPPORT abzurufen, geben Sie 3 ein.  
  
 Beispielergebnisse:  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Fender Set – Mountain|1415|0.095100477|0.090718432|  
  
 **Beachten Sie** in diesem Beispiel wird nur bereitgestellt, um die Verwendung der BottomCount-Funktion zu veranschaulichen. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)   
 [BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)   
 [TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)  
  
  
