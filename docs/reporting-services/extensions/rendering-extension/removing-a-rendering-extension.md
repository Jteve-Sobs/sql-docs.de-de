---
title: Entfernen von Renderingerweiterungen | Microsoft-Dokumentation
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0ee3563074e2379061006b72f55dab99f80094cd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63193451"
---
# <a name="removing-a-rendering-extension"></a>Entfernen von Renderingerweiterungen
  Um eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Renderingerweiterung zu entfernen, entfernen Sie einfach das **Extension**-Element für Ihre Renderingerweiterung im Ordner **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instanzname>\Reporting Services\ReportServer** aus der Datei „rsreportserver.config“. Wenn Sie Einträge für einen Berichts-Designer und einen Berichtsserver vorgenommen haben, entfernen Sie das **Extension**-Element auch aus der [Konfigurationsdatei RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md). Nachdem Sie die Konfigurationsdaten entfernt haben, steht die Renderingerweiterung nicht mehr für die Komponente zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurationsdateien](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Übersicht über Renderingerweiterungen](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Implementieren der IRenderingExtension-Schnittstelle](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Überlegungen zur Sicherheit von Erweiterungen](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Bereitstellen von Renderingerweiterungen](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
