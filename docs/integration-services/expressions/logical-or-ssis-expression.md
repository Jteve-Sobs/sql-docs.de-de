---
title: '|| (Logisches OR) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 771dea6d044fc797c5fe8bcc4a04e61679794ecd
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290066"
---
# <a name="-logical-or-ssis-expression"></a>|| (Logisches OR) (SSIS-Ausdruck)
  Führt eine logische OR-Operation aus. Der Ausdruck wird zu TRUE ausgewertet, falls mindestens eine Bedingung TRUE ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression1, boolean_expression2*  
 Ein gültiger Ausdruck, der zu TRUE, FALSE oder NULL ausgewertet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 In der folgenden Tabelle wird das Ergebnis des ||-Operators dargestellt.  
  
|Ergebnis|expression|expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel werden die Spalten **StandardCost** und **ListPrice** verwendet. In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **StandardCost** -Spalte kleiner als 300 oder falls die **ListPrice** -Spalte größer als 500 ist.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 In diesem Beispiel werden die Variablen **SPrice** und **LPrice** anstelle numerischer Literale verwendet.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#124; &#40;Bitweises inklusives OR&#41; &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;Bitweises exklusives OR&#41; &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
