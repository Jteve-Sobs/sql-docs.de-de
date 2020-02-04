---
title: Veröffentlichen von Berichten auf einem Berichtsserver | Microsoft-Dokumentation
ms.date: 06/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2a2628bc5d098c32fc63d4a80bcf4c7b403a82a0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "72359407"
---
# <a name="publishing-reports-to-a-report-server"></a>Veröffentlichen von Berichten auf einem Berichtsserver
  Nachdem Sie einen Bericht oder eine Reihe von Berichten entworfen und getestet haben, können Sie die Bereitstellungsfunktionen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwenden, um die Berichte auf einem Berichtsserver zu veröffentlichen. Sie können einzelne Berichte oder ein Berichtsserverprojekt veröffentlichen, das mehrere Berichte und Datenquellen enthalten kann. Die einfachste Möglichkeit zum Veröffentlichen mehrerer Berichte ist die Veröffentlichung eines Berichtsserverprojekts. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwendet den Begriff *Bereitstellen*anstelle von *Veröffentlichen*. Die beiden Begriffe sind austauschbar.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] stellt Projektkonfigurationen für die Verwaltung der Berichtsveröffentlichung bereit. Die Konfiguration gibt den Speicherort des Berichtsservers und die Version der auf dem Berichtsserver installierten SQL Server Reporting Services an; weiter legt sie fest, ob die auf dem Berichtsserver veröffentlichten Datenquellen überschrieben werden usw. Die Konfiguration „Debug“ kann z.B. auf einem anderen Server als die „Version“-Konfiguration veröffentlichen. Zusätzlich zur Verwendung der von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] bereitgestellten Konfigurationen können Sie zusätzliche Konfigurationen erstellen.  
 
## <a name="requirements-to-publish"></a>Anforderungen für das Veröffentlichen
Die Berechtigung wird durch rollenbasierte Sicherheit bestimmt, die vom Berichtsserveradministrator definiert wird. Berechtigungen für Veröffentlichungsvorgänge werden in der Regel über die **Verleger**-Rolle gewährt.  
  
## <a name="project-configurations"></a>Projektkonfigurationen  
 Die Berichterstellungsumgebung kann mehrere Berichtsserver und verschiedene Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aufweisen. Sie können mehrere Konfigurationen erstellen und dann je nach Bereitstellungsszenario eine andere verwenden. Projektkonfigurationen schließen Eigenschaften zum Erstellen von Berichten ein, z. B. den Ordner, in dem die erstellten Berichte vorübergehend gespeichert werden, und die Behandlung von Erstellungsproblemen. Die Konfigurationen verfügen außerdem über Eigenschaften, mit denen Sie den Speicherort und die Version des Berichtsservers und die Ordner auf dem Berichtsserver angeben.  
  
 Standardmäßig stellt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] drei Projektkonfigurationen bereit: **DebugLocal**, **Debug**und **Release**. Die Standardkonfiguration ist DebugLocal. Mit der DebugLocal-Konfiguration können Sie Berichte in der Regel in einem lokalen Vorschaufenster anzeigen, mit der Debug-Konfiguration können Sie Berichte auf einem Testserver veröffentlichen, und mit der Release-Konfiguration veröffentlichen Sie Berichte auf einem Produktionsserver. Die aktive Konfiguration wird auf der Standardsymbolleiste in der Dropdownliste Projektmappenkonfigurationen angezeigt. Wenn Sie eine andere Konfiguration verwenden möchten, wählen Sie sie aus der Liste aus.  
  
 ![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png) 
  
 Weitere Informationen finden Sie unter:
 + [Project Property Pages Dialog Box (Projekt (Eigenschaftenseiten, Dialogfeld))](../../reporting-services/tools/project-property-pages-dialog-box.md)
 + [Bereitstellung und Versionsunterstützung in SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)
 + [Festlegen von Bereitstellungseigenschaften für Reporting Services-Projekte in SSDT](../../reporting-services/tools/set-deployment-properties-reporting-services.md)
  
## <a name="to-publish-all-reports-in-a-project"></a>So veröffentlichen Sie alle Berichte in einem Projekt  
  
Klicken Sie im Menü **Erstellen** auf **Berichtsprojektname>\< bereitstellen**. Sie können auch im Projektmappen-Explorer mit der rechten Maustaste auf das Berichtsobjekt klicken. Klicken Sie dann auf **Bereitstellen**. Den Status des Veröffentlichungsvorgangs sehen Sie im Ausgabefenster.  
  
Wenn Sie ein Berichtsserverprojekt bereitstellen, werden die freigegebenen Datenquellen im Berichtsprojekt ebenfalls bereitgestellt. Alle Berichte werden mithilfe derselben Projektkonfiguration bereitgestellt: auf demselben Berichtsserver, im selben Ordner auf dem Server usw. Zur Veröffentlichung von Berichten auf verschiedenen Servern veröffentlichen Sie sie entweder nacheinander oder schließen nur die gewünschten Berichte in das Berichtsserverprojekt ein. Eine Projektmappe kann mehrere Berichtsserverprojekte enthalten. Die Verwendung mehrerer Projekte erleichtert zudem die Verwaltung der Berichtsbereitstellung, weil Sie zur Bereitstellung unterschiedlicher Projekte jeweils eine andere Konfiguration verwenden können. 
  
## <a name="to-publish-a-single-report"></a>So veröffentlichen Sie einen einzelnen Bericht  
  
Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Bericht, und klicken Sie auf **Bereitstellen**. Den Status des Veröffentlichungsvorgangs sehen Sie im Ausgabefenster.  
  
 Wenn Sie einen Bericht veröffentlichen, müssen Sie auch die freigegebenen Datenquellen bereitstellen, die vom Bericht verwendet werden.   
 Wenn Sie nicht alle Berichte in einem Projekt veröffentlichen möchten, können Sie einen einzelnen Bericht veröffentlichen. Wählen Sie dazu eine Konfiguration aus, durch die der Bericht bereitgestellt wird (z.B. die Release-Konfiguration), klicken Sie mit der rechten Maustaste auf den Bericht, und klicken Sie dann auf **Bereitstellen**.  
  
 Wenn ein Bericht eine freigegebene Datenquelle verwendet, müssen Sie ebenfalls die freigegebene Datenquelle bereitstellen, oder der bereitgestellte Bericht wird nicht ausgeführt. Klicken Sie mit der rechten Maustaste auf die freigegebene Datenquelle, und klicken Sie dann auf **Bereitstellen**.  
  
 Die Zielserver-URL des Berichtsservers muss angegeben werden. Zudem können Sie die Standardordner ändern, in denen Berichte und freigegebene Datenquellen bereitgestellt werden.  

  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaftsseiten für Projekt (Dialogfeld)](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Upgrade Reports (Aktualisieren von Berichten)](../../reporting-services/install-windows/upgrade-reports.md)  
  
  
