---
title: Spaltenverteilungen [Datamining] | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a4969e3665aca4ed5aef588fa9595e96b846e98
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62715432"
---
# <a name="column-distributions-data-mining"></a>Spaltenverteilungen [Data Mining]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie Spaltenverteilungen in einer Miningstruktur definieren, um zu beeinflussen, wie Algorithmen die Daten in diesen Spalten verarbeiten, wenn Sie Miningmodelle erstellen. Für einige Algorithmen ist es hilfreich, vor dem Verarbeiten des Modells für jede kontinuierliche Spalte die Verteilung zu definieren, wenn für die Spalten bekannt ist, dass sie normal verteilte Werte enthalten. Wenn Sie die Verteilungen nicht definieren, liefern die sich ergebenden Miningmodelle möglicherweise ungenauere Vorhersagen, da die Algorithmen weniger Informationen zum Interpretieren der Daten haben.  
  
 Die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbaren Algorithmen unterstützen folgende Verteilungstypen:  
  
 `Normal`  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, das einer Normalverteilung folgt.  
  
 ![Histogramm mit normalverteilung](../media/normal-distribution.gif "Histogramm mit normalverteilung")  
  
 `Log Normal`  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, in dem die Kurve am oberen Ende einen gedehnten Verlauf und am unteren Ende  einen Schrägverlauf aufweist.  
  
 ![Histogramm mit protokollnormalverteilung](../media/log-normal-distribution.gif "Histogramm mit protokollnormalverteilung")  
  
 `Uniform`  
 Die Werte für die kontinuierliche Spalte bilden eine flache Kurve, in der alle Werte gleich wahrscheinlich sind.  
  
 ![Histogramm mit gleichverteilung](../media/uniform-distribution.gif "Histogramm mit gleichverteilung")  
  
 Weitere Informationen zu den von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Diskretisierungsmethoden &#40;Data Mining&#41;](discretization-methods-data-mining.md)   
 [Verteilungen &#40;DMX&#41;](/sql/dmx/distributions-dmx)   
 [Miningstrukturspalten](mining-structure-columns.md)  
  
  
