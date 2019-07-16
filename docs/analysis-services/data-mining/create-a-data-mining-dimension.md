---
title: Erstellen von Datamining-Dimension | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2455ccc283af429cb314aa2e5182f8b2ee58c18e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68184101"
---
# <a name="create-a-data-mining-dimension"></a>Erstellen einer Data Mining-Dimension
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Wenn Ihre Miningstruktur auf einem OLAP-Cube basiert, können Sie eine Dimension erstellen, die den Inhalt des Miningmodells enthält. Sie können dann die Dimension wieder in den Quellcube einbinden.  
  
 Sie können auch die Dimension durchsuchen, sie zum Untersuchen der Modellergebnisse verwenden oder die Dimension mit MDX abfragen.  
  
### <a name="to-create-a-data-mining-dimension"></a>So erstellen Sie eine Data Mining-Dimension  
  
1.  Wählen Sie im Data Mining-Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]entweder die **Miningstruktur** -Registerkarte oder die **Miningmodelle** -Registerkarte aus.  
  
2.  Wählen Sie aus dem Menü **Miningmodell** die Option **Data Mining-Dimension erstellen**aus.  
  
     Das Dialogfeld **Data Mining-Dimension erstellen** wird geöffnet.  
  
3.  Wählen Sie in der **Modellname** -Liste des Dialogfelds **Data Mining-Dimension auswählen** ein OLAP-Miningmodell aus.  
  
4.  Geben Sie im Feld **Dimensionsname** einen Namen für die neue Data Mining-Dimension ein.  
  
5.  Wenn Sie einen Cube erstellen wollen, der die neue Data Mining-Dimension einbindet, wählen Sie **Cube erstellen**aus. Nachdem Sie **Cube erstellen**ausgewählt haben, können Sie einen neuen Namen für den Cube eingeben.  
  
6.  Klicken Sie auf **OK**.  
  
     Die Data Mining-Dimension wird erstellt und dem **Dimensionen** -Ordner im Projektmappen-Explorer hinzugefügt. Wenn Sie **Cube erstellen**ausgewählt haben, wird auch ein neuer Cube erstellt und dem **Cubes** -Ordner hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
