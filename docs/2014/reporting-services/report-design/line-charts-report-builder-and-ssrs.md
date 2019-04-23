---
title: Liniendiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68e6ea1c31cea554944824e38926318682b163ce
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59971936"
---
# <a name="line-charts-report-builder-and-ssrs"></a>Liniendiagramme (Berichts-Generator und SSRS)
  Ein Liniendiagramm zeigt Reihen als einen Satz von Punkten an, die durch eine einzelne Linie verbunden sind. Liniendiagramme werden verwendet, um große Datenmengen darzustellen, die über einen kontinuierlichen Zeitraum hinweg auftreten. Weitere Informationen zu Hinzufügen von Daten zu einem Liniendiagramm finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Die folgende Illustration zeigt ein Liniendiagramm mit drei Reihen an.  
  
 ![Liniendiagramm](../media/rs-linechart.gif "Line chart")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Variationen  
  
-   **Geglättete Linie**. Ein Liniendiagramm, in dem eine gekrümmte statt einer regulären Linie verwendet wird.  
  
-   **Linie, abgestuft**. Ein Liniendiagramm, in dem eine abgestufte statt einer regulären Linie verwendet wird. Die abgestufte Linie verbindet Punkte miteinander, indem eine Linie verwendet wird, die sie wie die Stufen einer Treppe aussehen lässt.  
  
-   **Sparklinediagramme**. Variationen des Liniendiagramms, die nur die Zeilenreihe in der Zelle einer Tabelle oder einer Matrix anzeigen. Weitere Informationen finden Sie unter [Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="data-considerations-for-line-charts"></a>Überlegungen zu Daten für ein Liniendiagramm  
  
-   Um das Standardliniendiagramm einprägsamer darzustellen, sollten Sie in Betracht ziehen, die Breite des Reihenrahmens auf 3 einzustellen und einen Schattenoffset mit dem Wert 1 hinzuzufügen. Hierdurch wird ein weit fetteres Liniendiagramm erstellt. Diese Eigenschaften müssen auf die ursprünglichen Werte zurückgesetzt werden, wenn Sie den Diagrammtyp von Linie in einen anderen Typ ändern.  
  
-   Falls das Dataset leere Werte enthält, werden vom Liniendiagramm leere Punkte in Form von Platzhalterlinien hinzugefügt, um die Kontinuität im Diagramm zu gewährleisten. Falls Sie nicht möchten, dass diese Linien angezeigt werden, können Sie das Dataset mit einem nicht zusammenhängenden Diagrammtyp anzeigen, beispielsweise einem Balken- oder Säulendiagramm.  
  
-   Ein Liniendiagramm erfordert mindestens zwei Punkte, um eine Linie zu zeichnen.  Falls das Dataset nur einen Datenpunkt aufweist, wird das Liniendiagramm als einzelner Datenpunktmarker angezeigt.  
  
-   Eine als Linie gezeichnete Reihe nimmt in einem Diagrammbereich nur wenig Raum ein.  Aus diesem Grund werden Liniendiagramme häufig mit anderen Diagrammtypen, z. B. Säulendiagrammen, kombiniert. Liniendiagramme können jedoch nicht mit Balken-, Polar-, Kreis- oder Formdiagrammtypen kombiniert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](bar-charts-report-builder-and-ssrs.md)   
 [Säulendiagramme &#40;Berichts-Generator und SSRS&#41;](column-charts-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Flächendiagramme (Berichts-Generator und SSRS)](area-charts-report-builder-and-ssrs.md)   
 [Leere und NULL-Datenpunkte in Diagrammen (Berichts-Generator und SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
