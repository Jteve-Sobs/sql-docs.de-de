---
title: Verwenden von Elementausdrücken | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41ff63d47a62b9b83fb583c55ff2405638de22cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097114"
---
# <a name="using-member-expressions"></a>Verwenden von Elementausdrücken


  Ein Elementausdruck enthält einen Elementbezeichner, eine Elementfunktion oder einen Ausdruck, der in ein Element konvertiert werden kann.  
  
 Elementbezeichner können viele verschiedene Formate haben. Die einfachste Form eines Elementbezeichners besteht aus dem Namen des Elements. Zum Beispiel:  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 Falls es jedoch mehrere Elemente des gleichen Namens in unterschiedlichen Hierarchien gibt, gibt es keine Möglichkeit, zu bestimmen, welches Element die Abfrage zurückgibt. Zum Beispiel fordert die folgende Abfrage Daten für ein Element mit dem Namen [CY 2004] an. Die Abfrage wird erfolgreich ausgeführt, jedoch gibt es im Adventure Works-Cube mindestens sechs Elemente mit diesem Namen:  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 Deshalb ist die zuverlässigste Form von Elementbezeichnern der eindeutige Name des Elements, um ein spezifisches Element in einem Cube sicher zu identifizieren. Analyses Services kann auf unterschiedliche Weise eindeutige Namen generieren, ein eindeutiger Name setzt sich jedoch immer aus mindestens zwei Bezeichnern zusammen: dem Dimensionsnamen sowie dem Elementnamen oder dem Elementschlüssel. Ein eindeutiger Name hat folgendes Format:  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 Im Folgenden sind einige Beispiele für eindeutige Elementnamen aus dem Adventure Works-Cube aufgelistet:  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 Es gibt viele MDX-Funktionen, die Elemente zurückgeben. Eine vollständige Liste finden Sie unter [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Weitere Informationen zu Elementnamen und Elementschlüsseln finden Sie unter [arbeiten mit Elementen, Tupeln und Mengen &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
