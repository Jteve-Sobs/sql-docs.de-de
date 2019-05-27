---
title: Definieren eines Standardelements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959645223eacec6c000ddbfa23615b7949d10d5a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66077420"
---
# <a name="define-a-default-member"></a>Definieren eines Standardelements
  Das Standardelement einer Attributhierarchie wird zum Auswerten von Ausdrücken verwendet, wenn eine Attributhierarchie nicht in einer Abfrage enthalten ist. Das Standardelement wird ignoriert, wenn eine Abfrage eine Attributhierarchie oder eine benutzerdefinierte Hierarchie einschließt, die das Quellattribut der Attributhierarchie enthält. Der Grund dafür ist, dass hier das in der Abfrage angegebene Element verwendet wird.  
  
 Das Standardelement einer Attributhierarchie wird festgelegt, indem ein Attributelement als `DefaultMember`-Eigenschaftswert der Attributhierarchie angegeben wird. Diese Eigenschaft legen Sie auf der Registerkarte Dimensionsstruktur des Dimensions-Designers oder im Kalkulationsskript auf der Registerkarte Berechnung des Cube-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fest. Sie können die `DefaultMember`-Eigenschaft auch für eine Sicherheitsrolle angeben (und damit das für die Dimension festgelegte Standardelement überschreiben). Öffnen Sie dazu während der Definition der Dimensionssicherheit die Registerkarte Dimensionsdaten. Wenn Sie Namensauflösungsprobleme in folgenden Situationen vermeiden möchten, definieren Sie das Standardelement im MDX-Skript des Cubes: wenn der Cube mehr als einmal auf eine Datenbankdimension verweist; wenn die Dimension im Cube einen anderen Namen aufweist als die Dimension in der Datenbank; wenn Sie in verschiedenen Cubes verschiedene Standardelemente verwenden möchten.  
  
 Das Standardelement eines Attributs wird zum Auswerten von Ausdrücken verwendet, wenn ein Attribut nicht in einer Abfrage enthalten ist. Das Standardelement eines Attributs wird durch die `DefaultMember`-Eigenschaft des Attributs angegeben. Wenn eine Hierarchie aus einer Dimension in einer Abfrage enthalten ist, werden alle Standardelemente von Attributen ignoriert, die Ebenen in der Hierarchie entsprechen. Ist keine Hierarchie aus einer Dimension in einer Abfrage enthalten, werden für alle Attribute in der Dimension Standardelemente verwendet.  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>Auflösen des Standardelements, wenn kein Standardelement angegeben ist  
 Wird für eine Attributhierarchie kein Standardelement angegeben, und kann die Attributhierarchie aggregiert werden (die `IsAggregatable`-Eigenschaft des Attributs ist auf `True` festgelegt), ist das (Alle)-Element das Standardelement. Wird kein Standardelement angegeben, und kann die Attributhierarchie nicht aggregiert werden (die `IsAggregatable`-Eigenschaft des Attributs ist auf `False` festgelegt), wird ein Standardelement aus der obersten Ebene der Attributhierarchie ausgewählt.  
  
## <a name="specifying-the-default-member"></a>Festlegen des Standardelements  
 Jedes Attribut in einer Dimension [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] besitzt ein Standardelement, die Sie angeben können, mit der `DefaultMember` -Eigenschaft für ein Attribut. Diese Einstellung wird zum Auswerten von Ausdrücken verwendet, wenn ein Attribut nicht in einer Abfrage enthalten ist. Legt eine Abfrage eine Hierarchie in einer Dimension fest, werden die Standardelemente für die Attribute in der Hierarchie ignoriert. Wenn eine Abfrage keine Hierarchie in einer Dimension fest, wird die `DefaultMember` -Einstellungen für Dimensionsattribute werden wirksam.  
  
 Wenn die `DefaultMember` -Einstellung für ein Attribut leer und die zugehörige `IsAggregatable` -Eigenschaftensatz auf `True`, gilt das alle-Element als Standardelement. Wenn die `IsAggregatable` -Eigenschaftensatz auf `False`, das Standardelement ist das erste Element der ersten sichtbaren Ebene.  
  
 Die `DefaultMember` -Einstellung für ein Attribut für jede Hierarchie gilt in der das Attribut beteiligt ist. Sie können für verschiedene Hierarchien in einer Dimension keine unterschiedlichen Einstellungen verwenden. Wenn beispielsweise das Element [1998] das Standardelement für ein [Year]-Attribut ist, gilt diese Einstellung für jede Hierarchie in der Dimension. Die `DefaultMember` Einstellung in diesem Fall nicht [1998] in einer Hierarchie und [1997] in einer anderen Hierarchie.  
  
 Wenn Sie ein Standardelement für eine bestimmte Ebene in einer Hierarchie definieren, das nicht auf natürliche Weise aggregiert, müssen Sie in allen Ebenen über dieser Ebene in der Hierarchie Standardelemente definieren. In der Hierarchie All-Ländern-Klima, können nicht Sie beispielsweise ein Standardelement für Climate definieren, wenn Sie ein Standardelement für Countries definieren. Tun Sie dies nicht, führt dies zu Abfragezeitfehlern.  
  
 Wenn Ebenen in einer Hierarchie natürlich aggregieren, können Sie ein Standardelement für ein beliebiges Attribut in der Hierarchie definieren, ohne andere Attribute in der Hierarchie berücksichtigen zu müssen. In der Hierarchie Country-Province-City können Sie beispielsweise ein Standardelement für City wie [City] definieren. [Montreal] ohne die Definition des Standardelements für State oder für das Land.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Ebene &#40;Alle&#41; für Attributhierarchien](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
