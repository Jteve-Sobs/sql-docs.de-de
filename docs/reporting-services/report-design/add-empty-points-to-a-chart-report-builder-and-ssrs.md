---
title: Hinzufügen von leeren Punkten zu einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ddb7fa0fcfbb12ba3cef14fb82bee08f67bc3cf6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581986"
---
# <a name="add-empty-points-to-a-chart-report-builder-and-ssrs"></a>Hinzufügen von leeren Punkten zu einem Diagramm (Berichts-Generator und SSRS)
NULL-Werte werden im Diagramm als Leerzeichen oder Lücken zwischen Datenpunkten einer Reihe angezeigt. In paginierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichten sind leere Punkte Datenpunkte, die in den leeren Bereich eingefügt werden können, der von NULL-Werten erstellt wird.  
  
 Standardmäßig werden leere Punkte berechnet, indem der Durchschnitt der vorherigen und nächsten Datenpunkte herangezogen wird, die einen Wert enthalten. Sie können dies so ändern, dass alle leeren Punkte am Nullpunkt eingefügt werden.  
  
 Weitere Informationen finden Sie unter [Leere und NULL-Datenpunkte in Diagrammen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-empty-points-on-a-chart"></a>So geben Sie leere Punkte in einem Diagramm an  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf die Reihe, die NULL-Werte enthält. Die Eigenschaften für die Reihe werden im Bereich "Eigenschaften" angezeigt.  
  
3.  Erweitern Sie den Knoten **EmptyPoint** .  
  
4.  Wählen Sie für die Color-Eigenschaft einen Farbwert aus.  
  
5.  Erweitern Sie im Knoten **EmptyPoint** den Knoten Marker.  
  
6.  Wählen Sie für die MarkerType-Eigenschaft einen Markertyp aus.  
  
    > [!NOTE]  
    >  Sie müssen einen Markertyp wählen, um leere Punkte einem Balken-, Säulen- oder Punktdiagramm hinzufügen zu können. Bei Flächen-, Linien- und Netzdiagrammen ist das Wählen eines Markertyps optional, weil der leere Bereich bzw. die Lücke im Diagramm gefüllt wird, ohne dass ein Marker angegeben werden muss.  
  
7.  Legen Sie den Wert des leeren Punkts fest.  
  
    1.  Erweitern Sie im Bereich Eigenschaften den Knoten **CustomAttributes** .  
  
    2.  Legen Sie die EmptyPointValue-Eigenschaft fest. Um leere Punkte bei einem Mittelwert der vorherigen und der nächsten Datenpunkte einzufügen, wählen Sie **Mittelwert**. Um leere Punkte am Nullpunkt einzufügen, wählen Sie **Null**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Hinzufügen von Skalierungsunterbrechungen zu einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
