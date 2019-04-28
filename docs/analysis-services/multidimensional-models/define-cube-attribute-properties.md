---
title: Definieren von Cubeattributeigenschaften | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e2ab2374955710452f1ba1cba91e3a4d8ff8c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025462"
---
# <a name="define-cube-attribute-properties"></a>Definieren von Cubeattributeigenschaften
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Durch Cubeattributeigenschaften können Sie eindeutige Einstellungen für Dimensionsattribute in Cubedimensionen angeben, die auf derselben Datenbankdimension basieren. In der folgenden Tabelle werden die Eigenschaften eines Cubeattributs beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**AggregationUsage**|Gibt an, wie der Aggregationsentwurfs-Assistent Aggregationen für das Attribut entwirft. Der Standardwert lautet **Default**. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> **Default:**<br />                    Der Aggregationsentwurfs-Assistent wendet eine Standardregel basierend auf dem Typ des Attributs an (Vollständig für Schlüssel, Uneingeschränkt für andere Attribute).<br /><br /> **None:**<br />                    Keine Aggregation für den Cube darf dieses Attribut enthalten.<br /><br /> **Unrestricted:**<br />                    Für den Aggregationsentwurfs-Assistenten gelten keine Einschränkungen.<br /><br /> **Full:**<br />                    Jede Aggregation für den Cube muss dieses Attribut enthalten.|  
|**AttributeHierarchyEnabled**|Identifiziert, ob die Attributhierarchie für diese Cubedimension aktiviert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu deaktivieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie deaktiviert ist. Der Standardwert ist **True**.|  
|**OptimizedState**|Zeigt an, ob die Attributhierarchie für diese Cubedimension optimiert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu optimieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht optimiert ist. Der Standardwert lautet **FullyOptimized**. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> **FullyOptimized:** Durch die Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> **NotOptimized:**<br />                    Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
|**AttributeHierarchyVisible**|Zeigt an, ob die Attributhierarchie für diese Cubedimension sichtbar ist. Hierdurch ist es möglich, dass Attributhierarchien für bestimmte Cubes oder Dimensionsrollen sichtbar gemacht werden. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht sichtbar ist. Der Standardwert lautet **True**.|  
|**AttributeID**|Enthält den eindeutigen Bezeichner (ID) des Attributs.|  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Cubedimensionseigenschaften](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [Definieren von Cubehierarchieeigenschaften](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  
