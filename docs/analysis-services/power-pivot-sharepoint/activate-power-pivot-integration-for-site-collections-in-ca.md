---
title: Aktivieren der PowerPivot-Integration für Websitesammlungen in der Zertifizierungsstelle | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 564ff616ec13b5f7f669db4cf6402114175f5670
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68164465"
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>Aktivieren der PowerPivot-Integration für Websitesammlungen in der Zertifizierungsstelle
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Funktion zur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Integration für bestimmte Websitesammlungen muss aktiviert werden, wenn Sie die Installationsoption „Vorhandene Farm“ zur Installation von SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint verwendet haben. Wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint mit der Option „Neuer Server“ installiert haben, können Sie diese Aufgabe überspringen, da SQL Server-Setup bereits die Funktion zur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Integration für die Stammwebsitesammlung aktiviert hat, als die Bereitstellung konfiguriert wurde.  
  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung ist erforderlich, um Ihren Websites Anwendungsseiten und Vorlagen zur Verfügung zu stellen, einschließlich Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog- und Datenfeed-Bibliotheken.  
  
 Sie müssen die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Integration für jede Websitesammlung aktivieren, die die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Abfrageverarbeitung unterstützt.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Sie müssen Administrator einer Websitesammlung sein.  
  
## <a name="activate-power-pivot-features"></a>Aktivieren von PowerPivot-Funktionen  
  
1.  Klicken Sie auf einer SharePoint-Website auf **Websiteaktionen**.  
  
     Standardmäßig wird auf SharePoint-Webanwendungen über Port 80 zugegriffen. Dies bedeutet, dass Sie häufig eine SharePoint-Website zugreifen können, durch Eingabe von http://\<Computername > um die Stammwebsitesammlung zu öffnen.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie unter Websitesammlungsverwaltung auf **Websitesammlungsfeatures**.  
  
4.  Scrollen Sie auf der Seite nach unten, bis Sie **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Integration Site Collection Feature**(Power Pivot-Integrationsfunktion für Webseitensammlungen) finden.  
  
5.  Klicken Sie auf **Aktivieren**.  
  
6.  Wiederholen Sie den Schritt für zusätzliche Websitesammlungen, indem Sie jede Website öffnen und auf **Websiteaktionen**klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Anfängliche Konfiguration (PowerPivot für SharePoint)](http://msdn.microsoft.com/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Installation von PowerPivot für SharePoint 2010](http://msdn.microsoft.com/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  
