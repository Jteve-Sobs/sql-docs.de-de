---
title: IsTrainingCase (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4a2dad29a3a1b0ca5fdae12b11b190fd7e59380f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937689"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt an, ob ein Fall als Trainingsfall für ein bestimmtes Data Mining-Modell oder eine bestimmte Data Mining-Struktur verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Ergebnistyp  
 Gibt **"true"** ist der Fall ein Teil des trainingsdatasets; andernfalls **"false"** .  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie eine Miningstruktur und ein damit verknüpftes Miningmodell mit dem Data Mining-Assistenten erstellen, werden standardmäßig 30 Prozent der Fälle zur Verwendung als Testdataset zurückgehalten. Die verbleibenden Fälle in der angegebenen Datenquelle werden zum Trainieren des Modells verwendet. Wenn Sie das Miningmodell jedoch mithilfe von DMX-Anweisungen (Data Mining-Erweiterungen) erstellen, werden standardmäßig alle Daten zum Trainieren des Modells verwendet, und es wird kein Testsatz erstellt. Damit ein Testdataset erstellt werden kann, müssen Sie die Parameter der WITH HOLDOUT-Klausel festlegen.  
  
 Sie können ermitteln, ob die Daten in einer bestimmten Miningstruktur in Test- und Trainingssätze geteilt wurden, indem Sie den Wert der Eigenschaften von <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> und <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> anzeigen.  
  
> [!NOTE]  
>  Für das Modell muss Drillthrough aktiviert werden, wenn Sie die IsTrainingCase oder IsTestCase-Funktion zu verwenden, um die Details der Fälle im Modell zurückgeben möchten. Weitere Informationen finden Sie unter [Aktivieren von Drillthrough für ein Miningmodell](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Um Fälle zurückzugeben, die Teil des testdatasets sind, verwenden Sie die Funktion [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das clustering Datamining-Modell aus der targeted mailing-Szenario, in der [Lernprogramm zu Data Mining](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Die Abfrage gibt nur die Fälle zurück, die zum Trainieren des Miningmodells verwendet wurden. Darüber hinaus werden die Trainingsfälle auf Kunden unter 40 eingeschränkt.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Weitere Beispiele zum Abfragen von Fällen in Datamining verwendete finden Sie unter [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md) und [SELECT FROM &#60;Struktur&#62;. Fällen](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Trainings- und Testdatasets](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Data Mining-Abfragen](../analysis-services/data-mining/data-mining-queries.md)  
  
  
