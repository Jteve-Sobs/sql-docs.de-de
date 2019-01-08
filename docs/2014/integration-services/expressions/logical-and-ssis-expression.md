---
title: '&amp;&amp; (Logisches AND) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0482db6754777c2501e776a166f4d385e86900a4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52780192"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (Logisches AND) (SSIS-Ausdruck)
  Führt eine logische AND-Operation aus. Der Ausdruck wird zu TRUE ausgewertet, falls alle Bedingungen TRUE sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression1, boolean_expression2*  
 Ein gültiger Ausdruck, der zu TRUE, FALSE oder NULL ausgewertet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle wird das Ergebnis des &&-Operators dargestellt.  
  
|Ergebnis|expression|expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden die Spalten **StandardCost** und **ListPrice** verwendet. In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **StandardCost** -Spalte kleiner als 300 und falls die **ListPrice** -Spalte größer als 500 ist.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 In diesem Beispiel werden die Variablen **SPrice** und **LPrice** anstelle von Literalen verwendet.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Siehe auch  
 [& &#40;Bitweises AND&#41; &#40;SSIS-Ausdruck&#41;](bitwise-and-ssis-expression.md)   
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
