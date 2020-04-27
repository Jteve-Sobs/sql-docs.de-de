---
title: Manuelles Bearbeiten einer Vorhersage Abfrage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce2086e998704e893beaa92aabd2e51129a0450f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084211"
---
# <a name="manually-edit-a-prediction-query"></a>Manuelles Bearbeiten eine Vorhersageabfrage
  Nachdem Sie eine Abfrage mit dem Generator für Vorhersageabfragen erstellt haben, können Sie die Abfrage ändern, indem Sie zur Abfragetextansicht auf der Registerkarte **Miningmodellvorhersage** des Data Mining-Designers wechseln. Am unteren Rand des Bildschirms wird ein Texteditor angezeigt, in dem die vom Abfragegenerator erstellte Abfrage angezeigt wird.  
  
 Das Wechseln zur Abfragetextansicht ist für Hinzufügungen zur Abfrage nützlich. Sie können z. B. eine WHERE-Klausel oder eine ORDER BY-Klausel hinzufügen.  
  
 Verwenden Sie das Raster im Generator für Vorhersageabfragen, um die Namen von Objekten und Spalten einzufügen, und richten Sie die Syntax für einzelne Vorhersagefunktionen ein, und wechseln Sie dann in den manuellen Bearbeitungsmodus, um Parameterwerte zu ändern.  
  
> [!NOTE]  
>  Wenn Sie von der **Abfragetextansicht** wieder zurück zur **Entwurfsansicht** wechseln, gehen alle von Ihnen in der **Abfragetextansicht** vorgenommenen Änderungen verloren.  
  
### <a name="modify-a-query"></a>Ändern einer Abfrage  
  
1.  Klicken Sie in der Registerkarte **Miningmodellvorhersage** des Data Mining-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf **SQL**.  
  
     Der Rasterbereich am unteren Bildschirmrand wird durch einen Texteditor ersetzt, der die Abfrage enthält. In diesem Editor können Sie die Abfrage ändern.  
  
2.  Zum Ausführen der Abfrage wählen Sie im Menü **Miningmodell** die Option **Ergebnis**, oder klicken Sie auf die Schaltfläche zum Wechseln zu den Abfrageergebnissen.  
  
    > [!NOTE]  
    >  Wenn die erstellte Abfrage ungültig ist, werden im Ergebnisfenster weder ein Fehler noch Ergebnisse angezeigt. Klicken Sie auf die Schaltfläche **Entwurf** , oder wählen Sie im Menü **Miningmodell** die Option **Entwurf** oder **Abfrage** aus, um das Problem zu beheben und die Abfrage erneut auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Abfragen](data-mining-queries.md)   
 [Vorhersage Abfrage-Generator &#40;Data Mining-&#41;](../prediction-query-builder-data-mining.md)   
 [Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Tutorial zu Data Mining-Grundlagen&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
