---
title: Teradata-Verbindungstyp (SSRS) | Microsoft-Dokumentation
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4c50b757f6866307b52106055fd5affbf46789c0
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66500133"
---
# <a name="teradata-connection-type-ssrs"></a>Teradata-Verbindungstyp (SSRS)
  Wenn Sie Daten aus einer relationalen Teradata-Datenbank in den Bericht einschließen möchten, benötigen Sie ein Dataset, das auf einer Berichtsdatenquelle vom Typ "Teradata" basiert. Dieser integrierte Datenquellentyp basiert auf dem verwalteten .NET-Anbieter für die Teradata-Datenverarbeitungserweiterung.  
  
 Verwenden Sie die Informationen in diesem Thema, um eine Datenquelle zu erstellen. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Hinzufügen und Prüfen einer Datenverbindung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Verbindungszeichenfolge  
 Erfragen Sie bei Ihrem Datenbankadministrator die Verbindungsinformationen und die Anmeldeinformationen, die verwendet werden sollen, um eine Verbindung mit der Datenquelle herzustellen. Im folgenden Beispiel für eine Verbindungszeichenfolge wird eine Teradata-Datenbank auf dem Server mit einer IP-Adresse angegeben:  
  
```  
data source=<IP Address>  
```  
  
 Weitere Beispiele für Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="Credentials"></a> Anmeldeinformationen  
 Anmeldeinformationen sind erforderlich, um Abfragen auszuführen und den Bericht lokal oder vom Berichtsserver aus in der Vorschau anzuzeigen.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
 Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen &#40;Berichts-Generator und SSRS&#41; ](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) oder [angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen-Verbindungen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Remarks"></a> Hinweise  
 Bevor Sie eine Verbindung mit einer Teradata-Datenquelle herstellen können, muss der Systemadministrator die Version des .NET-Datenanbieters für Teradata installieren, die das Abrufen von Daten aus der Teradata-Datenbank unterstützt. Dieser Datenanbieter muss auf dem gleichen Computer wie der Berichts-Generator und auf dem Berichtsserver installiert werden.  
  
 Nicht alle Berichtsübermittlungsmodi werden von diesem Datenanbieter unterstützt. Die Übermittlung von Berichten über datengesteuerte Abonnements wird für diese Datenverarbeitungserweiterung nicht unterstützt. Weitere Informationen finden Sie unter [Verwenden einer externen Datenquelle für Abonnentendaten &#40;datengesteuertes Abonnement&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dokumentation der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
  
##  <a name="Models"></a> Berichtsmodelle  
 Wenn Sie ein Dataset aus einem Berichtsmodell erstellen möchten, das auf einer Teradata-Datenquelle basiert, muss das Modell im Modell-Designer in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] entworfen und auf einem Berichtsserver veröffentlicht werden.  
  
  
##  <a name="Related"></a> Verwandte Abschnitte  
 Diese Abschnitte der Dokumentation enthalten umfassende grundlegende Informationen zu Berichtsdaten sowie Informationen zum Definieren, Anpassen und Verwenden der mit Daten zusammenhängenden Teile eines Berichts.  
  
 [Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Bietet eine Übersicht über den Zugriff auf Daten für den Bericht.  
  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 Enthält Informationen zu Datenverbindungen und Datenquellen.  
  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Enthält Informationen zu eingebetteten und freigegebenen Datasets.  
  
 [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Enthält Informationen zu der von der Datasetabfrage generierten Feldauflistung.  
  
 [Von Reporting Services unterstützte Datenquellen (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dokumentation der [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Enthält ausführliche Informationen zur Plattform- und Versionsunterstützung für die einzelnen Datenerweiterungen.  
  
 [Verwenden von SQL Server 2008 Reporting Services mit dem .NET Framework-Datenanbieter für Teradata](https://go.microsoft.com/fwlink/?LinkID=130848)  
 Enthält ausführliche Informationen zum Arbeiten mit dieser Datenerweiterung.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
