---
title: Count (Tupel) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3775af63181489b982778d40ddd69ebc12872271
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285034"
---
# <a name="count-tuple-mdx"></a>Count (Tupel) (MDX)


  Gibt die Anzahl der Dimensionen in einem Tupel zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Gibt die Anzahl der Dimensionen in einem Tupel zurück.  
  
## <a name="example"></a>Beispiel  
 Das berechnete Measure in der folgenden Abfrage gibt den Wert 2 zurück, der die Anzahl der Hierarchien im Tupel `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])` wiedergibt:  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzahl &#40;Dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Anzahl &#40;Hierarchieebenen&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
