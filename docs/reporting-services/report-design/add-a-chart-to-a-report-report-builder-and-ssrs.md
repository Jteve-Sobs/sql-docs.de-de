---
title: Hinzufügen eines Diagramms zu einem Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 550459c3b261a42aa1b5be0ad37cd1681f566a02
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50030779"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a>Hinzufügen eines Diagramms zu einem Bericht (Berichts-Generator und SSRS)
  Wenn Sie Daten in einem visuellen Format in einem paginierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht zusammenfassen möchten, verwenden Sie den Diagrammdatenbereich. Es ist wichtig, einen geeigneten Diagrammtyp für die von Ihnen dargestellten Daten auszuwählen. Durch den Diagrammtyp wird bestimmt, wie gut die Daten interpretiert werden können, wenn sie in Diagrammform umgesetzt werden. Weitere Informationen finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 Am einfachsten können Sie einen Diagrammdatenbereich einem Bericht hinzufügen, indem Sie den Assistenten Neues Diagramm ausführen. Mit dem Assistenten können Sie Säulen-, Linien-, Balken- und Flächendiagramme erstellen. Für diese und andere Diagrammtypen können Sie auch manuell ein Diagramm hinzufügen.  
  
 Nachdem Sie einen Diagrammdatenbereich der Entwurfsoberfläche hinzugefügt haben, können Sie Berichtsdataset-Felder für numerische und nicht numerische Daten in den Diagrammdatenbereich des Diagramms ziehen. Klicken Sie auf das Diagramm, um den Diagrammdatenbereich mit den drei Bereichen Reihengruppen, Kategoriegruppen und Werte anzuzeigen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a>So fügen Sie einem Bericht ein Diagramm mit dem Diagramm-Assistenten hinzu  
  
1.  > [!NOTE]  
    >  Der Diagramm-Assistent ist nur in Berichts-Generator verfügbar.  
  
     Klicken Sie auf der Registerkarte **Einfügen** auf **Diagramm**und dann auf **Diagramm-Assistent**.  
  
2.  Führen Sie die Schritte im Assistenten **Neues Diagramm** aus.  
  
3.  Klicken Sie auf der Registerkarte **Home** auf **Ausführen** , um den gerenderten Bericht anzuzeigen.  
  
4.  Klicken Sie auf der Registerkarte **Ausführen** auf **Entwurf** , um den Bericht weiter zu bearbeiten.  
  
## <a name="to-add-a-chart-to-a-report"></a>So fügen Sie einem Bericht ein Diagramm hinzu  
  
1.  Erstellen Sie einen Bericht, und definieren Sie ein Dataset. Weitere Informationen finden Sie unter [Berichtsdatasets (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md).  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** auf **Diagramm**und dann auf **Diagramm einfügen**.  
  
3.  Klicken Sie auf der Entwurfsoberfläche auf die Stelle, an der die obere linke Ecke des Diagramms positioniert werden soll, und ziehen Sie den Mauszeiger an die Stelle, an der die untere rechte Ecke des Diagramms positioniert werden soll.  
  
     Das Dialogfeld **Diagrammtyp auswählen** wird angezeigt.  
  
4.  Wählen Sie den Diagrammtyp aus, den Sie hinzufügen möchten. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Klicken Sie zum Anzeigen des Bereichs **Diagrammdaten** auf das Diagramm.  
  
6.  Fügen Sie dem Bereich **Werte** mindestens ein Feld hinzu. Diese Informationen werden auf der Wertachse dargestellt.  
  
7.  Fügen Sie dem Bereich **Kategoriegruppen** ein Gruppierungsfeld hinzu. Wenn Sie dem Bereich **Kategoriegruppen** dieses Feld hinzufügen, wird automatisch ein Gruppierungsfeld erstellt. Jede Gruppe stellt einen Datenpunkt in der Reihe dar.  
  
8.  Klicken Sie mit der rechten Maustaste auf das Datenfeld, und klicken Sie anschließend auf **Reiheneigenschaften**, um die Daten nach Kategorie zusammenzufassen. Wählen Sie im Feld **Kategorie** das Kategoriefeld in der Dropdownliste aus. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. Klicken Sie auf der Registerkarte **Home** auf **Ausführen** , um den gerenderten Bericht anzuzeigen.  
  
10. Klicken Sie auf der Registerkarte **Ausführen** auf **Entwurf** , um den Bericht weiter zu bearbeiten.  
  
 In Diagrammen mit Achsen, z. B. Balken- und Säulendiagrammen, zeigt die Kategorieachse möglicherweise nicht alle Kategoriebezeichnungen an. Weitere Informationen zum Ändern der Achsenbezeichnungen finden Sie unter [Angeben eines Achsenintervalls (Berichts-Generator und SSRS)](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Leere und NULL-Datenpunkte in Diagrammen (Berichts-Generator und SSRS)](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)](https://go.microsoft.com/fwlink/?LinkId=198052)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Designer)](https://go.microsoft.com/fwlink/?LinkId=198042)   
 [Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator)](https://go.microsoft.com/fwlink/?LinkId=198051)   
 [Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Designer)](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
