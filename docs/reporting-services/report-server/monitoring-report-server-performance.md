---
title: Überwachen der Leistung des Berichtsservers | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- report servers [Reporting Services], performance
- counters [Reporting Services]
- monitoring performance [Reporting Services]
- SQL Server Reporting Services, performance
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: c1bc13d4-8297-4daf-bb19-4c1e5ba292a6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba639ea5bc65cb8d5e753883418ad3937919fa1d
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65577665"
---
# <a name="monitoring-report-server-performance"></a>Überwachen der Leistung des Berichtsservers
  Überwachen Sie die Leistung des Berichtsservers mithilfe der Tools zur Leistungsüberwachung, um die Serveraktivität auszuwerten, Trends zu beobachten, Engpässe im System zu diagnostizieren oder Daten zu sammeln, mit denen Sie bestimmen können, ob die aktuelle Konfiguration ausreichend ist. Zum Optimieren der Serverleistung können Sie angeben, wie oft die Anwendungsdomäne des Berichtsservers wiederverwendet werden soll. Weitere Informationen finden Sie unter [Konfigurieren von verfügbarem Speicher für Berichtsserveranwendungen](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md).  
  
## <a name="sources-of-performance-data"></a>Quellen von Leistungsdaten  
 Verwenden Sie eine Kombination aus Technologien und Tools, um sich umfassende Informationen zur Leistung des Systems zu beschaffen: [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server-Betriebssysteme stellen Leistungsinformationen mithilfe der folgenden Tools bereit:  
  
-   Task-Manager  
  
-   Ereignisanzeige  
  
-   Leistungskonsole  
  
 Der Task-Manager stellt Informationen zu Programmen und Prozessen bereit, die auf einem Computer ausgeführt werden. Mit dem Task-Manager können Sie wichtige Indikatoren für die Leistung des Berichtsservers überwachen. Darüber hinaus können Sie die Aktivität von ausgeführten Prozessen bewerten und Grafiken sowie Daten zur CPU-Nutzung und Speicherauslastung anzeigen. Weitere Informationen zum Verwenden des Task-Managers finden Sie in der Produktdokumentation zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Mit der Leistungskonsole und der Ereignisanzeige können Sie Protokolle und Warnungen zur Berichtsverarbeitung und zum Ressourcenverbrauch erstellen. Informationen zu Windows-Ereignissen, die von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]generiert werden, finden Sie unter [Windows-Anwendungsprotokoll](../../reporting-services/report-server/windows-application-log.md). Weitere Informationen zur Leistungskonsole finden Sie unter „Windows-Leistungsindikatoren“ weiter unten in diesem Thema.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramme stellen außerdem Informationen zur Berichtsserver-Datenbank und zu temporären Datenbanken bereit, die zur Zwischenspeicherung und Sitzungsverwaltung verwendet werden.  
  
## <a name="windows-performance-counters"></a>Windows-Leistungsindikatoren  
 Die Überwachung bestimmter Leistungsindikatoren ermöglicht folgende Aktionen:  
  
-   Schätzen der zur Unterstützung einer prognostizierten Arbeitsauslastung erforderlichen Systemanforderungen.  
  
-   Erstellen einer Leistungsbasislinie, um die Auswirkungen von Konfigurationsänderungen oder Anwendungsupgrades zu messen.  
  
-   Überwachen der Anwendungsleistung unter bestimmten Arbeitsauslastungen, unabhängig davon, ob real oder künstlich generiert.  
  
-   Überprüfen, ob Hardwareupgrades sich wie gewünscht auf die Leistung auswirken.  
  
-   Überprüfen, ob an der Systemkonfiguration vorgenommene Änderungen sich wie gewünscht auf die Leistung auswirken.  
  
## <a name="reporting-services-performance-objects"></a>Reporting Services-Leistungsobjekte  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] beinhaltet die folgenden Leistungsobjekte:  
  
-   **MSRS 2011 Web Service** und **MSRS 2011 SharePoint Mode Web Service** zum Überwachen der Berichtsserverleistung. Diese Leistungsobjekte enthalten eine Reihe von Leistungsindikatoren zum Nachverfolgen der Verarbeitung auf einem Berichtsserver, die in der Regel über interaktive Vorgänge zum Anzeigen von Berichten gestartet wird. Diese Leistungsindikatoren werden zurückgesetzt, sobald [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] den Berichtsserver-Webdienst beendet.  
  
