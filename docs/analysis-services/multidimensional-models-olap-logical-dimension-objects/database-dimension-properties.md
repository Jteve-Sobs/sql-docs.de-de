---
title: Eigenschaften von Datenbankdimensionen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c7944ab279f2b036a3acd7cf75bd775d0ec6d6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68180774"
---
# <a name="database-dimension-properties"></a>Eigenschaften von Datenbankdimensionen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], die Merkmale einer Dimension sind definiert, indem die Metadaten für die Dimension basierend auf den Einstellungen der verschiedenen Dimensionseigenschaften und auf die Attribute oder Hierarchien, die der Dimension enthalten sind. In der folgenden Tabelle werden die Dimensionseigenschaften in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**AttributeAllMemberName**|Gibt den Namen des Alle-Elements für Attribute in einer Dimension an.|  
|**Sortierung**|Bestimmt die von der Dimension verwendete Sortierung.|  
|**CurrentStorageMode**|Enthält den aktuellen Speichermodus für die Dimension.|  
|**DependsOnDimension**|Enthält die ID einer anderen Dimension, von der die Dimension abhängt, falls vorhanden.|  
|**Beschreibung**|Enthält die Beschreibung einer Dimension.|  
|**ErrorConfiguration**|Konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|**ID**|Enthält den eindeutigen Bezeichner (ID) der Dimension.|  
|**Sprache**|Gibt die Standardsprache für die Dimension an.|  
|**MdxMissingMemberMode**|Legt die Verarbeitung fehlender Elemente in MDX-Anweisungen (Multidimensional Expressions) fest.|  
|**MiningModelID**|Enthält die ID des Miningmodells, der die Data Mining-Dimension zugeordnet ist. Diese Eigenschaft kann nur angewendet werden, wenn die Dimension eine Miningmodelldimension ist.|  
|**Name**|Gibt den Namen der Dimension an.|  
|**ProactiveCaching**|Definiert die Einstellungen für die Dimension für die proaktive Zwischenspeicherung.|  
|**ProcessingGroup**|Gibt die Verarbeitungsgruppe an. Die Werte sind ByAttribute oder ByTable. Der Standardwert ist **ByAttribute**.|  
|**ProcessingMode**|Gibt an, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] während oder nach der Verarbeitung indizieren und aggregieren soll.|  
|**ProcessingPriority**|Bestimmt die Verarbeitungspriorität der Dimension während Hintergrundvorgängen wie verzögerte Aggregation, Indizierung oder Clustererstellung.|  
|**Quelle**|Identifiziert die Datenquellensicht, an die die Dimension gebunden ist.|  
|**StorageMode**|Bestimmt den Speichermodus für die Dimension.|  
|**Typ**|Gibt den Typ der Dimension an.|  
|**UnknownMember**|Gibt an, ob das unbekannte Element sichtbar ist.|  
|**UnknownMemberName**|Gibt die Beschriftung in der standardmäßigen Sprache der Dimension für das unbekannte Element der Dimension an.|  
|**WriteEnabled**|Gibt an, ob das Rückschreiben von Dimensionen unterstützt wird (unterliegt den Sicherheitsberechtigungen).|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen der Werte für die Eigenschaften ErrorConfiguration und UnknownMember bei der Arbeit mit null-Werte und andere Probleme mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Benutzerhierarchien](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Dimensionsbeziehungen](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
