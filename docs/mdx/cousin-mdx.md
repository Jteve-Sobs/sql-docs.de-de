---
title: Cousin (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8a98d496467e2fd75924b0067257f192c79cdf6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047250"
---
# <a name="cousin-mdx"></a>Cousin (MDX)


  Gibt das untergeordnete Element mit derselben relativen Position unter einem übergeordneten Element wie das angegebene untergeordnete Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Ancestor_Member_Expression*  
 Ein gültiger MDX-Elementausdruck (Multidimensional Expressions), der ein Vorgängerelement zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion bezieht sich auf die Reihenfolge und Position von Elementen in Ebenen. Wenn zwei Hierarchien gegeben sind, von denen die eine vier Ebenen und die andere fünf Ebenen aufweist, entspricht der Cousin der dritten Ebene der ersten Hierarchie der dritten Ebene der zweiten Hierarchie.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Cousin des vierten Quartals des Geschäftsjahres 2002 basierend auf seinem Vorgänger auf der Year-Ebene im Geschäftsjahr 2003 abgerufen. Der abgerufene Cousin ist das vierte Quartal des Geschäftsjahres 2003.  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird der Cousin des Monats Juli des Geschäftsjahres 2002 basierend auf seinem Vorgänger auf der Quarter-Ebene im zweiten Quartal des Geschäftsjahres 2004 abgerufen. Der abgerufene Cousin ist der Monat Oktober 2003.  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
