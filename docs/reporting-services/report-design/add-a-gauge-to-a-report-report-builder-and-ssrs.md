---
title: Hinzufügen eines Messgeräts zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie im Berichts-Generator Daten in einem visuellen Format zusammenfassen, indem Sie einen Datenbereich für ein Messgerät erstellen und Berichtsdatasetfelder in einen Bereich des Messgeräts ziehen.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ebf3648c2292e5d3e83ff753f70b5f430f0ba3bc
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681549"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a>Hinzufügen eines Messgeräts zu einem Bericht (Berichts-Generator und SSRS)
  Wenn Sie [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] in einem paginierten Bericht Daten in einem visuellen Format zusammenfassen möchten, verwenden Sie einen Messgerätdatenbereich. Nachdem Sie einen Messgerätdatenbereich zur Entwurfsoberfläche hinzugefügt haben, können Sie Berichtsdatasetfelder in einen Datenbereich auf dem Messgerät ziehen.  
  
## <a name="to-add-a-gauge-to-your-report"></a>So fügen Sie ein Messgerät zu einem Bericht hinzu  
  
1.  Erstellen Sie einen Bericht, oder öffnen Sie einen vorhandenen Bericht.  
  
2.  Doppelklicken Sie auf der Registerkarte Einfügen auf Messgerät. Das Dialogfeld **Messgerättyp auswählen** wird geöffnet.  
  
3.  Wählen Sie den gewünschten Messgerättyp aus. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Im Gegensatz zu Diagrammen gibt es nur zwei Messgerättypen, nämlich linear und radial. Die im Dialogfeld **Messgerättyp auswählen** verfügbaren Messgeräte sind Vorlagen für diese beiden Arten von Messgeräten. Deshalb können Sie den Messgerättyp nicht ändern, nachdem Sie das Messgerät dem Bericht hinzugefügt haben. Wenn Sie den Typ ändern möchten, müssen Sie das Messgerät löschen und erneut hinzufügen.  
  
     Wenn der Bericht keine Datenquelle und kein Dataset enthält, wird das Dialogfeld **Datenquelleneigenschaften** geöffnet. Es führt Sie durch die einzelnen Schritte beim Erstellen von Datenquelle und Dataset. Weitere Informationen finden Sie unter [Hinzufügen und Prüfen einer Datenverbindung (Berichts-Generator und SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
     Wenn der Bericht eine Datenquelle, jedoch kein Dataset enthält, wird das Dialogfeld **Dataseteigenschaften** geöffnet. Es führt Sie durch die einzelnen Schritte beim Erstellen des Datasets. Weitere Informationen finden Sie unter [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
4.  Klicken Sie zum Anzeigen des Datenbereichs auf das Messgerät. Standardmäßig verfügt ein Messgerät über einen Zeiger, der einem Wert entspricht. Sie können weitere Zeiger hinzufügen.  
  
5.  Fügen Sie der Datenfeldablagezone ein Feld aus dem Dataset hinzu. Sie können nur ein Feld hinzufügen. Wenn Sie mehrere Felder anzeigen möchten, müssen Sie zusätzliche Zeiger hinzufügen, einen für jedes Feld.  
  
     Klicken Sie mit der rechten Maustaste auf die Skalierung des Messgeräts, und wählen Sie **Skalierungseigenschaften**aus. Geben Sie einen Wert für das **Minimum** und das **Maximum** der Skala ein. Weitere Informationen finden Sie unter [Festlegen eines Mindestwerts oder eines Höchstwerts auf einem Messgerät (Berichts-Generator und SSRS)](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
