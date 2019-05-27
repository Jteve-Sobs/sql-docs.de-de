---
title: Durchsuchen eines Modells mit dem Microsoft Association Rules-Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7c3764d18d26d739023bbbb744236273e5cfd1a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66086160"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a>Modell mit dem Microsoft-Viewer für Zuordnungsregeln durchsuchen
  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules-Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zeigt Miningmodelle an, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association-Algorithmus erstellt wurden. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association-Algorithmus ist ein Zuordnungsalgorithmus zum Erstellen von Data Mining-Modellen, die Sie für die Warenkorbanalyse verwenden können. Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Association Algorithm](microsoft-association-algorithm.md).  
  
 Die primären Gründe zum Verwenden des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association-Algorithmus sind die folgenden:  
  
-   Zum Finden von Itemsets, die Elemente beschreiben, die in der Regel zusammen in einer Transaktion gefunden werden.  
  
-   Zum Erkennen von Regeln, die, basierend auf vorhandenen Elementen, das Vorhandensein anderer Elemente in einer Transaktion vorhersagen.  
  
> [!NOTE]  
>  Wenn Sie detaillierte Informationen über die im Modell verwendeten Formeln und die entdeckten Muster sehen möchten, verwenden Sie den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree-Viewer. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) oder [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
 Eine exemplarische Vorgehensweise zum Erstellen, durchsuchen und Verwenden eines zuordnungsminingmodells finden Sie unter [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).  
  
##  <a name="BKMK_ViewerTabs"></a> Viewer-Registerkarten  
 Wenn Sie ein Miningmodell in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]durchsuchen, wird das Modell im Data Mining-Designer auf der Registerkarte **Miningmodell-Viewer** mit dem jeweils geeigneten Viewer für das Modell angezeigt. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Zuordnungsregeln-Viewer enthält die folgenden Registerkarten:  
  
-   [Itemsets](#BKMK_Itemsets)  
  
-   [Regeln](#BKMK_Rules)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_Dependency)  
  
 Jede Registerkarte enthält das Kontrollkästchen **Langen Namen anzeigen** , mit dem Sie die Tabelle, aus der das Itemset in der Regel oder im Itemset stammt, anzeigen oder ausblenden können.  
  
###  <a name="BKMK_Itemsets"></a> Itemsets  
 Die Registerkarte **Itemsets** zeigt die Liste der Itemsets an, die das Modell häufig gemeinsam identifiziert hat. Die Registerkarte zeigt ein Raster mit den folgenden Spalten: **Unterstützung**, **Größe**, und **Itemset**. Weitere Informationen zum Unterstützungswert finden Sie unter [Microsoft Association Algorithm](microsoft-association-algorithm.md). Die Spalte **Größe** zeigt die im Itemset enthaltene Anzahl an Elementen an. Die **Itemset** -Spalte zeigt das eigentliche, vom Modell erkannte Itemset an. Sie können das Format des Itemsets mithilfe der Liste **Anzeigen** steuern. Dabei können Sie das Format auf die folgenden Optionen festlegen:  
  
-   **Attributnamen und Wert anzeigen**  
  
-   **Nur Attributwert anzeigen**  
  
-   **Nur Attributnamen anzeigen**  
  
 Sie können die Anzahl der auf der Registerkarte angezeigten Itemsets mit den Optionen **Minimaler Unterstützungswert** und **Mindestgröße des Itemsets**filtern. Die Anzahl der angezeigten Itemsets können Sie weiter einschränken, indem Sie die Option **Filteritemset** verwenden und ein bereits vorhandenes Itemsetmerkmal eingeben. Wenn Sie z. B. "Water Bottle = existing" eingeben, können Sie die Einschränkung auf jene Itemsets vornehmen, die eine Wasserflasche enthalten. Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
 Sie können die Zeilen im Raster sortieren, indem Sie auf eine Spaltenüberschrift klicken.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Regeln  
 Die Registerkarte **Regeln** zeigt die vom Zuordnungsalgorithmus erkannten Regeln an. Die **Regeln** Registerkarte enthält ein Raster mit den folgenden Spalten: **Wahrscheinlichkeit**, **Wichtigkeit**, und **Regel**. Die Wahrscheinlichkeit beschreibt, wie wahrscheinlich das Ergebnis einer Regel auftreten kann. Mit der Wichtigkeit wird die Nützlichkeit einer Regel gemessen. Obwohl die Wahrscheinlichkeit, dass eine Regel auftritt, hoch sein kann, kann die Nützlichkeit der Regel an sich unwichtig sein. Dies wird in der Wichtigkeitsspalte berücksichtigt. Wenn z. B. jedes Itemset einen bestimmten Attributstatus hat, ist die Regel, die den Status vorhersagt, unbedeutend, auch wenn die Wahrscheinlichkeit sehr hoch ist. Je größer die Wichtigkeit ist, umso wichtiger ist die Regel.  
  
 Sie können zum Filtern der Regeln – ähnlich wie das Filtern auf der Registerkarte **Itemsets** – die Optionen **Mindestwahrscheinlichkeit** und **Minimale Wichtigkeit** verwenden. Sie können auch die Option **Filterregel** verwenden, um eine Regel auf Basis der Attributstatus, die in der Regel enthalten sind, zu filtern.  
  
 Sie können die Zeilen im Raster sortieren, indem Sie auf eine Spaltenüberschrift klicken.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Abhängigkeitsnetzwerk  
 Die Registerkarte **Abhängigkeitsnetzwerk** enthält einen Abhängigkeitsnetzwerk-Viewer. Jeder Knoten im Viewer stellt ein Element dar, wie z. B. "state = WA". Der Pfeil zwischen den Knoten stellt die Zuordnung zwischen den Elementen dar. Die Richtung des Pfeils schreibt die Zuordnung zwischen den Elementen gemäß den vom Algorithmus erkannten Regeln vor. Z. B. wenn der Viewer drei Elemente enthält, A, B und C und C vorhergesagt wird von A und B, bei Auswahl von Knoten C zwei Pfeile zeigen in Richtung Knoten C -, A bis C und B, c  
  
 Der Schieberegler auf der linken Seite des Viewers fungiert als Filter, der an die Wahrscheinlichkeit der Regeln gebunden ist. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Links angezeigt.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Association Algorithm](microsoft-association-algorithm.md)   
 [Tasks und Anweisungen für Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md)   
 [Tasks und Anweisungen für Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md)   
 [Data Mining-Tools](data-mining-tools.md)   
 [Data Mining-Modell-Viewer](data-mining-model-viewers.md)  
  
  
