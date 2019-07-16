---
title: MDX-Skripts Grundlagen (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9ca77b9c10f1dba24127e35e5fe55d7ffcdad3dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165848"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Grundlegendes zu MDX-Skripts (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]besteht ein MDX-Skript (Multidimensional Expressions) aus einem oder mehreren MDX-Ausdrücken oder -Anweisungen, die einen Cube mit Berechnungen auffüllen.  
  
 In einem MDX-Skript wird der Berechnungsprozess für einen Cube definiert. Ein MDX-Skript wird auch als Teil des Cubes selbst angesehen. Daher bewirkt ein Ändern eines MDX-Skripts, das einem Cube zugeordnet ist, dass der Berechnungsprozess für den Cube sofort geändert wird.  
  
 Um MDX-Skripts zu erstellen, können Sie den Cube-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]verwenden. Weitere Informationen finden Sie unter [Definieren von Zuweisungen und anderen Skriptbefehlen](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) und [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892)(Einführung in MDX-Skripts in Microsoft SQL Server 2005).  
  
 Informationen zu Leistungsproblemen im Zusammenhang mit MDX-Abfragen und -Berechnungen finden Sie im Abschnitt zur MDX-Optimierung im [SQL Server Analysis Services Performance Guide](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Grundlegendes MDX-Skript &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Beschreibt ausführlich das grundlegende MDX-Skript (samt dem MDX-Standardskript, das in jedem Cube bereitgestellt wird), und beschreibt, wie MDX-Skripts in einem Cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]im Grundsatz funktionieren.|  
|[Verwalten von Gültigkeitsbereich und Kontext &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Beschreibt, wie die [CALCULATE](../../../mdx/mdx-scripting-calculate.md) -Anweisung, die [SCOPE](../../../mdx/mdx-scripting-scope.md) -Anweisung und die [This](../../../mdx/this-mdx.md) -Funktion dazu verwendet werden, in einem MDX-Skript den Kontext und den Gültigkeitsbereich zu verwalten.|  
|[Verwenden von Variablen und Parametern &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Beschreibt, wie Variablen und Parameter in einem MDX-Skript verwendet werden.|  
|[Fehlerbehandlung &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Erläutert die Fehlerbehandlung innerhalb eines MDX-Skripts.|  
|[Unterstütztes MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Stellt eine Liste der MDX-Operatoren, -Anweisungen und -Funktionen bereit, die in einem MDX-Skript unterstützt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Sprachreferenz &#40;MDX&#41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  
