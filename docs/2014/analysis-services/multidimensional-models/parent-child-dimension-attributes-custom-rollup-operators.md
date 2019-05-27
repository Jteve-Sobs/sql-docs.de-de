---
title: Benutzerdefinierte Rollupoperatoren in über-und untergeordnete Dimensionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 20f25474b15ecf58c45383a8290bb13f956a5db8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66073460"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a>Benutzerdefinierte Rollupoperatoren in über- und untergeordneten Dimensionen
  Mit benutzerdefinierten Rollup-Operatoren können Sie auf einfache Weise steuern, wie Rollups von Elementwerten zu übergeordneten Werten in einer Hierarchie mit über- und untergeordneten Elementen ausgeführt werden. In einer Dimension mit einer Über-/Unterordnungsbeziehung geben Sie eine Spalte mit unären Operatoren an, die einen Rollup für alle nicht berechneten Elemente des übergeordneten Attributs angeben. Der unäre Operator wird immer dann auf die Elemente angewendet, wenn die Werte des übergeordneten Elements ausgewertet werden.  
  
 Die unären Operatoren werden in der Spalte gespeichert, die durch die `UnaryOperatorColumn`-Eigenschaft des übergeordneten Attributs definiert ist, und werden auf jedes Element des Attributs angewendet. Die durch diese Eigenschaft angegebene Spalte kann sich in der Dimensionstabelle oder in einer Tabelle befinden, die durch einen Fremdschlüssel in der Dimensionstabelle mit der Dimensionstabelle verknüpft ist.  
  
 Benutzerdefinierte Rollup-Operatoren stellen eine Funktionalität bereit, die der von benutzerdefinierten Elementformeln ähnelt, jedoch einfacher ist. Eine benutzerdefinierte Elementformel bestimmt mithilfe von MDX-Ausdrücken (Multidimensional Expressions), wie der Rollup für die Elemente ausgeführt wird. Im Gegensatz dazu bestimmt ein benutzerdefinierter Rollup-Operator mithilfe eines einfachen unären Operators, wie sich der Wert eines Elements auf das übergeordnete Element auswirkt. Benutzerdefinierte Elementformeln der vorherigen Ebene in einer Dimension überschreiben den benutzerdefinierten Rollup-Operator einer Ebene.  
  
## <a name="custom-rollup-precedence"></a>Rangfolge von benutzerdefinierten Rollup-Operatoren  
 Im Hinblick auf die Rangfolge überschreiben die benutzerdefinierten Rollup-Operatoren des Quellattributs für eine Ebene in einer Hierarchie die benutzerdefinierten Elementformeln der vorherigen Ebene Die benutzerdefinierten Elementformeln der vorhergehenden Ebene überschreiben jedoch die benutzerdefinierten Rollup-Operatoren einer Ebene.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von benutzerdefinierten Elementformeln](attribute-properties-define-custom-member-formulas.md)   
 [Unäre Operatoren in über- und untergeordneten Dimensionen](parent-child-dimension-attributes-unary-operators.md)  
  
  
