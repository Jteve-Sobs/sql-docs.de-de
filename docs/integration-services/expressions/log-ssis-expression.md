---
title: LOG (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 54de500bc6cda16126fcf7b680c7443f947301e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027440"
---
# <a name="log-ssis-expression"></a>LOG (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt den Logarithmus eines numerischen Ausdrucks zur Basis 10 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck, der ungleich 0 oder nicht negativ ist.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Der *numerische Ausdruck* wird in den DT_R8-Datentyp umgewandelt, bevor der Logarithmus berechnet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Falls *numeric_expression* zu 0 (null) oder einem negativen Wert ausgewertet wird, wird als Ergebnis NULL zurückgegeben.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein numerisches Literal verwendet. Die Funktion gibt den Wert 1.988291341907488 zurück.  
  
```  
LOG(97.34)  
```  
  
 In diesem Beispiel wird die **Length**-Spalte verwendet. Falls der Spaltenwert 101.24 ist, gibt die Funktion 2.005352136486217 zurück.  
  
```  
LOG(Length)   
```  
  
 In diesem Beispiel wird die **Length**-Variable verwendet. Die Variable muss einen numerischen Datentyp aufweisen, oder der Ausdruck muss eine explizite Umwandlung in einen numerischen [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Datentyp einschließen. Falls **Length** gleich 234.567 ist, gibt die Funktion 2.370266913465859 zurück.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [EXP &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/exp-ssis-expression.md)   
 [LN &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/ln-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
