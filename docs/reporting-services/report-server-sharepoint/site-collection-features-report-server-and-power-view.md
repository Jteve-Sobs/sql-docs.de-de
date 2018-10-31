---
title: Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint | Microsoft-Dokumentation
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e40163fe08b451e59dc28915002079b80e987e6f
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021184"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Die Websitesammlungsfunktionen von Reporting Services werden standardmäßig aktiviert, nachdem Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]-Add-In für SharePoint-Produkte installiert haben. In einigen Situationen müssen Sie die Funktionen manuell aktivieren.  

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

 Wenn Sie nach der Installation des SharePoint-Produkts das Reporting Services-Add-In für SharePoint 2010-Produkte installieren, werden die Berichtsserverintegrationsfunktion und die Power View-Integrationsfunktion nur für Stammwebsitesammlungen aktiviert. Für andere Websitesammlungen müssen Sie die Funktionen manuell aktivieren. Wenn Sie z.B. eine Websitesammlung wie **http://[Mein Servername]/sites/[Websitesammlungsname]** besitzen, müssen Sie die Reporting Services-Websitesammlungsfunktionen manuell aktivieren.  
  
 Wenn keine Stammwebsitesammlung vorhanden ist, wird vom Reporting Services-Add-In ungefähr folgende Meldung protokolliert.  
  
 "SharePoint Web App 80 besitzt keine Stammwebsitesammlung"  
  
 Die Meldung befindet sich im Add-In-Installationsprotokoll „RS_SP_#.log“, wobei „#“ für eine inkrementelle Zahl steht. Die Protokolldatei befindet sich im temporären Ordner des aktuellen Benutzers, z.B. C:\Benutzer\\[Benutzername]\AppData\Local\Temp. Weitere Informationen zu Anmeldeoptionen mit dem Add-In finden Sie unter [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>Aktivieren der Websitesammlungsfunktion für die Berichtsserver- und Power View-Integration
  
1.  Öffnen Sie den Browser für die Website, auf der die Reporting Services-Funktionen aktiviert werden sollen.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste **Berichtsserver-Integrationsfunktion** oder **Funktion zur Power View-Integration** .  
  
6.  Klicken Sie auf **Aktivieren**.  
  
 Verwenden Sie zum Deaktivieren der Funktionen die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt auf **Aktivieren**.  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>Aktivieren oder Deaktivieren der Websitesammlungsfunktion für die Reporting Services-Zentraladministration
  
1.  Öffnen Sie den Browser für die SharePoint-Zentraladministration.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste die Funktion **Berichtsserver-Zentraladministration** .  
  
6.  Klicken Sie auf **Aktivieren**.  
  
 Verwenden Sie zum Deaktivieren der Funktion die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt **Aktivieren**.  
  
## <a name="next-steps"></a>Nächste Schritte

Nachdem die Funktion aktiviert wurde, können Sie die Serverintegration fortsetzen.

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
