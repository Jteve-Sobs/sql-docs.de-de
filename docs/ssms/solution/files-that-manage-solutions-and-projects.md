---
title: Dateien zum Verwalten von Projektmappen und Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3bff8bd75d6852cc978dc63d198479a65f4ede9d
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100241"
---
# <a name="files-that-manage-solutions-and-projects"></a>Dateien zum Verwalten von Projektmappen und Projekten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 In diesem Thema werden die Dateitypen von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschrieben. Standardmäßig werden alle Projektmappen und Projekte im Verzeichnis \Meine Dokumente\SQL Server Management Studio Projects erstellt.  


## <a name="management-studio-solution-files"></a>Management Studio-Projektmappendateien  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet andere Dateitypen als [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] oder [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Dies bedeutet, dass Sie eine [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Projektmappe nicht in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] oder in Visual Studio öffnen können. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Projektmappendateien ermöglichen dem Projektmappen-Explorer, eine grafische Benutzeroberfläche zum Verwalten Ihrer Dateien anzuzeigen.  
   
|Erweiterung|Dateityp|und Beschreibung|Erstellt von|  
|-------------|-------------|---------------|--------------|  
|SSMSSLN|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Projektmappenobjekt|Stellt der Umgebung Verweise auf den Speicherort auf dem Datenträger von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Projekten, -Projektelementen und -Projektmappen bereit|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Management Studio-Projektdateien  
In derselben Weise, wie Projektmappen Projektmappendateien zum Verwalten von Objekten in einer Projektmappe enthalten, enthalten Projekte Projektdateien. Der Projektdateityp, der von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] für ein Projekt erstellt wird, hängt von der Vorlage ab, mit der das Projekt erstellt wurde. In der folgenden Tabelle werden die Dateitypen beschrieben, die für die einzelnen Projekte erstellt werden.  
   
|Erweiterung|Projektvorlage|  
|-------------|--------------------|  
|SSMSSQLPROJ|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Skriptprojekt|  
|SSMSASPROJ|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Skriptprojekt|  
   
## <a name="location-of-solution-level-files"></a>Speicherort für Dateien auf Projektmappenebene  
Standardmäßig werden Dateien auf Projektmappenebene im physischen Verzeichnis des ersten Projekts erstellt, das mit der Projektmappe erstellt wird. Sie können ein Verzeichnis für die Projektmappe angeben, indem Sie eine Projektmappe erstellen. Sie können das Verzeichnis auch angeben, wenn Sie ein neues Projekt erstellen.  
 
Wenn eine Verzeichnisstruktur vorhanden ist, die der logischen Struktur im Projektmappen-Explorer ähnelt, lassen sich Projekt- und Projektmappendateien einfacher suchen und mit anderen Entwicklern im Team gemeinsam nutzen.  
   
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwalten von Dateien mit Codierung](../../ssms/solution/manage-files-with-encoding.md)  
[Sonstige Dateien](../../ssms/solution/miscellaneous-files.md)  
[Projektmappen-Explorer](../../ssms/solution/solution-explorer.md)  
[Projektmappen &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Projekte &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
[Quellcodeverwaltung des Projektmappen-Explorers](https://msdn.microsoft.com/library/ms173879.aspx)  
  
