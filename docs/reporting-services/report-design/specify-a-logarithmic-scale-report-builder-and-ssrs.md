---
title: Angeben einer logarithmischen Skalierung (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d3a3e94111a11380b86ec3127d7a1c9641f20b44
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65570815"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>Angeben einer logarithmischen Skalierung (Berichts-Generator und SSRS)
  Bei logarithmisch proportionalen Daten wäre es möglicherweise sinnvoll, in einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Bericht eine logarithmische Skalierung für das Diagramm zu verwenden. So werden die Daten überschaubarer und die Darstellung des Diagramms wird verbessert. Die meisten logarithmischen Skalierungen verwenden die Basis 10.  
  
 Diese Funktion ist nur auf der Wertachse verfügbar. Die Wertachse ist normalerweise die vertikale Achse bzw. y-Achse. Bei Balkendiagrammen ist jedoch die horizontale Achse bzw. x-Achse die Wertachse.  
  
 Wenn die Achse logarithmisch ist, werden alle anderen Eigenschaften, die sich auf die Achse beziehen, logarithmisch skaliert. Wenn Sie beispielsweise eine logarithmische Skalierung zur Basis 10 auf der Achse angeben, werden durch Festlegen eines Achsenintervalls von 2 Intervalle in der Größenordnung von 10 hoch 2 bzw. 100 generiert. Dies bedeutet, dass die Achsenwerte 1, 100, 10000 und nicht wie standardmäßig 1, 10, 100, 1000, 10000 lauten.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-logarithmic-scale"></a>So geben Sie eine logarithmische Skalierung an  
  
1.  Klicken Sie mit der rechten Maustaste auf die y-Achse des Diagramms, und klicken Sie auf **Eigenschaften für vertikale Achsen**. Das Dialogfeld **Eigenschaften für vertikale Achsen** wird angezeigt.  
  
2.  Aktivieren Sie unter **Achsenoptionen**die Option **Logarithmische Skalierung verwenden**.  
  
3.  Geben Sie im Textfeld **Logarithmische Basis** einen positiven Wert für die logarithmische Basis ein. Wird kein Wert angegeben, wird als Standardwert 10 verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung (Berichts-Generator und SSRS)](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
