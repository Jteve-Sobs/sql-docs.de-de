---
title: Erstellen von berechneten Elementen in MDX (Multidimensional Expressions) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9235b9e3531e2ca40cabe211d85c077e629dacee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806132"
---
# <a name="mdx-calculated-members---building-calculated-members"></a>Berechnete Elemente (MDX) – Erstellen berechneter Elemente
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Ein berechnetes Element in MDX (Multidimensional Expressions) ist ein Element, das durch Berechnen eines MDX-Ausdrucks aufgelöst wird, um einen Wert zurückzugeben. Diese einfach klingende Definition hat immense Auswirkungen. Die Erstellung und Verwendung von berechneten Elementen in einer MDX-Abfrage eröffnet umfassende Änderungsmöglichkeiten für mehrdimensionale Daten.  
  
 Sie können berechnete Elemente an jedem beliebigen Punkt in einer Hierarchie erstellen. Sie können außerdem berechnete Elemente erstellen, die nicht nur von vorhandenen Elementen in einem Cube abhängen, sondern auch von anderen berechneten Elementen, die in demselben MDX-Ausdruck definiert sind.  
  
 Sie können berechnete Elemente in einem der folgenden Kontexte definieren:  
  
-   **Im Bereich einer Abfrage** : Mit dem WITH-Schlüsselwort können Sie ein berechnetes Element erstellen, das als Teil einer MDX-Abfrage definiert ist und dessen Bereich somit auf die Abfrage beschränkt ist. Anschließend können Sie das berechnete Element in einer SELECT-Anweisung von MDX verwenden. Bei dieser Vorgehensweise kann das mit dem WITH-Schlüsselwort erstellte berechnete Element geändert werden, ohne dass die SELECT-Anweisung davon beeinflusst wird.  
  
     Weitere Informationen zum Erstellen berechneter Elemente mithilfe des WITH-Schlüsselworts finden Sie unter [Erstellen berechneter Elemente im Bereich einer Abfrage &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Im Bereich einer Sitzung**: Mit der CREATE MEMBER-Anweisung können Sie ein berechnetes Element erstellen, dessen Bereich umfangreicher als der Kontext der Abfrage ist, d.h. der Dauer der MDX-Sitzung entspricht. Ein mit der CREATE MEMBER-Anweisung definiertes berechnetes Element ist für alle MDX-Abfragen in dieser Sitzung verfügbar. Die CREATE MEMBER-Anweisung ist z. B. in einer Clientanwendung sinnvoll, die die gleiche Menge in unterschiedlichen Abfragen wiederverwendet.  
  
     Weitere Informationen zum Erstellen berechneter Elemente in einer Sitzung mithilfe der CREATE MEMBER-Anweisung finden Sie unter [Erstellen berechneter Elemente im Bereich einer Abfrage &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE MEMBER-Anweisung &#40;MDX&#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT-Anweisung &#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
