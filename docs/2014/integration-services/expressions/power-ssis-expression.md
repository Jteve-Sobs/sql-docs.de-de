---
title: POWER (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3d25801b7cc7f6282ebc8cf7b1ce7839159312dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897411"
---
# <a name="power-ssis-expression"></a>POWER (SSIS-Ausdruck)
  Gibt das Ergebnis eines in eine Potenz erhobenen numerischen Ausdrucks zurück. Der power-Parameter muss zu einer ganzen Zahl ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
 *power*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Hinweise  
 Die Argumente *numeric_expression* und *power* werden in den „DT_R8“-Datentyp umgewandelt, bevor der Potenzwert berechnet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 Falls *numeric_expression* in 0 (null) ausgewertet wird und *power* negativ ist, gibt die Ausdrucksauswertung einen Fehler zurück und legt das zurückgegebene Ergebnis auf NULL fest.  
  
 Falls *numeric_expression* oder *power* in unbestimmte Ergebnisse ausgewertet werden, wird als Ergebnis NULL zurückgegeben.  
  
 Das *power* -Argument kann eine Bruchzahl sein. Sie können z. B. 0.5 als Potenzwert verwenden.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein numerisches Literal verwendet. Die Funktion potenziert 4 mit 3 und gibt 64 zurück.  
  
```  
POWER(4,3)  
```  
  
 In diesem Beispiel wird die **Length** -Spalte und die **DimensionCount** -Variable verwendet. Falls **Length** gleich 8 ist und **DimensionCount** gleich 2, wird als Ergebnis 64 zurückgegeben.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
