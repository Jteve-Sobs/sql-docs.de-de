---
title: Karten in mobilen Reporting Services-Berichten | Microsoft-Dokumentation
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 50658295-a71c-441e-8eba-e1ef066629c0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5b09c8aec100d877256f0d8d9b4b97530ecdf5c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62683702"
---
# <a name="maps-in-reporting-services-mobile-reports"></a>Karten in mobilen Reporting Services-Berichten
Karten sind eine hervorragende Möglichkeit, geografische Daten visuell darzustellen. [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] bietet drei verschiedene Typen von Kartenvisualisierungen sowie integrierte Karten für Kontinente und eine Reihe von einzelnen Ländern. Sie können auch [benutzerdefinierte Karten hochladen und verwenden](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).   
  
## <a name="types-of-maps"></a>Kartentypen  
  
Mobile SQL Server-Berichte bieten drei verschiedene Typen von Karten, die sich für unterschiedliche Situationen eignen.  
  
![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
**Wärmebilder mit Verlauf** Das Feld in der Eigenschaft „Werte“ wird als Schattierungen einer einzelnen Farbe angezeigt, die jede Region in einer Karte ausfüllt. Im Feld **Wertrichtung** können Sie festlegen, ob die höheren oder die niedrigeren Werte dunkler sind.  
  
**Blasendiagrammkarte** Die Eigenschaft „Werte“ bestimmt den Radius der Blasenvisualisierung, die über den zugeordneten Bereich angezeigt wird. Sie können festlegen, ob alle Blasen die gleiche oder unterschiedliche Farben aufweisen.   
  
**Wärmebild mit Bereichsabgrenzung** zeigt einen Wert in Relation zu einem Ziel. Die Eigenschaft **Ziele** bestimmt das Delta zwischen einem Vergleichsfeld und dem Wertefeld. Das resultierende Delta bestimmt die Farbe, die die jeweilige Region der Karte ausfüllt: von Grün über Gelb zu Rot. Im Feld **Wertrichtung** können Sie festlegen, ob die höheren oder die niedrigeren Werte grün sind.  
  
## <a name="select-the-map-type-and-region"></a>Auswählen des Kartentyps und der Region  
  
1. Wählen Sie auf der Registerkarte **Layout** einen Kartentyp aus, ziehen Sie ihn auf die Entwurfsoberfläche, und stellen Sie ihn auf die gewünschte Größe ein.  
  
2. Wählen Sie in der Ansicht **Layout** im Bereich **Eigenschaften visueller Elemente** unter **Karte** die gewünschte Kartenregion aus.  
  
   ![SSMRP_SelectMap](../../reporting-services/mobile-reports/media/ssmrp-selectmaps.png)  
  
3. Stellen Sie für Wärmebilder mit Verlauf oder mit Bereichsabgrenzung im Feld **Wertrichtung** unter **Eigenschaften visueller Elemente**ein, ob höhere oder niedrigere Werte besser sind.  
  
7. Legen Sie für Blasendiagrammkarten unter **Eigenschaften visueller Elemente** die Option **Verschiedene Farben verwenden** auf **Ein** oder **Aus** fest, damit die Blasen alle die gleiche oder unterschiedliche Farben aufweisen.  
  
## <a name="select-the-map-data"></a>Auswählen der Kartendaten  
Wenn Sie eine Karte erstmals einem Bericht hinzufügen, wird sie von [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] mit simulierten geografischen Daten aufgefüllt.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
Um echte Daten in Ihrer Karte anzuzeigen, müssen Sie Werte für mindestens zwei der Dateneigenschaften der Karte festlegen:   
* Die Eigenschaft **Schlüssel** verbindet die Daten mit bestimmten Kartenregionen: z. B. Staaten in den USA oder Länder in Afrika.  
* Die Eigenschaft **Werte** ist ein numerisches Feld in der gleichen Tabelle wie das ausgewählte Schlüsselfeld. Diese Werte werden in unterschiedlichen Karten unterschiedlich dargestellt. Die **Verlaufskarte** verwendet diese Werte, um den einzelnen Regionen anhand des Wertebereichs unterschiedliche Farbschattierungen zuzuweisen. Bei der **Blasendiagrammkarte** beruht die Größe einer Blasenvisualisierung über jede Region auf der Werteigenschaft.   
* Bei Wärmebildern mit Bereichsabgrenzung müssen Sie auch die Eigenschaft **Ziele** festlegen.  
  
### <a name="set-map-data-properties"></a>Festlegen der Eigenschaften von Kartendaten  
  
1. Wählen Sie in der linken oberen Ecke die Registerkarte **Daten** aus.  
  
2. Wählen Sie **Daten hinzufügen**und anschließend entweder **Lokale Excel-Datei** oder **SSRS-Server**aus.  
  
   > **Tipp**: Stellen Sie sicher, dass die [Daten in einem Format vorliegen, das in mobilen Berichten eingesetzt werden kann](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md).  
  
3. Wählen Sie die gewünschten Arbeitsblätter aus, und wählen Sie **Importieren**.  
   Ihre Daten werden im [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]angezeigt.  
  
4. Wählen Sie in dieser Ansicht **Daten** im Bereich **Dateneigenschaften** unter **Schlüssel** im linken Feld die Tabelle mit den Kartendaten und im rechten Feld das Schlüsselfeld aus, das den Regionen in Ihrer Karte entspricht.  
  
5. Unter **Werte**befindet sich dieselbe Tabelle bereits im linken Feld. Wählen Sie das numerische Feld, dessen Werte auf der Karte angezeigt werden sollen.   
  
6. Wenn es sich um ein Wärmebild mit Verlauf handelt, befindet sich dieselbe Tabelle unter dem Feld **Ziele** im linken Feld. Wählen Sie im Feld auf der rechten Seite das numerische Feld aus, dessen Werte als Ziel dienen sollen.   
  
   ![SSMRP_MapRangeHeatData](../../reporting-services/mobile-reports/media/ssmrp-maprangeheatdata.png)  
  
7. Wählen Sie in der oberen linken Ecke die Option **Vorschau** .  
  
   ![SSMRP_MapRangeHeatPreview](../../reporting-services/mobile-reports/media/ssmrp-maprangeheatpreview.png)  
     
8. Wählen Sie in der oberen linken Ecke das Symbol **Speichern** und dann entweder **Lokal speichern** zum Speichern auf Ihrem Computer oder **Auf Server speichern**.  
  
### <a name="see-also"></a>Siehe auch  
-  [Benutzerdefinierte Karten in mobilen Reporting Services-Berichten](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  
