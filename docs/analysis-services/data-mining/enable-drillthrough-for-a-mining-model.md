---
title: Aktivieren von Drillthrough für ein Miningmodell | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ec6d880c6b32a092f6d4da8b85dfd6693280da7d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535233"
---
# <a name="enable-drillthrough-for-a-mining-model"></a>Aktivieren von Drillthrough für ein Miningmodell
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Wenn Sie Drillthrough für ein Miningmodell aktiviert haben, können Sie beim Durchsuchen des Modells detaillierte Informationen über die Fälle abrufen, die für die Erstellung des Modells verwendet wurden. Zum Anzeigen dieser Informationen benötigen Sie die erforderlichen Berechtigungen. Außerdem muss die Struktur bereits verarbeitet worden sein.  
  
 **Berechtigungen:** Damit ein Benutzer einen Drillthrough in Modell- oder Strukturdaten ausführen kann, muss er Mitglied einer Rolle sein, die über [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) -Berechtigungen für das Miningmodell oder die Miningstruktur verfügt. Drillthroughberechtigungen werden getrennt für die Struktur und das Modell festgelegt.  
  
-   Mit Drillthrough-Berechtigungen für das Modell können Sie einen Drillthrough des Modells durchführen, auch wenn Sie keine Berechtigungen für die Struktur besitzen.  
  
-   Mit Drillthroughberechtigungen für die Struktur können Sie außerdem mit der Funktion [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md) Strukturspalten in Drillthroughabfragen für das Modell einbeziehen. Sie können auch die Trainings- und Testfälle in der Struktur Abfragen, die SELECT-Anweisung mit... VON \<Struktur >. Syntax von Fällen.  
  
 **Zwischenspeichern von Trainingsfällen:** Beim Drillthrough werden Informationen über die Trainingsfälle in der Miningstruktur abgerufen. Diese Informationen werden zwischengespeichert, wenn die Struktur verarbeitet wird. Wenn Sie alle zwischengespeicherten Daten durch Ändern der <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> -Eigenschaft in **ClearAfterProcessing**löschen, funktioniert der Drillthrough nicht.  
  
> [!NOTE]  
>  Wenn die Trainingsfälle nicht zwischengespeichert wurden, müssen Sie die <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> -Eigenschaft in **KeepTrainingCases** ändern und das Modell anschließend erneut verarbeiten, bevor Sie die Falldaten anzeigen können.  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>So aktivieren Sie Drillthrough für ein Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf den Namen des Miningmodells, für das Sie Drillthrough aktivieren möchten, und wählen Sie anschließend **Eigenschaften**aus.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf **AllowDrillthrough**, und wählen Sie **True**aus.  
  
3.  Klicken Sie auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf das Modell, und wählen Sie **Modell verarbeiten**aus.  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>So aktivieren Sie das Zwischenspeichern für eine Miningstruktur  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf der Registerkarte **Miningstruktur** mit der rechten Maustaste auf den Namen der Miningstruktur.  
  
2.  Öffnen Sie das Fenster **Eigenschaften** .  
  
3.  Suchen Sie im Fenster **Eigenschaften** die **CacheMode** -Eigenschaft, und wählen Sie dann **KeepTrainingCases** in der Liste aus.  
  
4.  Aktivieren Sie im Menü **Datenbank** die Option **Verarbeiten**.  
  
## <a name="see-also"></a>Siehe auch  
 [Drillthroughabfragen &#40;Data Mining&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  
