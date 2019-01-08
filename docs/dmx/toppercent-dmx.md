---
title: TopPercent (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6580599ed5c4c810a8b77369f850e9def2e90756
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527232"
---
# <a name="toppercent-dmx"></a>TopPercent (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **TopPercent** Funktion zurückgibt, in absteigender Rangreihenfolge die obersten Zeilen einer Tabelle, deren kumulativer Gesamtwert ist mindestens ein, angegebener Prozentsatz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TopPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein Ausdruck, der eine Tabelle, z. B. zurückgibt eine \<Tabelle Spaltenverweis >, oder eine Funktion, die eine Tabelle zurückgibt.  
  
## <a name="return-type"></a>Rückgabetyp  
 \<Tabellenausdruck >  
  
## <a name="remarks"></a>Hinweise  
 Die **TopPercent** Funktion gibt die obersten Zeilen zurück, in absteigender Rangreihenfolge entsprechend den ausgewerteten Wert des der \<rank Expression >-Arguments für jede Zeile, so, dass die Summe der der \<rank Expression > Werte sind mindestens die Prozentsatz sein muss, die angegeben wird die \<Prozent >-Argument. **TopPercent** die kleinste Anzahl von Elementen gibt mögliche zurück, denen den angegebenen Prozentwert erreicht.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel erstellt eine Vorhersageabfrage für das Association-Modell, das Sie erstellen, indem Sie mit der [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Um die Funktionsweise von TopPercent zu verstehen, ist es möglicherweise hilfreich, zunächst eine Vorhersageabfrage auszuführen, die lediglich die geschachtelte Tabelle zurückgibt.  
  
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
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
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
  
 Die TopPercent-Funktion verwendet die Ergebnisse dieser Abfrage und gibt den Zeilen mit den größten Werten ergeben, die den angegebenen Prozentsatz.  
  
```  
SELECT   
TopPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Das erste Argument für die TopPercent-Funktion ist der Name einer Tabellenspalte. In diesem Beispiel wird die geschachtelte Tabelle zurückgegeben, indem Sie die Predict-Funktion aufrufen und das INCLUDE_STATISTICS-Argument.  
  
 Das zweite Argument für die TopPercent-Funktion ist die Spalte in der geschachtelten Tabelle, die Sie zum Sortieren der Ergebnisse verwenden. In diesem Beispiel gibt die INCLUDE_STATISTICS-Option die Spalten $SUPPORT, $PROBABILTY und $ADJUSTED PROBABILITY zurück. In diesem Beispiel wird $SUPPORT verwendet, da diese Werte keine Bruchteile besitzen und daher leichter zu überprüfen sind.  
  
 Das dritte Argument für die TopPercent-Funktion gibt den Prozentsatz als Double-Wert. Geben Sie 50 ein, um die Zeilen für die obersten Produkte zu erhalten, die 50 Prozent der Gesamtunterstützung ergeben.  
  
 Beispielergebnisse:  
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,29...|0,25...|  
|Water Bottle|2866|0.19...|0,17...|  
|Patchkit|2113|0,14...|0.13...|  
|Mountain Tire Tube|1992|0.133...|0,12...|  
  
 **Beachten Sie** in diesem Beispiel wird nur bereitgestellt, um die Verwendung von TopPercent zu veranschaulichen. Je nach Größe des Datasets kann die Ausführung dieser Abfrage lange dauern.  
  
> [!WARNING]  
>  Die MDX-Funktionen für TOPPERCENT und BOTTOMPERCENT können unerwartete Ergebnisse generieren, wenn die Werte zur Berechnung des Prozentsatzes negative Zahlen enthalten. Dieses Verhalten wirkt sich nicht auf die DMX-Funktionen aus. Weitere Informationen finden Sie unter [BottomPercent &#40;MDX&#41;](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
