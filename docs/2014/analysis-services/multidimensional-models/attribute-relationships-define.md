---
title: Definieren Sie Attributbeziehungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecc6eefcf6fea5ee815190e1d4204a00cca60f0a
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59241238"
---
# <a name="define-attribute-relationships"></a>Definieren von Attributbeziehungen
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sind Attribute der grundlegende Baustein einer Dimension. Eine Dimension enthält einen Satz von Attributen, die auf Basis von Attributbeziehungen organisiert sind.  
  
 Für jede Tabelle in einer Dimension existiert eine Attributbeziehung, die das Schlüsselattribut der Tabelle mit anderen Attributen aus der Tabelle verknüpft. Diese Beziehung kommt zustande, wenn Sie die Dimension erstellen.  
  
 Eine Attributbeziehung bietet die folgenden Vorteile:  
  
-   Sie reduziert den für die Dimensionsverarbeitung erforderlichen Speicherplatz. Dies beschleunigt die Dimensions-, Partitions- und Abfrageverarbeitung.  
  
-   Sie erhöht die Abfrageleistung, da der Speicherzugriff beschleunigt wird und Ausführungspläne besser optimiert werden können.  
  
-   Sie führt aufgrund der Aggregationsentwurfsalgorithmen zur Auswahl effektiverer Aggregate, sofern benutzerdefinierte Hierarchien entlang den Beziehungspfaden definiert wurden.  
  
    > [!NOTE]  
    >  Weitere Informationen über die Bedeutung und Auswirkungen der Definition und Konfiguration von attributbeziehungen finden Sie im Abschnitt "Enhancing Query Performance" in der [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="attribute-relationship-considerations"></a>Überlegungen zu Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch eindeutige Attributbeziehungen zwischen Attributen definieren. Um eindeutige Attributbeziehungen zu definieren, verwenden Sie die Registerkarte **Attributbeziehungen** des Dimensions-Designers.  
  
 Jedes Attribut, das über eine ausgehende Beziehung verfügt, muss über einen eindeutigen Schlüssel relativ zu seinem verknüpften Attribut verfügen. Anders ausgedrückt darf ein Element in einem Quellattribut nur ein Element in einem verknüpften Attribut identifizieren. Betrachten Sie z. B. die Beziehung "City -> State". In dieser Beziehung ist "City" das Quellattribut und "State" das verknüpfte Attribut. Das Quellattribut ist der n-Seite, und die verknüpfte Seite entspricht der Seite "1", der viele-zu-eins-Beziehung. Der Schlüssel für das Quellattribut lautet "City + Status". Weitere Informationen finden Sie unter [Gewusst wie: Erstellen, Ändern oder Löschen einer Attributbeziehung](attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Weitere Informationen zu Eigenschaften einer Attributbeziehung finden Sie unter [Konfigurieren von Attributbeziehungseigenschaften](attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  Eine falsche Definition von Attributbeziehungen kann zu ungültigen Abfrageergebnissen führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Attributbeziehungen](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
