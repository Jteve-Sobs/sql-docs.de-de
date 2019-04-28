---
title: Über-/ Unterordnungshierarchie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], parent-child
- dimensions [Analysis Services], parent-child
- parent attributes [Analysis Services]
- data members [Analysis Services]
- hierarchies [Analysis Services], multilevel
- self-joins
- self-referencing relationships
- members [Analysis Services], data
- parent-child dimensions [Analysis Services]
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be08164b3e96f5995c5ed1b64edc83699c7d8b40
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62736798"
---
# <a name="parent-child-hierarchy"></a>Über-/ Unterordnungshierarchie
  Eine Hierarchie mit über- und untergeordneten Elementen ist eine Hierarchie in einer Standarddimension, die ein übergeordnetes Attribut enthält. Ein übergeordnetes Attribut beschreibt eine *auf sich selbst verweisende Beziehung*oder einen *Selbstjoin*innerhalb einer Dimensionstabelle. Über-/Unterordnungshierarchien werden von einem einzelnen übergeordneten Attribut erstellt. Nur eine Ebene ist einer Über-/Unterordnungshierarchie zugewiesen, da die in der Hierarchie vorhandenen Ebenen aus den Über-/Unterordnungsbeziehungen zwischen Elementen, die mit dem übergeordneten Attribut verknüpft sind, abgerufen werden. Die Position eines Elements in einer Über-/Unterordnungshierarchie wird durch die Eigenschaften `KeyColumns` und `RootMemberIf` des übergeordneten Attributs bestimmt, die Position eines Elements in einer Ebene wird hingegen durch die `OrderBy`-Eigenschaft des übergeordneten Attributs bestimmt. Weitere Informationen zu den Attributeigenschaften finden Sie unter [Attribute und Attributhierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
 Aufgrund von Über-/Unterordnungsbeziehungen zwischen Ebenen in einer Über-/Unterordnungshierarchie können einige Nichtblattelemente jedoch auch Daten enthalten, die von zugrunde liegenden Datenquellen abgeleitet sind, zusätzlich zu den aus untergeordneten Elementen aggregierten Daten.  
  
## <a name="dimension-schema"></a>Dimensionsschema  
 Das Dimensionsschema einer Über-/Unterordnungshierarchie hängt von einer auf sich selbst verweisenden Beziehung in der Dimensionshaupttabelle ab. Das folgende Diagramm veranschaulicht beispielsweise die **DimOrganization** -Dimensionshaupttabelle in der Beispieldatenbank [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] .  
  
 ![Sich selbst verweisende Join in der DimOrganization-Tabelle](../dev-guide/media/dimorganization.gif "sich selbst verweisende Join in der DimOrganization-Tabelle")  
  
 In dieser Dimensionshaupttabelle verfügt die Spalte **ParentOrganizationKey** über eine Fremdschlüsselbeziehung mit der Primärschlüsselspalte **OrganizationKey** . Mit anderen Worten: Jeder Datensatz in dieser Tabelle kann durch eine Über-/Unterordnungsbeziehung mit einem anderen Datensatz in der Tabelle verknüpft werden. Diese Art von Selbstjoin wird im Allgemeinen zum Darstellen von Organisationsentitätsdaten verwendet, z. B. für die Verwaltungsstruktur von Mitarbeitern in einer Abteilung.  
  
## <a name="hierarchies-and-levels"></a>Hierarchien und Ebenen  
 Dimensionen, die nicht über eine Über-/Unterordnungsbeziehung verfügen, erstellen Hierarchien, indem Attribute gruppiert und sortiert werden. Diese Dimensionen leiten die Ebenennamen für ihre Hierarchien aus den Attributnamen ab.  
  
 Dagegen erstellen über- und untergeordnete Dimensionen ihre Über-/Unterordnungshierarchien, indem die in der Dimensionshaupttabelle enthaltenen Daten überprüft und dann die Über-/Unterordnungsbeziehungen zwischen den Datensätzen in der Tabelle ausgewertet werden. Weitere Informationen zu Über-/Unterordnungshierarchien finden Sie unter [Benutzerhierarchien](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).  
  
 Über-/Unterordnungshierarchien leiten die Namen für die Ebenen in einer Über-/Unterordnungshierarchie nicht von den Attributen ab, die zum Erstellen der Hierarchie verwendet werden. Stattdessen erstellen diese Dimensionen die Ebenennamen automatisch mithilfe eines Ausdrucks der naming-Vorlage eine Zeichenfolge können Sie durch Angeben der Ebene des übergeordneten Attributs, das steuert, wie das Attribut die Attributhierarchie generiert. Weitere Informationen zum Festlegen der Benennungsvorlage für ein übergeordnetes Attribut finden Sie unter [Attribute und Attributhierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="data-members"></a>Datenelemente  
 Normalerweise enthalten Blattelemente in einer Dimension Daten, die direkt aus den zugrunde liegenden Datenquellen abgeleitet wurden, Nichtblattelemente hingegen enthalten von Aggregationen abgeleitete Daten, die für untergeordnete Elemente ausgeführt wurden.  
  
 Allerdings können Über-/Unterordnungshierarchien über Nichtblattelemente verfügen, deren Daten von zugrunde liegenden Datenquellen abgeleitet sind, zusätzlich zu den aus untergeordneten Elementen aggregierten Daten. Für diese Nicht-Blattelemente in einer Über-/Unterordnungshierarchie können spezielle vom System generierte untergeordnete Elemente erstellt werden, die die Daten der zugrunde liegenden Faktentabelle enthalten. Diese als *Datenelemente*bezeichneten speziellen untergeordneten Elemente enthalten einen Wert, der direkt einem Nichtblattelement zugeordnet und unabhängig vom zusammenfassenden Wert ist, der aus den nachfolgenden Elementen des Nichtblattelements berechnet wird. Weitere Informationen zu Datenelementen finden Sie unter [Attribute in über- und untergeordneten Hierarchien](parent-child-dimension-attributes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute in über- und untergeordneten Hierarchien](parent-child-dimension-attributes.md)   
 [Eigenschaften von Datenbankdimensionen](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
