---
title: = (Gleich) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1fac06690d811c3ae3d4b00a82ad9088b2df4aae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690925"
---
# <a name="-equal-to-mdx"></a>= (Ist gleich) (MDX)


  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) gleich dem Wert eines anderen MDX-Ausdrucks ist.  
  
> [!NOTE]  
>  Um Objekte zu vergleichen, verwenden die [IS &#40;MDX&#41; ](../mdx/is-mdx.md) Operator. Verwenden Sie z. B. den IS-Operator, um zu prüfen, ob das aktuelle Element auf einer Abfrageachse ein spezifisches Element ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **"true"** , wenn der Wert des ersten Parameters gleich dem Wert des zweiten Parameters ist.  
  
-   **"false"** , wenn der Wert des ersten Parameters nicht gleich dem Wert des zweiten Parameters ist.  
  
-   **"true"** Wenn beide Parameter null ist, oder einen Parameter null ist und die anderen Parameter 0 ist gleich.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage enthält Beispiele für diese Bedingungen:  
  
 `With`  
  
 `--Returns true`  
  
 `Member [Measures].bool1 as 1=1`  
  
 `--Returns false`  
  
 `Member [Measures].bool2 as 1=0`  
  
 `--Returns true`  
  
 `Member [Measures].bool3 as null=null`  
  
 `--Returns true`  
  
 `Member [Measures].bool4 as 0=null`  
  
 `--Returns false`  
  
 `Member [Measures].bool5 as 1=null`  
  
 `Select {[Measures].bool1,[Measures].bool2,[Measures].bool3,[Measures].bool4,[Measures].bool5}`  
  
 `On 0`  
  
 `From [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
