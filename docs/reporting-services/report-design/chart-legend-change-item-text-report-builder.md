---
title: Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bc8b459c3ecfe9c34ff7552acb2565c1b25239a7
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581691"
---
# <a name="chart-legend---change-item-text-report-builder"></a>Diagrammlegende: Ändern von Elementtext (Berichts-Generator)
  Wenn Sie ein Feld im Wertebereich des Diagramms ablegen, wird automatisch ein Legendenelement mit dem Namen dieses Felds erstellt. Alle Legendenelemente im Diagramm sind mit jeweils einer Reihe verknüpft, mit Ausnahme von Formdiagrammen, bei denen die Legende stattdessen mit einzelnen Datenpunkten verknüpft ist.  
  
 In Formdiagrammen können Sie den Text eines Legendenelements so ändern, dass weitere Informationen zu den einzelnen Datenpunkten angezeigt werden. Wenn beispielsweise die Werte der Datenpunkte in der Legende als Prozentsätze angezeigt werden sollen, können Sie ein Schlüsselwort wie **#PERCENT**angeben. Sie können .NET Framework-Formatcodes in Verbindung mit Schlüsselwörtern anfügen, um numerische Formate und Datumsformate anzuwenden. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Sharp-Diagramm](../../reporting-services/report-design/media/sharpchart.png "Sharp-Diagramm")  
  
 In Nicht-Formdiagrammen können Sie den Text eines Legendenelements ändern. Wenn eine Reihe beispielsweise den Namen "Reihe1" aufweist, können Sie diesen in einen aussagekräftigeren Namen wie "Umsatz für 2008" ändern.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>So ändern Sie den Text, der in der Legende eines Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte** , und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** ein Schlüsselwort ein.  
  
 In der folgenden Tabelle sind Beispiele für diagrammspezifische Schlüsselwörter aufgelistet, die für die Eigenschaft **Benutzerdefinierter Legendentext** verwendet werden sollen. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Schlüsselwort|Beschreibung|Beispiel für den in der Legende angezeigten Text|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Zeigt den Prozentsatz des Gesamtwerts mit einer Dezimalstelle an.|85.0%|  
|`#VALY`|Zeigt den tatsächlichen numerischen Wert des Datenfelds an.|17000|  
|`#VALY{C2}`|Zeigt den tatsächlichen numerischen Wert des Datenfelds als Währung mit zwei Dezimalstellen an.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Zeigt die Textdarstellung des Kategoriefelds an, gefolgt von dem Prozentsatz, der in den einzelnen Kategorien im Diagramm angezeigt wird.|Michael Blythe (85 %)|  
  
> [!NOTE]  
>  Das Schlüsselwort #AXISLABEL kann nur dann zur Laufzeit ausgewertet werden, wenn im Bereich **Reihengruppen** kein Feld angegeben ist.  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>So ändern Sie den Text, der in der Legende eines Nicht-Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte** , und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** eine Legendenbezeichnung ein. Die Reihe wird mit dem Text aktualisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Ausblenden von Legendenelementen im Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-legend-hide-items-report-builder.md)  
  
  
