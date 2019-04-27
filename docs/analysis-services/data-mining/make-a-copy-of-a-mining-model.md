---
title: Erstellen Sie eine Kopie eines Miningmodells | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c5479a43a07a6398ff45635828a2a9c88b7cb11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679465"
---
# <a name="make-a-copy-of-a-mining-model"></a>Erstellen einer Kopie eines Miningmodells
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Erstellung einer Kopie eines Miningmodells ist hilfreich, wenn Sie schnell mehrere Miningmodelle erstellen möchten, die auf den gleichen Daten basieren. Nach dem Kopieren des Modells können Sie die neue Kopie bearbeiten, indem Sie Parameter ändern oder einen Filter hinzufügen.  
  
 Wenn Sie zum Beispiel eine Customers-Tabelle besitzen, die mit einer Tabelle verknüpft ist, in der Einkäufe aufgeführt sind, können Sie Kopien erstellen, um separate Miningmodelle für jede Kundendemografie zu generieren und nach Attributen wie Alter oder Region zu filtern.  
  
 Informationen zum Kopieren des Inhalts des Modells (z.B. die grafische Darstellung oder die Modellmuster) in die Zwischenablage zur Verwendung in anderen Programmen finden Sie unter [Kopieren einer Sicht eines Miningmodells](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>So erstellen Sie ein verknüpftes Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in Projektmappen-Explorer auf die Miningstruktur, die das Miningmodell enthält.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Wählen Sie das Modell aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü zu öffnen.  
  
     -oder-  
  
     Wählen Sie das Modell aus. Klicken Sie im Menü **Miningmodell** auf **Neues Miningmodell**.  
  
4.  Geben Sie einen Namen für das neue Miningmodell ein, und wählen Sie einen Algorithmus aus. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>So bearbeiten Sie den Filter im kopierten Miningmodell  
  
1.  Wählen Sie das Miningmodell aus.  
  
2.  In der **Eigenschaften** Fenster, klicken Sie auf das Textfeld für die **Filter** -Eigenschaft, und klicken Sie auf der Build **(...)**  Schaltfläche.  
  
3.  Ändern Sie die Filterbedingungen.  
  
     Weitere Informationen zur Verwendung der Dialogfelder des Filter-Editors finden Sie unter [Anwenden eines Filters auf ein Miningmodell](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
4.  Klicken Sie im Fenster **Eigenschaften** im Textfeld **AlgorithmParameters** auf **Algorithmusparameter festlegen**, und ändern Sie bei Bedarf Algorithmusparameter.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Filter für Miningmodelle &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Miningmodelltasks und Anweisungen](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Löschen eines Filters aus einem Miningmodell](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
