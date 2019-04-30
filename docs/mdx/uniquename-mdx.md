---
title: UniqueName (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41642dc8bcaed03faaffdf9a16d8fc465aa2d360
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63306483"
---
# <a name="uniquename-mdx"></a>UniqueName (MDX)


  Gibt den eindeutigen Namen einer angegebenen Dimension, Hierarchie, Ebene oder eines angegebenen Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Dimension expression syntax  
Dimension_Expression.UniqueName  
  
Hierarchy expression syntax  
Hierarchy_Expression.UniqueName  
  
Level expression syntax  
Level_Expression.UniqueName  
  
Member expression syntax  
Member_Expression.UniqueName  
```  
  
## <a name="arguments"></a>Argumente  
 *Dimension_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der zu einer Dimension aufgelöst wird.  
  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **UniqueName** Funktionsergebnis ist der eindeutige Name des Objekts, nicht den Namen, die zurückgegeben werden, indem die [Namen](../mdx/name-mdx.md) Funktion. Der zurückgegebene Name enthält nicht den Namen des Cubes. Das zurückgegebene Ergebnis hängt von den serverseitigen Einstellungen oder von der MDX Unique Name Style-Eigenschaft der Verbindungszeichenfolge ab.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Wert des eindeutigen Namens der Product-Dimension, der Product Categories-Hierarchie, der Subcategory-Ebene und des Bike Racks-Elements im Adventure Works-Cube zurückgegeben.  
  
```  
WITH MEMBER DimensionUniqueName   
   AS [Product].UniqueName  
MEMBER HierarchyUniqueName   
   AS [Product].[Product Categories].UniqueName  
MEMBER LevelUniqueName   
   AS [Product].[Product Categories].[Subcategory].UniqueName  
MEMBER MemberUniqueName   
   AS [Product].[Product Categories].[Subcategory].[Bike Racks]  
SELECT   
   {DimensionUniqueName  
   , HierarchyUniqueName  
   , LevelUniqueName  
   , MemberUniqueName }  
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
