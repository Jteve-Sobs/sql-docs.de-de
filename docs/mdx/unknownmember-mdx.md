---
title: UnknownMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84eda6f42b674ebde8793605816f98e82af350d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63065043"
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)


  Gibt das einer Ebene oder einem Element zugeordnete unbekannte Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Analysis Services erstellt ein unbekanntes Element einer Hierarchie Faktentabellendaten zuordnen, wenn die Hierarchie nicht bekannt ist. Das unbekannte Element kann sich auf einer der folgenden Ebenen befinden:  
  
-   Auf der obersten Ebene für nicht aggregierte Attributhierarchien.  
  
-   Klicken Sie auf der ersten Ebene unter der **alle** -Ebene für natürliche Hierarchien.  
  
-   Auf jeder Ebene für unnatürliche Hierarchien.  
  
 Wenn ein Elementausdruck angegeben ist, die **UnknownMember** Funktion gibt das unbekannte untergeordnete Element des angegebenen Elements zurück. Wenn das angegebene Element nicht vorhanden ist, gibt die Funktion den Wert NULL zurück.  
  
 Wenn ein Hierarchieausdruck angegeben wird, die **UnknownMember** Funktion gibt das unbekannte Element auf der obersten Ebene zurück, falls vorhanden.  
  
 Wenn das unbekannte Element nicht, auf die Ebene oder einem Element vorhanden ist, das **UnknownMember** -Funktion erstellt ein null-Element.  
  
> [!NOTE]  
>  Wenn kein unbekanntes Element in der Hierarchie oder für das Element vorhanden ist, wird ein Fehler generiert.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das unbekannte Element für das All Products-Element in der Product-Attributhierarchie für alle Elemente der Measures-Dimension zurückgegeben.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das unbekannte Element für die Product Categories-Hierarchie für alle Elemente der Measures-Dimension zurückgegeben.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
