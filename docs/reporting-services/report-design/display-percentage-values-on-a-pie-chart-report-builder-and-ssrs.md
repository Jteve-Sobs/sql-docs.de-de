---
title: Anzeigen von Prozentwerten in einem Kreisdiagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bbc386708543b82fd79c012a40ab94f8001f5815
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56289818"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Anzeigen von Prozentwerten in einem Kreisdiagramm (Berichts-Generator und SSRS)
In paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Berichten zeigt die Legende standardmäßig Kategorien an. Bei Bedarf können Sie die Prozentsätze auch in der Legende oder den Kreissegmenten selbst anzeigen.   

![Berichts-Generator-Kreisdiagramm-Vorschau-Prozente](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 Das [Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md) führt Sie schrittweise durch das Hinzufügen von Prozentsätzen zu Kreissegmenten, falls Sie dies zunächst anhand von Beispieldaten ausprobieren möchten.
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>So zeigen Sie Prozentwerte als Bezeichnungen in einem Kreisdiagramm an  
  
1.  Fügen Sie dem Bericht ein Kreisdiagramm hinzu. Weitere Informationen finden Sie unter [Hinzufügen eines Diagramms zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf das Kreisdiagramm, und wählen Sie **Datenbezeichnungen anzeigen**aus. Die Datenbezeichnungen sollten innerhalb jedes Segments des Kreisdiagramms angezeigt werden.  
  
3.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf die Bezeichnungen, und wählen Sie **Reihenbezeichnungseigenschaften**aus. Das Dialogfeld **Reihenbezeichnungseigenschaften** wird angezeigt.  
  
4.  Geben Sie für die Option **Bezeichnungsdaten** den Wert **#PERCENT** ein.  
  
5.  (Optional) Wenn Sie die Anzahl von Dezimalstellen in der Bezeichnung angeben möchten, geben Sie „#PERECENT{P*n*}“ an, wobei *n* die Anzahl der anzuzeigenden Dezimalstellen darstellt. Geben Sie z. B. "#PERCENT{P0}" ein, um keine Dezimalstellen anzuzeigen.  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>So zeigen Sie Prozentwerte in der Legende eines Kreisdiagramms an  
  
1.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf das Kreisdiagramm, und wählen Sie **Reiheneigenschaften**aus. Das Dialogfeld **Reiheneigenschaften** wird angezeigt.  
  
2.  Geben Sie unter **Legende**den Wert **#PERCENT** für die Eigenschaft **Benutzerdefinierter Legendentext** ein.  
  
## <a name="see-also"></a>Weitere Informationen  
* [Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Kreisdiagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [Anzeigen von Datenpunktbezeichnungen außerhalb eines Kreisdiagramms &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  
