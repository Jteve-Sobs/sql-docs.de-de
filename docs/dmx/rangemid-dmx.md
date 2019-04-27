---
title: RangeMid (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e7daff41d09f1468f3819af5a8d2020719aebe9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659003"
---
# <a name="rangemid-dmx"></a>RangeMid (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Mittelpunkt des vorhergesagten Buckets zurück, der für eine diskretisierte Spalte ermittelt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RangeMid(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diskretisierte skalare Spalten.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Hinweise  
 Bei Verwendung mit [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), **RangeMin**, **RangeMid**, und **RangeMax**  Funktionen geben die tatsächlichen Begrenzungswerte des angegebenen Buckets zurück. Wenn Sie z. B. eine Vorhersage für eine diskretisierte Spalte ausführen, gibt die Abfrage die vorhergesagte Bucketnummer in der diskretisierten Spalte zurück. Die **RangeMin**, **RangeMid**, und **RangeMax** Funktionen beschreiben den Bucket, der die Vorhersage angibt. Wenn die **RangeMid** Funktion, die mit einer PREDICTION JOIN-Anweisung verwendet wird, den Verweis auf skalare Spalte kann nur diskrete vorhersagbare Spalten enthalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Mindest-, Höchst- und Durchschnittswerte für die kontinuierliche Spalte Yearly Income im TM Decision Tree-Miningmodell zurückgegeben.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
