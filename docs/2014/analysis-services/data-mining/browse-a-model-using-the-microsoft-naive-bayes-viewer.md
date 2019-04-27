---
title: Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e90593dc605d700ed766d089e4605bd8cd243399
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689448"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a>Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer
  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Viewer für naives Bayes-Verfahren in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zeigt Miningmodelle an, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus erstellt wurden. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Algorithmus für das naive Bayes-Verfahren ist ein Klassifizierungsalgorithmus, der sehr gut an Modellierungsaufgaben für Vorhersagen angepasst werden kann. Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).  
  
 Da der Hauptverwendungszweck eines naiven Bayes-Modells darin besteht, eine Möglichkeit zum schnellen Durchsuchen von Daten in einem Dataset bereitzustellen, verfügt der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Viewer für naives Bayes-Verfahren über verschiedene Methoden, die Interaktion zwischen vorhersagbaren Attributen und Eingabeattributen anzuzeigen.  
  
> [!NOTE]  
>  Wenn Sie detaillierte Informationen über die im Modell verwendeten Formeln und die entdeckten Muster anzeigen möchten, können Sie zum [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree-Viewer wechseln. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) oder [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
##  <a name="BKMK_ViewerTabs"></a> Viewer-Registerkarten  
 Wenn Sie ein Miningmodell in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]durchsuchen, wird das Modell im Data Mining-Designer auf der Registerkarte **Miningmodell-Viewer** mit dem jeweils geeigneten Viewer für das Modell angezeigt. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Viewer für naives Bayes-Verfahren stellt zum Durchsuchen der Daten folgende Registerkarten bereit:  
  
-   [Abhängigkeitsnetzwerk](#BKMK_Dependency)  
  
-   [Attributprofile](#BKMK_Profiles)  
  
-   [Attributmerkmale](#BKMK_Characteristics)  
  
-   [Attributunterscheidung](#BKMK_Discrimination)  
  
##  <a name="BKMK_Dependency"></a> Abhängigkeitsnetzwerk  
 Die Registerkarte **Abhängigkeitsnetzwerk** zeigt die Abhängigkeiten zwischen den Eingabeattributen und den vorhersagbaren Attributen in einem Modell an. Der Schieberegler auf der linken Seite des Viewers fungiert als Filter, der an die Stärken der Abhängigkeiten gebunden ist. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Links angezeigt.  
  
 Wenn Sie einen Knoten auswählen, hebt der Viewer die Abhängigkeiten hervor, die knotenspezifisch sind. Wenn Sie beispielsweise einen vorhersagbaren Knoten auswählen, wird vom Viewer auch jeder Knoten hervorgehoben, der beim Vorhersagen des vorhersagbaren Knotens hilft.  
  
 Die Legende im unteren Bereich des Viewers verknüpft Farbcodes mit dem Abhängigkeitstyp im Diagramm. Wenn Sie einen vorhersagbaren Knoten auswählen, wird dieser z. B. türkis schattiert, und die Knoten, die den ausgewählten Knoten vorhersagen, orange.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Profiles"></a> Attributprofile  
 Die Registerkarte **Attributprofile** zeigt Histogramme in einem Raster an. Sie können dieses Raster verwenden, um die vorhersagbaren Attribute, die Sie im Feld **Vorhersagbar** auswählen, mit den anderen Attributen zu vergleichen, die im Modell enthalten sind. Jede Spalte in der Tabelle stellt einen Status des vorhersagbaren Attributs dar. Wenn das vorhersagbare Attribut viele Status hat, können Sie die Anzahl der Status verändern, die im Histogramm angezeigt werden, indem Sie die Option **Histogrammbalken**anpassen. Wenn die Anzahl, die Sie auswählen, kleiner ist als die Gesamtzahl von Status im Attribut, werden die Status nach Unterstützung sortiert, wobei die restlichen Status in einem einzigen grauen Bucket gesammelt werden.  
  
 Um eine Mininglegende anzuzeigen, die die Farben des Histogramms den Statuswerten eines Attributs zuordnet, aktivieren Sie das Kontrollkästchen **Legende anzeigen** . Die Mininglegende zeigt auch die Verteilung von Fällen für jedes Attribut/Wert-Paar an, das Sie auswählen.  
  
 Klicken Sie mit der rechten Maustaste auf die Registerkarte **Attributprofile** , und wählen Sie **Kopieren**aus, um die Inhalte des Rasters als HTML-Tabelle in die Zwischenablage zu kopieren.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Characteristics"></a> Attributmerkmale  
 Um die Registerkarte **Attributmerkmale** zu verwenden, wählen Sie aus der Liste **Attribut** ein vorhersagbares Attribut aus, und wählen Sie anschließend aus der Liste **Wert** einen Status des ausgewählten Attributs aus. Wenn Sie diese Variablen festlegen, zeigt die Registerkarte **Attributmerkmale** die Status der Attribute an, die mit dem ausgewählten Fall des ausgewählten Attributs verknüpft sind. Die Attribute sind nach ihrer Wichtigkeit sortiert.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Discrimination"></a> Attributunterscheidung  
 Wählen Sie zum Verwenden der Registerkarte **Attributunterscheidung** ein vorhersagbares Attribut und zwei ihrer Status aus den Listen **Attribut**, **Wert 1**und **Wert 2** aus. Das Raster auf der Registerkarte **Attributunterscheidung** zeigt daraufhin die folgenden Informationen in Spalten an:  
  
 **Attribut**  
 Listet weitere Attribute im Dataset auf, die einen Status enthalten, der den Status eines vorhersagbaren Attributs stark bevorzugt.  
  
 **Werte**  
 Zeigt den Wert des Attributs in der Spalte **Attribute** an.  
  
 **Begünstigt \<Wert 1 >**  
 Zeigt eine farbige Leiste an, die kennzeichnet, wie stark der Attributwert den in **Wert 1**dargestellten vorhersagbaren Attributwert bevorzugt.  
  
 **Begünstigt \<Wert 2 >**  
 Zeigt eine farbige Leiste an, die kennzeichnet, wie stark der Attributwert den in **Wert 2** dargestellten vorhersagbaren Attributwert bevorzugt.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md)   
 [Tasks und Anweisungen für Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md)   
 [Data Mining-Tools](data-mining-tools.md)   
 [Data Mining-Modell-Viewer](data-mining-model-viewers.md)  
  
  
