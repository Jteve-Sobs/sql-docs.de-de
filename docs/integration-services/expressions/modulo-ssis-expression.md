---
title: (Modulo) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 855e96dbc95b7b6b76fce213524705b289bce42b
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58277539"
---
# <a name="modulo-ssis-expression"></a>(Modulo) (SSIS-Ausdrücke)
  Stellt den ganzzahligen Rest einer Division des ersten numerischen Ausdrucks durch den zweiten bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a>Argumente  
 *dividend*  
 Der zu dividierende numerische Ausdruck. *dividend* kann ein beliebiger numerischer Ausdruck sein. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Der numerische Ausdruck, durch den der Dividend geteilt werden soll. *divisor* kann ein beliebiger numerischer Ausdruck außer Null sein.  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Beide Ausdrücke müssen zu ganzzahligen Datentypen mit oder ohne Vorzeichen ausgewertet werden.  
  
 Wenn einer der Operanden NULL ist, ist das Ergebnis NULL.  
  
 Modulo Null ist nicht zulässig.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird der Teilungsrest von zwei numerischen Literalen berechnet. Das Ergebnis ist 3.  
  
```  
42 % 13  
```  
  
 In diesem Beispiel wird der Teilungsrest von der **SalesQuota** -Spalte und einem numerischen Literal berechnet.  
  
```  
SalesQuota % 12  
```  
  
 In diesem Beispiel wird der Teilungsrest von den beiden numerischen Variablen **Sales$** und **Month**berechnet. Die **Sales$** -Variable muss in eckige Klammern eingeschlossen werden, weil der Name das $-Zeichen enthält. Weitere Informationen finden Sie unter [Bezeichner &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
@[Sales$] % @Month  
```  
  
 In diesem Beispiel wird mithilfe des Modulo-Operators ermittelt, ob der Wert der **Value** -Variablen gerade oder ungerade ist, und mit dem Bedingungsoperator wird eine Zeichenfolge zur Beschreibung des Ergebnisses zurückgegeben. Weitere Informationen finden Sie unter [? : &#40;Bedingt, SSIS-Ausdruck&#41;](../../integration-services/expressions/conditional-ssis-expression.md).  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
