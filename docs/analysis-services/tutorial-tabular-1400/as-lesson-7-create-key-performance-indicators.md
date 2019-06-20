---
title: 'Analysis Services-Tutorial – Lektion 7: Erstellen von Key Performance Indicators | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f3b3de71cb60a27613482255556bfbff6bcc8cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "64877621"
---
# <a name="create-key-performance-indicators"></a>Erstellen von Leistungskennzahlen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie Key Performance Indicators (KPIs). KPIs werden verwendet, um die Leistung eines Werts definiert durch eine *Base* Measure für ein *Ziel* ebenfalls durch ein Measure oder einen absoluten Wert definiert. In Clientanwendungen zur Berichtserstellung erhalten Geschäftsleute mit KPIs einen schnellen und einfachen Einblick in den insgesamten Geschäftserfolg bzw. können Trends leichter identifizieren. Weitere Informationen finden Sie unter [KPIs](../tabular-models/kpis-ssas-tabular.md)
  
Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 6: Erstellen von Measures](../tutorial-tabular-1400/as-lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Erstellen von Leistungskennzahlen  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterSalesPerformance-KPI  
  
1.  Klicken Sie im Modell-Designer auf die **"factinternetsales"** Tabelle.  
  
2.  Klicken Sie im Measureraster auf eine leere Zelle.  
  
3.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IF([InternetPreviousQuarterSalesProportionToQTD]<>0,([InternetCurrentQuarterSales]-[InternetPreviousQuarterSalesProportionToQTD])/[InternetPreviousQuarterSalesProportionToQTD],BLANK()) 
    ```

    Dieses Measure fungiert als Basiskennzahl für den KPI.  
  
4.  Klicken Sie im measureraster mit der Maustaste **InternetCurrentQuarterSalesPerformance** > **Create KPI**.   
  
5.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1.1**.  
  
7.  Geben Sie im linken (unteren) Schiebereglerfeld den Wert **1**und anschließend im rechten (oberen) Schiebereglerfeld **1,07**ein.  
  
8.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus.
  
    ![als lesson7 kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > Beachten Sie die erweiterbare **Beschreibungen** Bezeichnung unterhalb der verfügbaren symbolarten. Verwenden Sie eine Beschreibung der verschiedenen KPI-Elemente, um die in Clientanwendungen leichter.  
  
9. Klicken Sie auf **OK** , um den KPI abzuschließen.  
  
    Beachten Sie im measureraster das Symbol neben dem **InternetCurrentQuarterSalesPerformance** Measure. Dieses Symbol gibt an, dass das Measure als Basiswert für einen KPI dient.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterMarginPerformance-KPI  
  
1.  Das measureraster für die **"factinternetsales"** Tabelle, klicken Sie auf eine leere Zelle.  
  
2.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Mit der rechten Maustaste **"internetcurrentquartermarginperformance"**  > **KPI erstellen**.  
  
4.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1,25**.   
  
5.  Schieben Sie im Feld linken (unteren) Schieberegler, bis im Feld **0,8**, und klicken Sie dann den rechten (oberen) schiebereglerfeld bis im Feld **1,03**.  
  
6.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus. Klicken Sie anschließend auf **OK**.  
  
## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 8: Erstellen von Perspektiven](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).
  
  
