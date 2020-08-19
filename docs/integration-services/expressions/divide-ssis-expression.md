---
description: (Division) (SSIS-Ausdruck)
title: (Division) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 516d8705f38f3bdd7234f1975f5188d32f501efe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430602"
---
# <a name="divide-ssis-expression"></a>(Division) (SSIS-Ausdruck)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Dividiert den ersten numerischen Ausdruck durch den zweiten numerischen Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Argumente  
 *dividend*  
 Der zu dividierende numerische Ausdruck. *dividend* kann ein beliebiger numerischer Ausdruck sein. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Der numerische Ausdruck, durch den der Dividend geteilt werden soll. *divisor* kann ein beliebiger numerischer Ausdruck außer Null sein.  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn einer der Operanden NULL ist, ist das Ergebnis NULL.  
  
 Division durch Null ist nicht zulässig. Je nachdem, wie der *divisor* -Teilausdruck ausgewertet wird, wird einer der folgenden Fehler gemeldet:  
  
-   Falls der zu Null ausgewertete *divisor* -Teilausdruck eine Konstante ist, wird der Fehler zur Entwurfszeit angezeigt, und der Ausdruck kann deshalb nicht überprüft werden.  
  
-   Falls der zu Null ausgewertete *divisor* -Teilausdruck Variablen, aber keine Eingabespalten enthält, wird für die zugehörige Komponente bei der Überprüfung vor der Ausführung (die vor der Ausführung des Pakets erfolgt) ein Fehler gemeldet.  
  
-   Falls der zu 0 (null) ausgewertete *divisor* -Teilausdruck Eingabespalten enthält, wird der Fehler zur Laufzeit gemeldet und gemäß den Fehlerflussregeln der Datenflusskomponente behandelt.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden zwei numerische Literale dividiert.  
  
```  
25 / 5  
```  
  
 In diesem Beispiel werden Werte in der **ListPrice** -Spalte durch die Werte in der **StandardCost** -Spalte dividiert.  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
