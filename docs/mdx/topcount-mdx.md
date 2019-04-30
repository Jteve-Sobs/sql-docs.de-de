---
title: TopCount (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fa8edcf8af510a41affdcbcc9924edf69cf4c220
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228048"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


  Sortiert eine Menge in absteigender Reihenfolge und gibt die angegebene Anzahl von Elementen mit den höchsten Werten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, die **TopCount** sortiert in absteigender Reihenfolge der Tupel in der Menge, die von der angegebenen Menge nach dem angegebenen numerischen Ausdrucks, Wert angegeben wird, ausgewertet über der angegebenen Funktion Legen Sie. Nach dem Sortieren der Menge der **TopCount** Funktion gibt dann die angegebene Anzahl von Tupeln mit dem höchsten Wert zurück.  
  
> [!IMPORTANT]  
>  Wie die [BottomCount](../mdx/bottomcount-mdx.md) -Funktion, die **TopCount** Funktion immer die Hierarchie unterbrochen.  
  
 Wenn ein numerischer Ausdruck nicht angegeben wird, die Funktion gibt die Menge der Elemente in natürlicher Reihenfolge ohne Sortierung, verhält, wie die [Head (MDX)](../mdx/head-mdx.md) Funktion.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die ersten 10 Daten nach Internetverkaufsbetrag zurück:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel werden für die Bike-Kategorie die ersten fünf Elemente in der Menge der Elemente zurückgegeben, die alle Kombinationen von Elementen der City-Ebene in der Geography-Hierarchie in der Geography-Dimension sowie alle Geschäftsjahre aus der Fiscal-Hierarchie der Date-Dimension enthält, geordnet nach dem Reseller Sales Amount-Measure (beginnend mit den Elementen dieser Menge, die den höchsten Umsatz aufweisen).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
