---
title: Überprüfen von Cube- und Dimensionseigenschaften | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 97b12ad51affaebb87f152938bdfbfae16bd8900
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403732"
---
# <a name="lesson-2-4---reviewing-cube-and-dimension-properties"></a>Lektion 2.4: Überprüfen von Cube- und Dimensionseigenschaften
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Nachdem Sie einen Cube definiert haben, können Sie die Ergebnisse mit dem Cube-Designer überprüfen. In der folgenden Aufgabe überprüfen Sie die Struktur des Cubs im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Projekt.  
  
### <a name="to-review-cube-and-dimension-properties-in-cube-designer"></a>So überprüfen Sie Cube- und Dimensionseigenschaften im Cube-Designer  
  
1.  Zum Öffnen des Cube-Designers doppelklicken Sie auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten des Projektmappen-Explorers.  
  
2.  Erweitern Sie im Cube-Designer auf der Registerkarte **Cubestruktur** im Bereich **Measures** die Measuregruppe **Internet Sales** , um die definierten Measures anzuzeigen.  
  
    Durch Ziehen können Sie die Reihenfolge der Measures ändern. Die Reihenfolge hat Auswirkungen auf die Reihenfolge, in der bestimmte Clientanwendungen diese Measures anordnen. Die Measuregruppe und jedes enthaltene Measure weisen Eigenschaften auf, die Sie im Eigenschaftenfenster bearbeiten können.  
  
3.  Überprüfen Sie im Cube-Designer auf der Registerkarte **Cubestruktur** im Bereich **Dimensionen** die Cubedimensionen des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cubes.  
  
    Zwar wurden auf der Datenbankebene nur drei Dimensionen erstellt, wie im Projektmappen-Explorer angezeigt; der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube enthält jedoch fünf Cubedimensionen. Der Cube enthält mehr Dimensionen als die Datenbank, da die Datenbankdimension "Date" als Grundlage für drei separate datumsbezogene Cubedimensionen verwendet wird, basierend auf unterschiedlichen datumsbezogenen Fakten in der Faktentabelle. Diese datumsbezogenen Dimensionen werden auch *Dimensionen mit unterschiedlichen Rollen*genannt. Mit den drei datumsbezogenen Cubedimensionen können Benutzer den Cube anhand von drei separaten Fakten dimensionieren, die sich auf die einzelnen Produktverkäufe beziehen: das Produktbestelldatum, das Fälligkeitsdatum und das Lieferdatum für die Bestellung. Durch das Wiederverwenden einer einzelnen Datenbankdimension für mehrere Cubedimensionen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wird die Dimensionsverwaltung vereinfacht sowie die Speicherplatzverwendung und die Gesamtverarbeitungszeit reduziert.  
  
4.  Erweitern Sie im **Dimensionen** -Bereich der Registerkarte **Cubestruktur** die **Customer**-Dimension, und klicken Sie dann auf **Customer bearbeiten** , um die Dimension im Dimensions-Designer zu öffnen.  
  
    Dimensions-Designer enthält folgende Registerkarten: **Dimensionsstruktur**, **Attributbeziehungen**, **Übersetzungen**, und **Browser**. Beachten Sie, dass die **Dimensionsstruktur** Registerkarte enthält drei Bereiche: **Attribute**, **Hierarchien**, und **Datenquellensicht**. Die Attribute, die die Dimension enthält, werden im Bereich **Attribute** angezeigt. Weitere Informationen finden Sie unter [Dimensionsattributeigenschaftenverweis](../multidimensional-models/dimension-attribute-properties-reference.md), [Erstellen von benutzerdefinierten Hierarchien](../multidimensional-models/user-defined-hierarchies-create.md) und [Definieren von Attributbeziehungen](../multidimensional-models/attribute-relationships-define.md).  
  
5.  Um zum Cube-Designer zu wechseln, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten, und klicken Sie anschließend auf **Designer anzeigen**.  
  
6.  Klicken Sie im Cube-Designer auf die Registerkarte **Dimensionsverwendung** .  
  
    In dieser Ansicht des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cubes sehen Sie die von der Internet Sales-Measuregruppe verwendeten Cubedimensionen. Außerdem können Sie den Typ der Beziehung zwischen jeder Dimension und den einzelnen Measuregruppen, in denen sie verwendet wird, definieren.  
  
7.  Klicken Sie auf die Registerkarte **Partitionen** .  
  
    Vom Cube-Assistenten wird eine einzelne Partition für den Cube definiert. Dabei wird der MOLAP-Speichermodus (Multidimensional Online Analytical Processing) ohne Aggregationen verwendet. Mit MOLAP werden alle Daten der Blattebene und alle Aggregationen innerhalb des Cubes gespeichert. Dies optimiert die Leistung. Aggregationen sind im Voraus berechnete Zusammenfassungen von Daten, mit denen die Abfrageantwortzeit verbessert werden kann, da die Antworten schon vorhanden sind, wenn Fragen gestellt werden. Auf der Registerkarte **Partitionen** können Sie zusätzliche Partitionen, Speichereinstellungen und Rückschreibeeinstellungen definieren. Weitere Informationen zu Partitionen finden Sie unter [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) und [Aggregationen und Aggregationsentwürfe](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
8.  Klicken Sie auf die Registerkarte **Browser** .  
  
    Der Cube kann nicht durchsucht werden, da er noch nicht in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitgestellt wurde. Zum aktuellen Zeitpunkt besteht der Cube im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Projekt nur aus einer Cubedefinition, die Sie in einer beliebigen Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitstellen können. Beim Bereitstellen und Verarbeiten eines Cubes erstellen Sie die definierten Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und füllen sie mit Daten aus den zugrunde liegenden Datenquellen auf.  
  
9. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Analysis Services Tutorial** im **Cubes** -Knoten und anschließend auf **Code anzeigen**. Sie müssen möglicherweise einen Moment warten.  
  
    Der XML-Code für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube wird auf der Registerkarte **[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial.cube [XML]** angezeigt. Es handelt sich um den tatsächlichen Code, mit dem der Cube bei der Bereitstellung in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt wird. Weitere Informationen finden Sie unter [Anzeigen des XML für ein Analysis Services-Projekt &#40;SSDT&#41;](../multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).  
  
10. Schließen Sie die Registerkarte mit dem XML-Code.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Bereitstellen eines Analysis Services-Projekts](lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a>Siehe auch  
[Durchsuchen von Dimensionsdaten im Dimensions-Designer](../multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  
  
