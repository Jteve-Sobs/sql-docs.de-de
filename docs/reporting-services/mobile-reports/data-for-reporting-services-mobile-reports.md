---
title: Daten für mobile Reporting Services-Berichte | Microsoft-Dokumentation
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6131f6bce9cb6d1c87a4a75215a906b6d097c7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63129742"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Daten für mobile Berichte von Reporting Services
Das [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] -Datenmodell ist einfach. Daten werden in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] als eine Sammlung von Datasets importiert. Formale Beziehungen zwischen Datasets sind nicht erforderlich. Suchvorgänge aus einem Dataset in einem anderen funktionieren, solange die Schlüsselwerte übereinstimmen. Datum/Uhrzeit-Aggregationen werden von der Laufzeitumgebung der mobilen Berichte behandelt und stimmen zwischen den verschiedenen Datasets überein, selbst wenn sich die Granularität der Datum/Uhrzeit-Daten zwischen den Datasets unterscheidet.   
  
Sie können Daten aus zwei Arten von Quellen importieren:   
  
* **Lokale Excel-Dateien**: Wählen Sie ein Excel-Dokument aus und wählen Sie aus, welches Arbeitsblatt bzw. welche Arbeitsblätter Sie importieren möchten. Nach dem Import werden die Daten in der mobilen Berichtsdefinition gespeichert. Verwenden Sie den Befehl **Daten aktualisieren** rechts oben auf der [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **Data** tab. Erfahren Sie mehr über das [Vorbereiten von Excel-Daten für mobile SSRS-Berichte](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md).  
  
* **Von Publisher für mobile Berichte von SQL Server freigegebene Datasets**: Durchsuchen Sie die Liste der veröffentlichten Datasets auf dem Server, und wählen Sie diejenigen aus, die Sie dem mobilen Bericht hinzufügen möchten. Auf Serverdaten basierende mobile Berichte erhalten immer die Verbindung mit den ursprünglichen Datasets und spiegeln den aktuellsten Zustand der Daten auf dem Server wider. Sehen Sie sich eine [Liste unterstützter Datenquellen](../report-data/data-sources-supported-by-reporting-services-ssrs.md)an.   
  
  Erfahren Sie mehr über das [Abrufen von Daten aus freigegebenen Datasets im Publisher für mobile Berichte](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md).  
  
Nachdem Sie Daten in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]importiert haben, ist die übrige Erstellung und Entwurfserfahrung der mobilen Berichte gleich, unabhängig davon, woher die Daten stammen.   
  
## <a name="connect-mobile-report-elements-to-data"></a>Verbinden von Elementen mobiler Berichte mit Daten ##  
  
Jedes Elements von Publisher für mobile Berichte von Microsoft SQL Server enthält ein oder mehrere Dateneinstellungen. Das Element „Radiales Messgerät“ enthält beispielsweise zwei Dateneinstellungen: Hauptwert und Vergleichswert. Jede dieser Einstellungen verweist auf genau ein Feld (eine Spalte) in einem spezifischen Dataset.   
  
Die Laufzeitumgebung mobiler Berichte stellt aggregierte Werte für das Messgerät basierend auf der Auswahl des Benutzers bereit. Beachten Sie, dass der Vergleichswert der gleichen „Radiales Messgerät“-Instanz an ein Feld aus einem anderen Dataset gebunden sein kann.   
  
### <a name="see-also"></a>Siehe auch  
-  [Vorbereiten von Daten für mobile Reporting Services-Berichte](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Abrufen von Daten aus freigegebenen Datasets](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Retain date formatting for Analysis Services in mobile reports (Datumsformatierung für Analysis Services in mobilen Berichten beibehalten)](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

