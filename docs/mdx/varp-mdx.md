---
title: VarP (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc1e6276de9a03af9800b9e242d54130c4241732
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251489"
---
# <a name="varp-mdx"></a>VarP (MDX)


  Gibt die Auffüllungsvarianz eines numerischen Ausdrucks, ausgewertet über einer Menge mithilfe der Formel für die unausgewogene Auffüllung (geteilt durch *n*-1).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **VarP** Funktion gibt die unausgewogene Varianz eines angegebenen numerischen Ausdrucks, ausgewertet über einer angegebenen Menge zurück.  
  
 Die **VarP** -Funktion verwendet die unausgewogene Auffüllung Formel, während die [Var](../mdx/var-mdx.md) -Funktion verwendet die Formel für die ausgewogene Auffüllung berechnet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
