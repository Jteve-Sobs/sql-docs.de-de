---
title: Inhaltstypen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ec3b618e83fff2915ec7d1dac0f25ea82c60912c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071018"
---
# <a name="content-types-dmx"></a>Inhaltstypen (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Data Mining-Algorithmen benötigen über den Datentyp hinausgehende, zusätzliche Informationen, damit sie richtig ausgewertet werden können, z. B. den Inhaltstyp. Der Inhaltstyp unterstützt dabei, für den jeweiligen Algorithmus zu ermitteln, wie die Daten in der Spalte verarbeitet werden sollen.  
  
 Jeder Algorithmus unterstützt bestimmte Inhaltstypen. Beispielsweise kann der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus keine kontinuierlichen Spalten verwenden. Wenn Sie eine kontinuierliche Spalte in einem [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Modell verwenden möchten, müssen Sie die Daten in der Spalte diskretisieren. Für einige Algorithmen sind bestimmte Inhaltstypen erforderlich, damit sie richtig funktionieren. Beispielsweise ist für den [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus eine Schlüsselzeitspalte erforderlich, um die Zeitspanne zu kennzeichnen, in der die Daten gesammelt wurden.  
  
 Eine vollständige Beschreibung des Inhalts Datentypen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt, finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](../analysis-services/data-mining/content-types-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
