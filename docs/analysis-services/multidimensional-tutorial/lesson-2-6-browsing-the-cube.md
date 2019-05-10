---
title: Durchsuchen des Cubes | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da01dbb0f8e67d885382a3fa125a0fb37596d553
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403972"
---
# <a name="lesson-2-6---browsing-the-cube"></a>Lektion 2 – 6: Durchsuchen des Cubes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Nach dem Bereitstellen des Cubes können dessen Daten auf der Registerkarte **Browser** im Cube-Designer und die Dimensionsdaten auf der Registerkarte **Browser** im Dimensions-Designer angezeigt werden. Indem Sie Cube- und Dimensionsdaten durchsuchen, können Sie Ihre Arbeit schrittweise überprüfen. Sie können überprüfen, ob geringe Änderungen an Eigenschaften, Beziehungen und anderen Objekten nach der Verarbeitung des Objekts den gewünschten Effekt hatten. Obwohl auf der Registerkarte Browser sowohl Cube- als auch Dimensionsdaten angezeigt werden, enthält die Registerkarte je nach Objekt, das durchsucht wird, unterschiedliche Funktionen.  
  
Bei Dimensionen bietet die Registerkarte Browser die Möglichkeit, Elemente anzuzeigen oder durch eine ganze Hierarchie bis zum Blattknoten zu navigieren. Dimensionsdaten können in verschiedenen Sprachen durchsucht werden, wenn Sie dem Modell entsprechende Übersetzungen hinzugefügt haben.  
  
Bei Cubes bietet die Registerkarte Browser zwei Möglichkeiten zum Durchsuchen von Daten. Mit dem integrierten MDX-Abfrage-Designer können Sie Abfragen erstellen, die ein vereinfachtes Rowset aus einer mehrdimensionalen Datenbank zurückgeben. Alternativ können Sie eine Excel-Verknüpfung verwenden. Wenn Sie Excel in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]starten, wird beim Öffnen von Excel ein Arbeitsblatt mit einer PivotTable und eine vordefinierte Verbindung mit der Arbeitsbereichsdatenbank des Modells angezeigt.  
  
Excel bietet im Allgemeinen eine bessere Browsererfahrung, weil Sie die Cubedaten mithilfe von horizontalen und vertikalen Achsen interaktiv durchsuchen können, um die Beziehungen innerhalb von Daten zu analysieren. Im Unterschied dazu ist der MDX-Abfrage-Designer auf eine einzelne Achse beschränkt. Da das Rowset vereinfacht ist, verfügen Sie darüber hinaus nicht über die Drilldownfunktionen, die eine Excel-PivotTable bereitstellt. Während dem Cube in den nachfolgenden Lektionen weitere Dimensionen und Hierarchien hinzugefügt werden, wird Excel zur bevorzugten Lösung für das Durchsuchen von Daten.  
  
### <a name="to-browse-the-deployed-cube"></a>So durchsuchen Sie den bereitgestellten Cube  
  
1.  Wechseln Sie zum **Dimensions-Designer** für die Produkt-Dimension in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Doppelklicken Sie dazu auf die **Product** -Dimension im **Dimensionen** -Knoten des Projektmappen-Explorers.  
  
2.  Klicken Sie auf die Registerkarte **Browser** , um das Element **Alle** der **Product Key** -Attributhierarchie anzuzeigen. In Lektion 3 definieren Sie eine Benutzerhierarchie für die Product-Dimension, mit der Sie die Dimension durchsuchen können.  
  
3.  Wechseln Sie in **zum** Cube-Designer [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Doppelklicken Sie hierzu auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten des Projektmappen-Explorers.  
  
4.  Klicken Sie auf die Registerkarte **Browser** und anschließend auf der Symbolleiste des Designers auf das Symbol zum **Wiederherstellen der Verbindung** .  
  
    Im linken Bereich des Designers werden die Objekte für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube angezeigt. Auf der rechten Seite der Registerkarte **Browser** sind zwei Bereiche enthalten: Beim oberen Bereich handelt es sich um den Bereich **Filter** , beim unteren um den Bereich **Daten** . In einer der nächsten Lektionen verwenden Sie den Cube-Browser zur Durchführung von Analysen.  
  
## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 3: Ändern von Maßen, Attributen und Hierarchien](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a>Siehe auch  
[MDX-Abfrage-Editor &#40;Analysis Services – Mehrdimensionale Daten&#41;](http://msdn.microsoft.com/library/777f2c23-1c1c-4b72-9d19-48a4866551f8)  
  
  
  
