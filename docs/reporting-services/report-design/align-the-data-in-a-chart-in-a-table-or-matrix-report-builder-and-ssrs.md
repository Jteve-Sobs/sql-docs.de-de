---
title: Ausrichten von Daten in einem Diagramm, in einer Tabelle oder einer Matrix (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 763091e27701524a40c686fc773a6e4e845992fb
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290418"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Ausrichten von Diagrammdaten in einer Tabelle oder einer Matrix (Berichts-Generator und SSRS)
  Sparklines und Datenbalken sind kleine, einfache Diagramme, die viel Information mit wenig relevanten Details vermitteln. Wenn Sie diese Option in einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Bericht aktivieren, werden die Werte in Ihren Sparklines und Datenbalken in den verschiedenen Zellen in der Tabelle oder Matrix ausgerichtet, selbst wenn in den Daten Werte fehlen, auf denen die Sparklines und Datenbalken basieren.  
  
 ![RS_SparklineDaten ausrichten](../../reporting-services/report-design/media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 In diesem Bild wird das Säulendiagramm für die täglichen Verkäufe jedes Mitarbeiters dargestellt. Beachten Sie, dass Tage, an denen ein Mitarbeiter keine Verkäufe getätigt hat, leer gelassen werden und die nachfolgenden Tage horizontal ausgerichtet werden. Die Diagramme werden auch vertikal ausgerichtet, indem die Größen der unterschiedlichen Diagramme relativ zu einander festgelegt werden. Weitere Informationen finden Sie unter [Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Ausrichten der Daten in einer Sparkline oder einem Datenbalken  
  
1.  [Fügen Sie eine Sparkline oder einen Datenbalken](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md) zu einer Tabelle oder Matrix hinzu.  
  
2. Klicken Sie in die Sparkline oder den Datenbalken, und klicken Sie dann auf **Eigenschaften für Horizontale Achsen** oder **Eigenschaften für vertikale Achsen**.  
  
2.  Aktivieren Sie auf der Registerkarte **Achsenoptionen** das Kontrollkästchen **Achsen ausrichten in** , und wählen Sie dann im Dropdownfeld die Gruppe aus, in der die Achse ausgerichtet werden soll.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Hinzufügen von Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
