---
title: Attribute in über-/ Unterordnungshierarchien | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6b6c10c8b1c7f311f7ba5e876c1b8d96c9e9701
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165421"
---
# <a name="parent-child-dimension-attributes"></a>Über- und untergeordnete Dimensionsattribute
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]wird im Allgemeinen eine generelle Annahme hinsichtlich des Inhalts von Elementen in einer Dimension vorausgesetzt. Blattelemente enthalten Daten, die direkt aus den zugrunde liegenden Datenquellen abgeleitet wurden, Nichtblattelemente enthalten von Aggregationen abgeleitete Daten, die für untergeordnete Elemente ausgeführt wurden.  
  
 In einer Über-/Unterordnungshierarchie können einige Nichtblattelemente jedoch auch Daten enthalten, die von zugrunde liegenden Datenquellen abgeleitet sind, zusätzlich zu den aus untergeordneten Elementen aggregierten Daten. Für diese Nichtblattelemente in einer Über-/Unterordnungshierarchie werden spezielle vom System generierte untergeordnete Elemente erstellt, die die Daten der zugrunde liegenden Faktentabelle enthalten. Sie werden als *Datenelemente*bezeichnet und enthalten einen Wert, der direkt einem Nichtblattelement zugeordnet und unabhängig vom zusammenfassenden Wert ist, der aus den nachfolgenden Elementen des Nichtblattelements berechnet wird.  
  
 Datenelemente sind nur für Dimensionen mit Über-/Unterordnungshierarchien verfügbar und nur dann sichtbar, wenn das übergeordnete Attribut dies zulässt. Sie können den Dimensions-Designer verwenden, um die Sichtbarkeit von Datenelementen zu steuern. Legen Sie die Eigenschaft **MembersWithData** für das übergeordnete Attribut auf **NonLeafDataVisible**fest, um die Datenelemente verfügbar zu machen. Legen Sie die Eigenschaft **MembersWithData** des übergeordneten Attributs auf **NonLeafDataHidden**fest, um Datenelemente auszublenden, die im übergeordneten Attribut enthalten sind.  
  
 Mit dieser Einstellung wird das normale Aggregationsverhalten von Nichtblattelementen nicht überschrieben, denn das Datenelement ist für Aggregationszwecke stets als untergeordnetes Element enthalten. Das normale Aggregationsverhalten kann jedoch durch eine benutzerdefinierte Rollupformel überschrieben werden. Mithilfe der MDX-Funktion (Multidimensional Expressions) [DataMember](../../mdx/datamember-mdx.md) können Sie unabhängig vom Wert der **MembersWithData** -Eigenschaft auf den Wert des dazugehörigen Datenelements zugreifen.  
  
 Die **MembersWithDataCaption** -Eigenschaft des übergeordneten Attributs stellt für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Benennungsvorlage für die Generierung von Elementnamen für Datenelemente bereit.  
  
## <a name="using-data-members"></a>Verwenden von Datenelementen  
 Datenelemente sind hilfreich bei der Aggregation von Measures gemäß der Organisationsdimensionen mit Über-/Unterordnungshierarchien. Das folgende Diagramm zeigt z. B. eine Dimension, die drei Ebenen enthält, die die Bruttoumsätze von Produkten darstellen. Die erste Ebene zeigt die Bruttoumsätze für alle Vertriebsmitarbeiter. Die zweite Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmanagern sortiert, und die dritte Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmitarbeitern sortiert.  
  
 ![GROSS sales Volume-Dimension mit drei Ebenen](../../analysis-services/multidimensional-models/media/agdatamember1.gif "Gross sales Volume-Dimension mit drei Ebenen")  
  
 Normalerweise würde der Wert des Elements Sales Manager 1 durch Aggregieren der Werte der Elemente Salesperson 1 und Salesperson 2 abgeleitet. Da jedoch auch Sales Manager 1 Produkte verkaufen kann, kann dieses Element auch Daten enthalten, die von der Faktentabelle abgeleitet sind, da möglicherweise Bruttoumsätze Sales Manager 1 zugeordnet sind.  
  
 Außerdem können die einzelnen Provisionen für jeden Vertriebsmitarbeiter unterschiedlich sein. In diesem Fall werden zwei unterschiedliche Skalen zum Berechnen der Provisionen für die einzelnen Bruttoumsätze der Vertriebsmanager im Gegensatz zum gesamten Bruttoumsatz ihres Vertriebspersonals verwendet. Deshalb ist die Möglichkeit wichtig, auf die Daten der zugrunde liegenden Faktentabelle für Nicht-Blattelemente zuzugreifen. Die MDX-Funktion **DataMember** kann zum Abrufen der einzelnen Bruttoumsätze des Sales Manager 1-Elements verwendet werden, und ein benutzerdefinierter Rollupausdruck kann verwendet kann, um Datenelemente aus dem aggregierten Wert des Sales Manager 1-Elements auszuschließen, wodurch die Bruttoumsätze der diesem Element zugeordneten Vertriebsmitarbeiter bereitgestellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaftenverweis](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [Über- und untergeordnete Dimensionen](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  
