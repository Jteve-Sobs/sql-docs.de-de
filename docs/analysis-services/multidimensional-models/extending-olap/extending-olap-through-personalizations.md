---
title: Erweitern von OLAP durch personalisierungen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c49d2d350504daef36d0fbe861b26ccf220e7a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208895"
---
# <a name="extending-olap-through-personalizations"></a>Erweitern von OLAP durch Personalisierungen
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Analysis Services stellt viele systeminterne Funktionen für die Verwendung mit den Sprachen MDX (Multidimensional Expressions) und Data Mining Extensions (DMX). Diese Funktionen sind ebenso für herkömmliche statistische Berechnungen wie zum Durchlaufenden der Elemente einer Hierarchie geeignet. Wie bei jedem anderen komplexen und robusten Produkt, ist es jedoch immer die Notwendigkeit, die die Funktionalität des Produkts zu erweitern.  
  
 Deshalb können Sie einer Instanz des Diensts mithilfe der Analysis Services Assemblys und Personalisierungserweiterungen hinzufügen, um die Geschäftsanforderungen zu erfüllen, wenn die Standardfunktionalität einmal nicht ausreichen sollte.  
  
## <a name="assemblies"></a>Assemblys  
 Assemblys können Sie die Geschäftsfunktionalität von MDX und DMX erweitern. Sie integrieren die gewünschte Funktionalität in eine Bibliothek, z. B. eine DLL (Dynamic Link Library), und fügen dann die Bibliothek als Assembly einer Instanz von Analysis Services oder einer Analysis Services-Datenbank hinzu. Die öffentlichen Methoden in der Bibliothek werden dann als benutzerdefinierte Funktionen für MDX- und DMX-Ausdrücke, Prozeduren, Berechnungen, Aktionen und Clientanwendungen verfügbar gemacht.  
  
## <a name="personalized-extensions"></a>Personalisierungserweiterungen  
 SQL Server Analysis Services-Personalisierungserweiterungen sind die Grundlage für das Konzept der Implementierung einer Plug-In-Architektur. Analysis Services-Personalisierungserweiterungen stellen eine einfache und elegante Modifikation der vorhandenen Architektur der verwalteten Assembly dar. Sie werden im Analysis Services-<xref:Microsoft.AnalysisServices.AdomdServer>-Objektmodell, in der MDX-Syntax (Multidimensional Expressions) und in den Schemarowsets zur Verfügung gestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Personalisierungserweiterungen für Analysis Services](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
  
