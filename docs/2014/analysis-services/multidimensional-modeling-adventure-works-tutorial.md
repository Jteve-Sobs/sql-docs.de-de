---
title: Mehrdimensionale Modellierung (Adventure Works-Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebbb4e6510f8896b9c931d6a582eaf6b3e2b0c24
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62703127"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a>Mehrdimensionale Modellierung (Adventure Works-Lernprogramm)
  Willkommen beim [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Lernprogramm. In diesem Lernprogramm wird beschrieben, wie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] zum Entwickeln und Bereitstellen eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekts verwendet wird, wobei das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] für alle Beispiele verwendet wird.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
-   Definieren von Datenquellen, Datenquellensichten, Dimensionen, Attributen, Attributbeziehungen, Hierarchien und Cubes in einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt innerhalb von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Anzeigen von Cube- und Dimensionsdaten durch Bereitstellen des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekts für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]und anschließendes Verarbeiten der bereitgestellten Objekte, um sie mit Daten aus der zugrunde liegenden Datenquelle aufzufüllen.  
  
-   Ändern von Measures, Dimensionen, Hierarchien, Attributen und Measuregruppen im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt und anschließendes Bereitstellen von inkrementellen Änderungen für den bereitgestellten Cube auf dem Entwicklungsserver.  
  
-   Definieren von Berechnungen, Key Performance Indicators (KPIs), Aktionen, Perspektiven, Übersetzungen und Sicherheitsrollen innerhalb eines Cubes.  
  
 Dieses Lernprogramm wird mit einer Szenariobeschreibung bereitgestellt, damit Sie den Kontext dieser Lektionen besser verstehen können. Weitere Informationen finden Sie unter [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie benötigen Beispieldaten, Beispielprojektdateien und Software, um alle Lektionen in diesem Lernprogramm abzuschließen. Anweisungen zum Suchen und Installieren der erforderlichen Komponenten für dieses Lernprogramm finden Sie unter [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).  
  
 Darüber hinaus müssen die folgenden Berechtigungen vorhanden sein, um das Lernprogramm erfolgreich abzuschließen:  
  
-   Sie müssen ein Mitglied der lokalen Administratorgruppe auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Computer oder ein Mitglied der Serveradministratorrolle in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz sein.  
  
-   Sie benötigen Leseberechtigungen für die **AdventureWorksDW2012** -Beispieldatenbank. Diese Beispieldatenbank ist für die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Version geeignet.  
  
## <a name="lessons"></a>Lektionen  
 Dieses Lernprogramm umfasst die folgenden Lektionen:  
  
|Lektion|Für den Abschluss voraussichtlich benötigte Zeit|  
|------------|--------------------------------|  
|[Lektion 1: Definieren einer Datenquellensicht innerhalb eines Analysis Services-Projekts](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 Minuten|  
|[Lektion 2: Definieren und Bereitstellen eines Cubes](lesson-2-defining-and-deploying-a-cube.md)|30 Minuten|  
|[Lektion 3: Ändern von Maßen, Attributen und Hierarchien](lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 Minuten|  
|[Lektion 4: Definieren von erweiterten Attributen und Dimensionseigenschaften](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 Minuten|  
|[Lesson 5: Definieren von Beziehungen zwischen Dimensionen und Measuregruppen](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 Minuten|  
|[Lektion 6: Definieren von Berechnungen](lesson-6-defining-calculations.md)|45 Minuten|  
|[Lektion 7: Definieren Key Performance Indicators &#40;KPIs&#41;](lesson-7-defining-key-performance-indicators-kpis.md)|30 Minuten|  
|[Lektion 8: Definieren von Aktionen](lesson-8-defining-actions.md)|30 Minuten|  
|[Lektion 9: Definieren von Perspektiven und Übersetzungen](lesson-9-defining-perspectives-and-translations.md)|30 Minuten|  
|[Lektion 10: Definieren von Administratorrollen](lesson-10-defining-administrative-roles.md)|15 Minuten|  
  
> [!NOTE]  
>  Die in diesem Lernprogramm erstellte Cubedatenbank ist eine vereinfachte Version des mehrdimensionalen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Modellprojekts, das Teil der Adventure Works-Beispieldatenbanken ist, die auf der Codeplex-Website zum Download verfügbar sind. Die Lernprogrammversion der mehrdimensionalen Adventure Works-Datenbank ist vereinfacht, um den Fokus auf die Fähigkeiten zu richten, die Sie vorrangig erwerben möchten. Nachdem Sie das Lernprogramm abgeschlossen haben, können Sie das mehrdimensionale Modellprojekt selbst untersuchen, um Ihr Verständnis der mehrdimensionalen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Modellierung zu vertiefen.  
  
## <a name="next-step"></a>Nächster Schritt  
 Um das Lernprogramm zu starten, gehen Sie zur ersten Lektion: [Lektion 1: Definieren einer Datenquellensicht innerhalb eines Analysis Services-Projekts](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
