---
title: Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bd5ce45952b88c21b9f5aa1a2f2f46de00428b68
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011783"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint
  Die Websitesammlungsfunktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden in der Regel standardmäßig aktiviert, nachdem Sie das [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]-Add-In für SharePoint-Produkte installiert haben. In einigen Situationen müssen Sie die Funktionen manuell aktivieren.  
  
 Wenn Sie nach der Installation des SharePoint-Produkts das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010-Produkte installieren, werden die Berichtsserverintegrationsfunktion und die Power View-Integrationsfunktion nur für Stammwebsitesammlungen aktiviert. Für andere Websitesammlungen müssen Sie die Funktionen manuell aktivieren. Wenn Sie z. B. eine Websitesammlung von **http://[Mein Servername]/Websites/[Websitesammlungsname]** besitzen, müssen Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Websitesammlungsfunktionen manuell aktivieren.  
  
 Wenn keine Stammwebsitesammlung vorhanden ist, wird vom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In ungefähr folgende Meldung protokolliert.  
  
 "SharePoint Web App 80 besitzt keine Stammwebsitesammlung"  
  
 Die Nachricht wird finden Sie in der Add-in-Installationsprotokoll "RS_SP_ # .log" wobei # eine inkrementelle Zahl steht. Die Protokolldatei befindet sich im temporären Ordner des aktuellen Benutzers, z. B. C:\Benutzer\\[Benutzername]\AppData\Local\Temp. Weitere Informationen zu Protokollierungsoptionen mit dem Add-in finden Sie unter [installieren oder deinstallieren Sie das Reporting Services-Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 In diesem Thema:  
  
-   [So aktivieren Sie die Websitesammlungsfunktion für die Berichtsserver- und Power View-Integration:](#bkmk_features)  
  
-   [So aktivieren oder deaktivieren Sie die Websitesammlungsfunktion für die Berichtsserver-Zentraladministration:](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> So aktivieren Sie die Websitesammlungsfunktion für die Berichtsserver- und Power View-Integration:  
  
1.  Öffnen Sie den Browser für die Website, auf der die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen aktiviert werden sollen.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste **Berichtsserver-Integrationsfunktion** oder **Funktion zur Power View-Integration** .  
  
6.  Klicken Sie auf **Aktivieren**.  
  
 Verwenden Sie zum Deaktivieren der Funktionen die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt auf **Aktivieren**.  
  
##  <a name="bkmk_centraladmin"></a> So aktivieren oder deaktivieren Sie die Websitesammlungsfunktion für die Berichtsserver-Zentraladministration:  
  
1.  Öffnen Sie den Browser für die SharePoint-Zentraladministration.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste die Funktion **Berichtsserver-Zentraladministration** .  
  
6.  Klicken Sie auf **Aktivieren**.  
  
 Verwenden Sie zum Deaktivieren der Funktion die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt **Aktivieren**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem die Funktion aktiviert wurde, können Sie die Serverintegration fortsetzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
