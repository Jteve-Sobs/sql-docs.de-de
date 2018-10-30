---
title: Datenwarnungs-Manager für Warnungsadministratoren | Microsoft-Dokumentation
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 32fd968f-1c0c-4ba8-851c-8a3b5e1fbbf2
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 84d99c48cea1da044e5372713a487f250bb1f40d
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021124"
---
# <a name="data-alert-manager-for-alerting-administrators"></a>Datenwarnungs-Manager für Warnungsadministratoren

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services stellt den Datenwarnungs-Manager zum Verwalten von Datenwarnungen für SharePoint-Warnungsadministratoren bereit. Warnungsadministratoren können Informationen zu allen auf der Website gespeicherten Warnungen anzeigen und Warnungen löschen. Das folgende Bild zeigt SharePoint-Warnungsadministratoren die verfügbaren Funktionen im Datenwarnungs-Manager.

![Warnungs-Manager für SharePoint-Websiteadministratoren](../reporting-services/media/rs-alertmanagersite.gif "Alert Manager for SharePoint site administrators")

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

 Wenn die Website für Datenwarnungen aktiviert ist, werden zwei SharePoint-Seiten (MyDataAlerts.aspx und SiteDataAlerts.aspx) erstellt und der SharePoint-Website hinzugefügt. SiteDataAlerts.aspx entspricht dem Datenwarnungs-Manager für Warnungsadministratoren. Warnungsadministratoren können den Datenwarnungs-Manager über die SharePoint-Seite "Siteeinstellungen" öffnen. Warnungsadministratoren müssen die SharePoint-Berechtigung "Benachrichtigungen verwalten" besitzen, um den Datenwarnungs-Manager zu öffnen.  
  
 Sie können den Datenwarnungs-Manager auch direkt über eine URL öffnen. Die Syntax der URL wird nachfolgend angezeigt:  
  
 `http: //<site name>/_layouts/ReportServer/ SiteDataAlerts.aspx`  
  
> [!NOTE]  
>  Als Warnungsadministrator können Sie Information Workern die Berechtigung erteilen, auf die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Datenwarnungsfunktionen zuzugreifen. Weitere Informationen zu den erforderlichen Berechtigungen finden Sie unter [Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md).  
  
##  <a name="ViewingAlerts"></a> Anzeigen von Datenwarnungsinformationen  
 Wenn Reporting Services installiert ist und in SharePoint konfiguriert wird, enthält die SharePoint-Seite "Siteeinstellungen" die **Reporting Services** -Optionen. Warnungsadministratoren klicken in Reporting Services auf die Option **Datenwarnungen verwalten** , um den Datenwarnungs-Manager zu öffnen. Das folgende Bild zeigt, wie sich der Datenwarnungs-Manager auf der Seite "Siteeinstellungen" öffnen lässt.  
  
 ![Reporting Services-Abschnitt der Seite „Websiteeinstellungen“](../reporting-services/media/rs-sitesettings.gif "Reporting Services section of Site Settings page")  
  
 Der Datenwarnungs-Manager umfasst eine Tabelle mit dem Warnungsnamen, Berichtsnamen, Namen des Warnungseigentümers, der Nummer der Warnmeldung, der letzten Ausführung der Warnung, der letzten Änderung der Warnungsdefinition und dem Status der Warnmeldung. Wenn die Datenwarnung nicht generiert oder gesendet werden kann, enthält die Statusspalte Informationen zum Fehler und hilft Ihnen bei der Behebung des Problems mit der Warnung. Weitere Informationen finden Sie unter [Manage All Data Alerts on a SharePoint Site in Data Alert Manager](../reporting-services/manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).  
  
 In der folgenden Tabelle werden Beispieldaten einer Tabelle im Datenwarnungs-Manager angezeigt. Tritt ein Fehler auf, werden die Fehlermeldung und der Bezeichner des Eintrags im Protokoll (eine GUID) in das Feld **Status** der Tabelle aufgenommen.  
  
|Name der Warnung|Berichtsname|Erstellt von|Gesendete Warnungen|Zuletzt ausgeführt|Zuletzt geändert|Status|  
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|  
|SalesQTR|SalesByTerritoryAndQTR|Lauren Johnson|4|6/12/2011|6/1/2011|Die letzte Warnung war erfolgreich, und die Warnung wurde gesendet.|  
|UnitsSold|ProductsSalesByQTR|Michael Blythe|2|7/1/2011|6/28/2011|Die letzte Warnung wurde erfolgreich ausgeführt, aber die Daten blieben unverändert, und es wurde keine Warnung gesendet.|  
|InventoryCount|StockStatusByQTR|Lauren Johnson|7|7/10/2011|7/2/2011|\<Fehlermeldung>Die Protokolldatei enthält Details zum Fehler. Weitere Informationen erhalten Sie unter dem Protokolleintrag mit dem Bezeichner: \<GUID>.|  
|TopPromotion|PromotionTracking|Cristian Petculescu|0||5/23/2011|Die Warnung wurde erstellt.|  
  
 Weitere Informationen finden Sie unter [Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager](../reporting-services/manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).  
  
 Sie können alle von Websitebenutzern erstellten Warnungen anzeigen. Sie wählen erst einen Benutzer und wählen dann, ob alle Warnungen oder nur Warnungen für einen bestimmten Bericht angezeigt werden sollen.  
  
  
##  <a name="DeleteAlerts"></a> Löschen von Datenwarnungen  
 Warnungsdefinitionen lassen sich über den Datenwarnungs-Manager löschen. Jede Datenwarnungsdefinition hat einen Eigentümer (den SharePoint-Benutzer, der sie erstellt hat). Eigentümer können nur die von ihnen erstellten Warnungsdefinitionen löschen. Weitere Informationen finden Sie unter [Verwalten meiner Datenwarnungen im Datenwarnungs-Manager](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md).  
  
 Ein SharePoint-Warnungsadministrator kann Warnungsdefinitionen auflisten und dann löschen, die von einem beliebigen Benutzer der Website erstellt wurden. Weitere Informationen finden Sie unter [Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager](../reporting-services/manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)  
  
 Nach dem Löschen der Warnungsdefinition werden keine weiteren Warnungen gesendet. Wenn Sie jedoch die Warnungsdatenbank abfragen, stellen Sie möglicherweise fest, dass die Warnungsdefinition immer noch vorhanden ist. Der Warndienst führt den Cleanup nach einem Zeitplan durch. Die Warnungsdefinition wird beim nächsten Cleanup dauerhaft gelöscht. Das Standardintervall für den Cleanup beträgt 20 Minuten. Dieses und andere Cleanupintervalle sind konfigurierbar. Weitere Informationen finden Sie unter [Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md).  
  
  
##  <a name="HowTo"></a> Verwandte Aufgaben  
 In diesem Abschnitt ist eine Prozedur aufgeführt, die das Verwalten der Warnungen zeigt.  
  
-   [Manage All Data Alerts on a SharePoint Site in Data Alert Manager](../reporting-services/manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)  

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
