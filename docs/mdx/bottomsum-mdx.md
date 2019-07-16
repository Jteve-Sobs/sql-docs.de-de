---
title: BottomSum (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e49fc5a7ffd4c0adff38628a143ded695785e29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016890"
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)


  Sortiert eine angegebene Menge in aufsteigender Reihenfolge und gibt eine Menge von Tupeln mit den niedrigsten Werten zurück, deren Summe kleiner oder gleich einem angegebenen Wert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Wert*  
 Ein gültiger numerischer Ausdruck, der den Wert angibt, mit dem die Tupel verglichen werden.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **BottomSum** -Funktion berechnet die Summe des angegebenen Measures, ausgewertet über einer angegebenen Menge, die Menge in aufsteigender Reihenfolge sortieren. Anschließend gibt die Funktion die Elemente mit den niedrigsten Werten zurück, deren Gesamtwert des angegebenen numerischen Ausdrucks mindestens dem angegebenen Wert (Summe) entspricht. Diese Funktion gibt die kleinste Teilmenge einer Menge zurück, deren kumulativer Gesamtwert mindestens dem angegebenen Wert entspricht. Die zurückgegebenen Elemente werden der Größe nach aufsteigend sortiert.  
  
> [!IMPORTANT]  
>  Die **BottomSum** ordnungsgemäß verwendet werden, wie z. B. die [TopSum](../mdx/topsum-mdx.md) funktionieren, immer die Hierarchie unterbrochen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird für die Bike-Kategorie die kleinste Menge der Elemente der City-Ebene in der Geography-Hierarchie in der Geography-Dimension für das Geschäftsjahr 2003 zurückgegeben, deren kumulativer Gesamtwert bezüglich des Reseller Sales Amount-Measures mindestens einer Summe von 50.000 entspricht (beginnend mit den Elementen dieser Menge, die den geringsten Umsatz aufweisen):  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
