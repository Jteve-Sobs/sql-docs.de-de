---
title: Liniendiagramme (Berichts-Generator) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b0e1308f7dfac834e6c50062a199403023088a59
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081967"
---
# <a name="line-charts-report-builder-and-ssrs"></a>Liniendiagramme (Berichts-Generator und SSRS)
  Ein Liniendiagramm zeigt Reihen als einen Satz von Punkten an, die durch eine einzelne Linie verbunden sind. Liniendiagramme werden verwendet, um große Datenmengen darzustellen, die über einen kontinuierlichen Zeitraum hinweg auftreten. Weitere Informationen zu Hinzufügen von Daten zu einem Liniendiagramm finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 Die folgende Illustration zeigt ein Liniendiagramm mit drei Reihen an.  
  
 ![Liniendiagramm](../../reporting-services/report-design/media/rs-linechart.gif "Liniendiagramm")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Abweichungen  
  
-   **Geglättete Linie**. Ein Liniendiagramm, in dem eine gekrümmte statt einer regulären Linie verwendet wird.  
  
-   **Linie, abgestuft**. Ein Liniendiagramm, in dem eine abgestufte statt einer regulären Linie verwendet wird. Die abgestufte Linie verbindet Punkte miteinander, indem eine Linie verwendet wird, die sie wie die Stufen einer Treppe aussehen lässt.  
  
-   **Sparklinediagramme**. Variationen des Liniendiagramms, die nur die Zeilenreihe in der Zelle einer Tabelle oder einer Matrix anzeigen. Weitere Informationen finden Sie unter [Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="data-considerations-for-line-charts"></a>Überlegungen zu Daten für ein Liniendiagramm  
  
-   Um das Standardliniendiagramm einprägsamer darzustellen, sollten Sie in Betracht ziehen, die Breite des Reihenrahmens auf 3 einzustellen und einen Schattenoffset mit dem Wert 1 hinzuzufügen. Hierdurch wird ein weit fetteres Liniendiagramm erstellt. Diese Eigenschaften müssen auf die ursprünglichen Werte zurückgesetzt werden, wenn Sie den Diagrammtyp von Linie in einen anderen Typ ändern.  
  
-   Falls das Dataset leere Werte enthält, werden vom Liniendiagramm leere Punkte in Form von Platzhalterlinien hinzugefügt, um die Kontinuität im Diagramm zu gewährleisten. Falls Sie nicht möchten, dass diese Linien angezeigt werden, können Sie das Dataset mit einem nicht zusammenhängenden Diagrammtyp anzeigen, beispielsweise einem Balken- oder Säulendiagramm.  
  
-   Ein Liniendiagramm erfordert mindestens zwei Punkte, um eine Linie zu zeichnen.  Falls das Dataset nur einen Datenpunkt aufweist, wird das Liniendiagramm als einzelner Datenpunktmarker angezeigt.  
  
-   Eine als Linie gezeichnete Reihe nimmt in einem Diagrammbereich nur wenig Raum ein.  Aus diesem Grund werden Liniendiagramme häufig mit anderen Diagrammtypen, z. B. Säulendiagrammen, kombiniert. Liniendiagramme können jedoch nicht mit Balken-, Polar-, Kreis- oder Formdiagrammtypen kombiniert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Säulendiagramme (Berichts-Generator und SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Flächendiagramme (Berichts-Generator und SSRS)](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md)   
 [Leere und NULL-Datenpunkte in Diagrammen (Berichts-Generator und SSRS)](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
