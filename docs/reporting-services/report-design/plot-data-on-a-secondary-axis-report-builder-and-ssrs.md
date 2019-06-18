---
title: Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 86d73f2ab16bdb7ee801e333f3a75c96a2a1c360
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65578190"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS)

Das Diagramm verfügt über zwei Achsentypen: primär und sekundär. Die sekundäre Achse ist nützlich beim Vergleichen von zwei Wertsätzen mit zwei unterschiedlichen Datenbereichen, die eine gemeinsame Kategorie verwenden.  
  
 Angenommen, Sie haben ein Diagramm, das Einnahmen und Steuern für das Jahr 2008 berechnet. In diesem Fall verwenden beide Wertsätze den Zeitraum 2008 gemeinsam. Wenn beide Reihen jedoch auf derselben Y-Achse gezeichnet werden, kann kein sinnvoller Vergleich durchgeführt werden, da die Skala der Y-Achse für die größten Werte im Dataset optimiert ist. Wenn die Einnahmen auf der primären Achse und die Steuern auf der sekundären Achse angezeigt werden, kann jede Reihe auf einer eigenen Y-Achse mit einer eigenen Werteskala dargestellt werden. Die Reihen verwenden nach wie vor eine gemeinsame X-Achse.  
  
 In Fällen, in denen mehr als zwei Reihen verglichen werden, sollten Sie einen anderen Ansatz für den Vergleich und die Anzeige mehrerer Reihen in einem Diagramm in Erwägung ziehen. Weitere Informationen hierzu finden Sie unter [Mehrere Reihen in einem Diagramm](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Ein Beispiel für dieses Diagramm ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>So zeichnen Sie eine Reihe auf der sekundären Achse  
  
1.  Klicken Sie mit der rechten Maustaste auf die Reihe im Diagramm oder auf ein Feld im Bereich **Werte** , das Sie auf der sekundären Achse anzeigen möchten. Klicken Sie anschließend auf **Reiheneigenschaften**. Das Dialogfeld **Reiheneigenschaften** wird angezeigt.  
  
2.  Klicken Sie auf **Achsen und Diagrammfläche**, und wählen Sie die sekundäre Achse aus, die Sie aktivieren möchten, d. h. die Wertachse oder die Kategorieachse.  

## <a name="next-steps"></a>Nächste Schritte

[Formatieren von Achsenbezeichnungen in einem Diagramm](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
[Angeben eines Achsenintervalls](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
