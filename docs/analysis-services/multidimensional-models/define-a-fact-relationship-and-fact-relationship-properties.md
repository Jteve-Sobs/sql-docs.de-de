---
title: Definieren von faktenbeziehungen und Faktenbeziehungseigenschaften | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2341335d1d9c4904e1832e0a8087c0fa8198fd58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178838"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definieren von Faktenbeziehungen und Faktenbeziehungseigenschaften
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Wenn Sie eine neue Cubedimension oder eine neue Measuregruppe definieren, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , zu erkennen, ob eine Faktendimensionsbeziehung vorhanden ist, und legt dann die Einstellung für die Dimensionsverwendung auf **Fakt**fest. Sie können eine Faktendimensionsbeziehung im Cube-Designer auf der Registerkarte **Dimensionsverwendung** anzeigen oder bearbeiten. Die Faktenbeziehung zwischen einer Dimension und einer Measuregruppe besitzt die folgenden Einschränkungen:  
  
-   Eine Cubedimension kann nur über eine Faktenbeziehung zu einer bestimmten Measuregruppe verfügen.  
  
-   Eine Cubedimension kann über separate Faktenbeziehungen zu mehreren Measuregruppen verfügen.  
  
-   Beim Granularitätsattribut der Beziehung muss es sich um das Schlüsselattribut (z. B. Transaction Number) für die Dimension handeln. Hierdurch wird eine 1:1-Beziehung zwischen der Dimension und den Fakten in der Faktentabelle erstellt.  
  
  
