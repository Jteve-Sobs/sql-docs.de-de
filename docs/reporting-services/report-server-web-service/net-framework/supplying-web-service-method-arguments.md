---
title: Bereitstellen von Argumenten für Webdienstmethoden | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ad5251471fe9be594bf0ffb09c13f5f9afc35990
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128957"
---
# <a name="supplying-web-service-method-arguments"></a>Bereitstellen von Argumenten für Webdienstmethoden
  Eine Report Server-Webdienstmethode sendet eine Anforderung an den Dienst unter einer bestimmten URL, wobei SOAP über HTTP verwendet wird. Der Dienst empfängt die Anforderung, verarbeitet sie und gibt dann eine Antwort zurück. Diese Anforderungen und Antworten haben die Form von XML-Dokumenten.  
  
## <a name="optional-parameters"></a>Optionale Parameter  
 In manchen Fällen kann eine Webdienstmethode optionale Eingabeparameter haben. Selbst wenn ein Eingabeparameter für eine Webdienstmethode optional ist, müssen Sie ihn trotzdem aufnehmen und den Parameterwert auf **NULL** festlegen (**Nothing** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Wenn Sie einen Parameterwert auf **NULL** festlegen, wird der Elementwert für diesen Parameter in der SOAP-Anforderung auf **NULL** festgelegt.  
  
 Im folgenden Beispiel wird die <xref:ReportService2010.ReportingService2010.CreateFolder%2A>-Methode zum Erstellen eines neuen Ordners mit dem Namen Product Sales im Ordner Sales verwendet. Wenn der Wert **NULL** für die Ordnereigenschaften verwendet wird, werden für den Ordner keine benutzerspezifischen Eigenschaften bereitgestellt:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Komplexe Datentypen  
 Die Kernklasse des Report Server-Webdiensts ist <xref:ReportService2010.ReportingService2010>. Sie wird verwendet, um die SOAP-Vorgänge oder Webmethoden der Proxyklasse aufzurufen. Damit diese Klasse und ihre Methoden unterstützt werden, enthält [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] benutzerdefinierte, komplexe Datentypen, die für die Eingabe- und Ausgabeparameter der Webdienstmethoden spezifisch sind. Diese komplexen Datentypen sind Teil der erzeugten Proxyklasse, die Sie beim Entwickeln in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Umgebung verwenden können.  
  
 Wenn Sie eine Proxyklasse erzeugen, werden die in der WSDL-Datei definierten komplexen Datentypen durch die Klassen des Proxys dargestellt, die Eigenschaften enthalten, welche den verschiedenen SOAP-Elementen der komplexen Datentypen entsprechen. Sequenzen dieser Datentypen werden zu Objektarrays, die Sie im Code durchlaufen können. Dadurch ist es nicht notwendig, direkt mit den in SOAP-Nachrichten gesendeten XML-Strukturen zu arbeiten. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] behandelt diese Übersetzung für Sie.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
