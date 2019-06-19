---
title: 'Lektion 8: Definieren von Aktionen | Microsoft-Dokumentation'
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2f233bab0c90abf41ab8fbef923e7c7b920ff2c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403672"
---
# <a name="lesson-8-defining-actions"></a>Lektion 8: Definieren von Aktionen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

In dieser Lektion erfahren Sie, wie Sie Aktionen in Ihrem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt definieren können. Eine Aktion bezeichnet einfach eine in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeicherte MDX-Anweisung (Multidimensional Expressions), die in Clientanwendungen integriert und von Benutzern gestartet werden kann.  
  
> [!NOTE]  
> Für alle Lektionen in diesem Lernprogramm sind abgeschlossene Projekte online verfügbar. Sie können jede Lektion aufrufen, indem Sie ein abgeschlossenes Projekt aus der vorherigen Lektion als Ausgangspunkt verwenden. [Klicken Sie hier](http://go.microsoft.com/fwlink/?LinkID=221866) , um die Beispielprojekte für dieses Lernprogramm herunterzuladen.  
  
[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die in der folgenden Tabelle beschriebenen Typen von Aktionen.  
  
|||  
|-|-|  
|CommandLine|Führt einen Befehl an der Eingabeaufforderung aus.|  
|Dataset|Gibt ein Dataset an eine Clientanwendung zurück.|  
|Drillthrough ausführen|Gibt eine Drillthroughanweisung als Ausdruck zurück, den der Client zur Rückgabe eines Rowsets ausführt.|  
|Html|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|Proprietär|Führt einen Vorgang über eine Schnittstelle aus, die nicht in dieser Tabelle aufgelistet ist.|  
|Bericht|Übermittelt eine parametrisierte, URL-basierte Anforderung an einen Berichtsserver und gibt einen Bericht an eine Clientanwendung zurück.|  
|Rowset|Gibt ein Rowset an eine Clientanwendung zurück.|  
|Anweisung|Gibt einen OLE DB-Befehl zurück.|  
|URL|Zeigt eine dynamische Webseite in einem Internetbrowser an.|  
  
Aktionen ermöglichen es Benutzern, eine Anwendung zu starten oder andere Schritte innerhalb des Kontexts eines bestimmten Elements auszuführen. Weitere Informationen finden Sie unter [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md) und [Aktionen in mehrdimensionalen Modellen](../multidimensional-models/actions-in-multidimensional-models.md).  
  
> [!NOTE]  
> Beispielaktionen finden Sie in den Aktionsbeispielen auf der Registerkarte Vorlagen im Bereich Berechnungstools oder in den Beispielen des [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW-Data Warehouse-Beispiels. Weitere Informationen zum Installieren dieser Datenbank finden Sie unter [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).  
  
Diese Lektion enthält den folgenden Task:  
  
[Definieren und Verwenden einer Drillthroughaktion](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
In diesem Task definieren, verwenden und ändern Sie eine Drillthroughaktion über die Faktendimensionsbeziehung, die Sie zu einem früheren Zeitpunkt in diesem Lernprogramm definiert haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 9: Definieren von Perspektiven und Übersetzungen](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Siehe auch  
[Analysis Services-Tutorialszenario](analysis-services-tutorial-scenario.md)  
[Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md)  
[Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[Aktionen in mehrdimensionalen Modellen](../multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