-   **MSRS 2011 Windows Service** und **MSRS 2011 Windows Service SharePoint Mode** zum Überwachen geplanter Vorgänge und der Berichtsübermittlung. Diese Leistungsobjekte enthalten eine Reihe von Leistungsindikatoren zum Nachverfolgen der Berichtsverarbeitung, die über geplante Vorgänge gestartet wird. Zu geplanten Vorgängen zählen Abonnement und Übermittlung, Berichtsausführungs-Momentaufnahmen und Berichtsverlauf.  
  
-   **ReportServer:Service** und **ReportServerSharePoint:Service** , HTTP-bezogene Ereignisse und die Verwaltung des Arbeitsspeichers zu überwachen. Diese Leistungsindikatoren sind spezifisch für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], und sie verfolgen HTTP-bezogene Ereignisse für den Berichtsserver nach, wie z. B. Anforderungen, Verbindungen und Anmeldeversuche. Darüber hinaus schließt dieses Leistungsobjekt Leistungsindikatoren in Bezug auf die Speicherverwaltung ein.  
  
 Falls auf einem Computer mehrere Berichtsserverinstanzen vorhanden sind, können die Instanzen gemeinsam oder separat überwacht werden. Wählen Sie beim Hinzufügen eines Leistungsindikators die zu überwachenden Instanzen aus. Weitere Informationen zum Verwenden der Leistungskonsole (perfmon.msc) und zum Hinzufügen von Leistungsindikatoren finden Sie in der Produktdokumentation zu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="other-performance-counters"></a>Weitere Leistungsindikatoren  
 Benutzerdefinierte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Leistungsindikatoren stehen nur für den **MSRS 2008-Webdienst**, **MSRS 2008-Windows-Dienst**und **ReportServer:Service**zur Verfügung. Die folgenden Leistungsobjekte stellen zusätzliche Leistungsüberwachungsdaten für den Berichtsserver bereit.  
  
|Leistungsobjekt|Hinweise|  
|------------------------|-----------|  
|**.NET CLR Data** und **.NET CLR Memory**|Der Berichts-Manager verwendet [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Leistungsindikatoren. Weitere Informationen finden Sie auf der MSDN-Website unter "Improving .NET Application Performance and Scalability" (in Englisch).|  
|**Verarbeiten**|Fügen Sie die Leistungsindikatoren **Elapsed Time** und **ID Process** für eine ReportingServicesService-Instanz hinzu, um die Prozessbetriebszeit nach Prozess-ID nachzuverfolgen.|  
  
## <a name="sharepoint-events"></a>SharePoint-Ereignisse  
 Zusätzlich zu den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Leistungsobjekten möchten Sie möglicherweise auch SharePoint-Ereignisse konfigurieren, wenn Sie einen Berichtsserver im integrierten SharePoint-Modus ausführen und die Berichterstellungsumgebung für die Verwendung eines SharePoint-Produkts konfiguriert haben. Mit den Ereignissen für einen Berichtsserver im integrierten SharePoint-Modus in diesem Abschnitt können Sie Diagnoseereignisse prüfen, die möglicherweise hilfreiche Informationen zur Verfügung stellen, wenn Ihre Berichterstellungsumgebung mit SharePoint integriert ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Leistungsindikatoren für den MSRS 2011-Webdienst und den MSRS 2011-Windows-Dienst, Leistungsobjekte &#40;einheitlicher Modus&#41;](../../reporting-services/report-server/performance-counters-msrs-2011-web-service-performance-objects.md)  
 Beschreibt die Leistungsindikatoren, die vom Berichtsserver-Webdienst verwendet werden.  
  
 [Leistungsindikatoren für den MSRS 2011-Webdienst im SharePoint-Modus und den MSRS 2011-Windows-Dienst im SharePoint-Modus, Leistungsobjekte &#40;SharePoint-Modus&#41;](../../reporting-services/report-server/performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
 Beschreibt die Leistungsindikatoren, die vom Berichtsserver-Windows-Dienst verwendet werden.  
  
 [Leistungsindikatoren für die Leistungsobjekte 'ReportServer:Service' und 'ReportServerSharePoint:Service'](../../reporting-services/report-server/performance-counters-reportserver-service-performance-objects.md)  
 Beschreibt die HTTP-bezogenen und speicherbezogenen Leistungsindikatoren in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Ereignisse für einen Berichtsserver im integrierten SharePoint-Modus  
 Beschreibt, welche hilfreichen Diagnoseereignisse protokolliert werden können, wenn Sie eine Berichterstellungsumgebung mit einem SharePoint-Produkt ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von verfügbarem Speicher für Berichtsserveranwendungen](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md)   
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Reporting Services-Tools](../../reporting-services/tools/reporting-services-tools.md)  
  
  
