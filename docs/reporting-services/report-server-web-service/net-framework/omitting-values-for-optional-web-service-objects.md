---
title: Weglassen von Werten für optionale Webdienstobjekte | Microsoft-Dokumentation
ms.date: 03/04/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a963fcad77a6c916b4726cf62b0dd09b49d6152f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128866"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>Weglassen von Werten für optionale Webdienstobjekte
  Eigenschaften von mehreren der komplexen Typen eines Berichtsserver-Webdiensts besitzen eine zugehörige Eigenschaft, die als die Specified-Eigenschaft bekannt ist. Der Name der Eigenschaft setzt sich aus dem ursprünglichen Eigenschaftennamen und dem daran angefügten Wort "Specified" zusammen. Wenn diese Eigenschaft vorhanden ist, bedeutet dies, dass ein Wert für die ursprüngliche Eigenschaft unter Umständen manchmal weggelassen wird. Das ist das direkte Ergebnis der Übersetzung aus WSDL (Web Service Description Language) in eine [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Proxyklasse. Beispiel: Die Webdiensteigenschaft <xref:ReportService2010.DataSourceDefinition.Enabled%2A> des komplexen Typs <xref:ReportService2010.DataSourceDefinition> besitzt eine zugehörige Eigenschaft mit dem Namen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Wenn Sie eine Anwendung erstellen und keinen Wert für die <xref:ReportService2010.DataSourceDefinition.Enabled%2A>-Eigenschaft festlegen möchten, müssen Sie keinen Wert für <xref:ReportService2010.DataSourceDefinition.Enabled%2A> angeben. Es wird der Standardwert **TRUE** verwendet. Sie müssen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> jedoch trotzdem auf **FALSE** festlegen. Wenn Sie einen Wert für die <xref:ReportService2010.DataSourceDefinition.Enabled%2A>-Eigenschaft angeben, müssen Sie <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> auf **TRUE** festlegen. Das ist bei schreibbaren Eigenschaften der Fall. Für schreibgeschützte Eigenschaften müssen Sie keine Aktion durchführen.  
  
> [!IMPORTANT]  
>  Wird keine Eigenschaft mit den oben genannten Vorgehensweisen festgelegt, kann dies zu unvorgesehenem Verhalten des Webdiensts führen.  
  
 Die Datentypen, die normalerweise eine Behandlung der zusätzlichen Specified-Eigenschaft erforderlich machen, lauten **Boolean**, **DateTime**, und **Enumeration**.  
  
 Ein Beispiel hierzu finden Sie unter <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>-Methode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Technische Referenz (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
