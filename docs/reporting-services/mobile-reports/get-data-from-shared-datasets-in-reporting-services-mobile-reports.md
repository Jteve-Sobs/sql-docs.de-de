---
title: Abrufen von Daten aus freigegebenen Datasets in mobilen Reporting Services-Berichten | Microsoft-Dokumentation
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 0b846451-c8d0-412c-802d-a42bb1ff8c63
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cac1a32b49fde5b41c0a8ef21706d873ce037cd3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63061154"
---
# <a name="get-data-from-shared-datasets-in-reporting-services-mobile-reports"></a>Abrufen von Daten aus freigegebenen Datasets in mobilen Reporting Services-Berichten
Neben dem [Laden von Daten aus Excel-Dateien](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md) kann der Publisher für mobile Berichte von Microsoft SQL Server auch auf Daten aus nahezu allen Quellen zugreifen. Für den Zugriff auf Daten wird eine freigegebene Datenquelle benötigt, die auf einem Reporting Services-Webportal konfiguriert ist. Erfahren Sie mehr über das [Erstellen freigegebener Datenquellen](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md) und das [Erstellen freigegebener Datasets](../../reporting-services/report-data/manage-shared-datasets.md).  
  
Nachdem freigegebene Datenquellen und freigegebene Datasets auf dem Reporting Services-Server konfiguriert wurden, können Sie diese in mobilen Berichten verwenden, die Sie im [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] erstellt haben.   
  
Nachdem Sie eine Verbindung mit einem [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] -Server aus der [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]hergestellt haben, ist das Verbinden eines mobilen Berichts mit einem freigegebener Dataset einfach.   
  
1. Wählen Sie auf der Registerkarte **Daten** **Daten hinzufügen**aus.  
  
2. Wählen Sie **Berichtsserver**aus.   
  
3.  Falls Sie sich zum ersten Mal mit dem Server verbinden, geben Sie den Servernamen und Ihren Namen sowie Ihr Kennwort ein. Fügen Sie den Namen des Servers im Adressfeld in folgendem Format ein:  
  
    \<Servername>/reports/  
  
    In diesem Beispiel:  
       
    ![SSMRP_ConnectToServer](../../reporting-services/mobile-reports/media/ssmrp-connecttoserver.png)  
      
  
4. Bei der Auswahl des [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] -Servers, werden verfügbare Datasets in Ordnern angezeigt. Wählen Sie ein Dataset zum Importieren der Daten in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].  
  
   ![SS_MRP_ServerData](../../reporting-services/mobile-reports/media/ss-mrp-serverdata.png)  
  
Nachdem Sie das Dataset importiert haben, können Sie den mobilen Bericht entwerfen, und zwar genau so wie mit simulierten Daten oder lokale Daten aus einer Excel-Datei.  
  
Standardmäßig besitzt das freigegebene Dataset immer die aktuellsten Daten, da SQL Server jedes Mal, wenn ein Benutzer einen mobilen Bericht basierend auf diesem Dataset anzeigt, die zugrunde liegende Abfrage durchführt und die aktuellen Daten zurückgibt. Sollten viele Personen Ihren Bericht abrufen, ist dies natürlich nicht ideal. Deshalb können Sie mithilfe der Zwischenspeicherung dafür sorgen, dass die Abfrage periodisch ausgeführt und das Dataset zwischengespeichert wird. In diesem Blogbeitrag wird erläutert [wie Zwischenspeicherung und Datenaktualisierung im Webportal funktioniert](https://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/).  
  
## <a name="add-edit-or-remove-a-report-server"></a>Hinzufügen, Bearbeiten oder Entfernen eines Berichtsservers  
  
Wenn Sie bereits mit einem Berichtsserver verbunden sind, wird Ihnen bei der Auswahl **Daten hinzufügen** auf der Registerkarte „Daten“ keine Option zum Hinzufügen eines anderen Berichtsservers angezeigt. Befolgen Sie stattdessen diese Schritte.  
  
1. Wählen Sie in der oberen linken Ecke die Option **Verbindungen**.  
  
   ![SSMRP_AddConnectionIcon](../../reporting-services/mobile-reports/media/ssmrp-addconnectionicon.png)  
     
   Der Bereich „Serververbindung“ wird auf der rechten Seite geöffnet.  
     
   ![SSMRP_ServerConnectnPane](../../reporting-services/mobile-reports/media/ssmrp-serverconnectnpane.png)  
     
2. Fügen Sie eine neue Serververbindung hinzu, oder bearbeiten bzw. entfernen Sie vorhandene Verbindungen.  
  
### <a name="see-also"></a>Weitere Informationen  
- [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  [Webportal (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md)  
-  Anzeigen von [mobilen SQL Server-Berichten und KPIs in der iPad-App](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI für iOS)  
-  Anzeigen von [mobilen SQL Server-Berichten und KPIs in der iPhone-App](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI für iOS)  
  
  
  
  

