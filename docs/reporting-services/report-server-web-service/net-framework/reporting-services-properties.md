---
title: Eigenschaften von Reporting Services | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e2b7495edef06da522112932c75d5f35684313f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742618"
---
# <a name="reporting-services-properties"></a>Eigenschaften von Reporting Services
  Der Berichtsserver definiert eine Reihe von Systemeigenschaften, die global für den Berichtsserver gelten, und eine Reihe von Elementeigenschaften, die zu einem in der Berichtsserver-Datenbank gespeicherten Einzelelement gehören. Vom Berichtsserver definierte Eigenschaften können nicht gelöscht werden, und in einigen Fällen sind sie schreibgeschützt. In einer Anwendung können die System- und Elementeigenschaften erweitert werden, indem zusätzliche benutzerdefinierte Eigenschaften zu den System- und den Elementeigenschaften hinzugefügt werden.  
  
 Die folgenden Webdienstmethoden rufen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Eigenschaften ab und legen diese fest.  
  
|Methode|Aktion|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Gibt die Werte von einer oder mehreren Eigenschaften eines Elements in der Berichtsserver-Datenbank zurück.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Gibt eine oder mehrere Systemeigenschaften zurück.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Legt eine oder mehrere Eigenschaften eines Elements in der Berichtsserver-Datenbank fest.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Legt eine oder mehrere Systemeigenschaften fest.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Eigenschaften der Berichtsserverelemente](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Beschreibt die elementspezifischen Eigenschaften in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Berichtsserver-Systemeigenschaften](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Beschreibt die systemspezifischen Eigenschaften in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
