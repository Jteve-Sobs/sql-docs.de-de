---
title: Vergleichsoperatoren (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fcbfb95070783db002d34870e5508df5322210d7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008202"
---
# <a name="operators---comparison"></a>Operatoren – vergleichend
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sie können Vergleichsoperatoren mit skalaren Daten in einem Data Mining Extensions (DMX) Ausdruck [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vergleichsoperatoren ergeben einen Wert vom booleschen Datentyp. Sie geben abhängig vom Ergebnis der getesteten Bedingung TRUE oder FALSE zurück.  
  
 In der folgenden Tabelle sind die Vergleichsoperatoren aufgeführt, die DMX unterstützt.  
  
|Operator|Beschreibung|  
|--------------|-----------------|  
|[&#60;&#40;Kleiner als&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite kleiner ist als der Wert des Arguments auf der rechten Seite; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62;&#40;Größer als&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Für Argumente, die einen Wert ungleich Null ergeben, gibt "true", wenn der Wert des Arguments auf der linken Seite größer als der Wert des Arguments auf der rechten Seite ist; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[= &#40;Gleich&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Für Argumente, die auf einen nicht-Null-Wert ausgewertet. gibt TRUE zurück, wenn der Wert des Arguments auf der linken Seite gleich dem Wert des Arguments auf der rechten Seite ist; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;&#62;&#40;Ungleich&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Für Argumente, die einen Wert ungleich Null ergeben, gibt "true", wenn der Wert des Arguments auf der linken Seite nicht gleich dem Wert des Arguments auf der rechten Seite ist; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;= &#40;Kleiner als oder gleich&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite kleiner gleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62;= &#40;Größer als oder gleich&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Für Argumente, die einen Wert ungleich Null ergeben, gibt true, wenn der Wert des Arguments auf der linken Seite größer als oder gleich dem Wert des Arguments auf der rechten Seite; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
  
 Sie können Vergleichsoperatoren in DMX-Anweisungen und -Funktionen auch verwenden, um nach einer Bedingung zu suchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Ausdrücke &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
