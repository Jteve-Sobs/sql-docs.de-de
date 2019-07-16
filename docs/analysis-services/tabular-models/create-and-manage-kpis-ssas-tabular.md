---
title: Erstellen und Verwalten von KPIs in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ae17e727367b702967ec879ed8469973ab3b812
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207731"
---
# <a name="create-and-manage-kpis"></a>Erstellen und Verwalten von KPIs 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Dieser Artikel beschreibt, wie Sie erstellen, bearbeiten oder löschen Sie einen KPI (Key Performance Indicator) in einem tabellarischen Modell. Um einen KPI zu erstellen, wählen Sie ein Measure, der Basiswert des KPIS ergibt. Anschließend wählen Sie im Dialogfeld Key Performance Indicator ein zweites Measure oder einen absoluten Wert aus, das bzw. der einen Zielwert ergibt. Sie können dann Statusschwellenwerte definieren, mit denen die Leistung zwischen dem Basis- und dem Zielmeasure gemessen wird.  
  
## <a name="tasks"></a>Richtlinienübersicht  
  
> [!IMPORTANT]  
>  Bevor Sie einen KPI erstellen, müssen Sie zuerst ein Basismeasure generieren, das einen Wert ergibt. Anschließend erweitern Sie das Basismeasure zu einem KPI. Zum Erstellen von Measures in einem anderen Thema beschrieben [erstellen und Verwalten von Measures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md). Für einen KPI ist zudem ein Zielwert erforderlich. Dieser Wert kann von einem anderen vordefinierten Measure stammen oder ein absoluter Wert sein. Nachdem Sie ein Basismeasure zu einem KPI erweitert haben, können Sie den Zielwert auswählen und die Statusschwellenwerte im Dialogfeld Key Performance Indicator definieren.  
  
###  <a name="bkmk_create_KPI"></a> So erstellen Sie einen KPI  
  
1.  Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) fungieren soll, und klicken Sie dann im Kontextmenü auf **KPI erstellen**.  
  
2.  Wählen Sie im Dialogfeld **Key Performance Indicator** unter **Zielwert definieren**eine der folgenden Optionen aus:  
  
     Klicken Sie auf **Measure**, und wählen Sie dann ein Zielmeasure aus dem Listenfeld aus.  
  
     Wählen Sie **Absoluter Wert**aus, und geben Sie einen numerischen Wert ein.  
  
3.  Klicken Sie in **Statusschwellenwerte definieren**auf den Schieberegler, um den niedrigen und hohen Schwellenwert festzulegen.  
  
4.  Klicken Sie in **Symbolart auswählen**auf einen Bildtyp.  
  
5.  Klicken Sie auf **Beschreibungen**, und geben Sie Beschreibungen für KPI, Wert, Status und Ziel ein.  
  
> [!TIP]  
>  Sie können die Funktion In Excel analysieren verwenden, um den KPI zu testen. Weitere Informationen finden Sie unter [in Excel analysieren](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
###  <a name="bkmk_edit_KPI"></a> So bearbeiten Sie einen KPI  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **KPI-Einstellungen bearbeiten**.  
  
###  <a name="bkmk_delete"></a> So löschen Sie einen KPI und das Basismeasure  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **Löschen**.  
  
###  <a name="bkmk_delete_KPI"></a> So löschen Sie einen KPI, behalten aber das Basismeasure bei  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **KPI löschen**.  
  
## <a name="alt-shortcuts"></a>ALT-Tastenkombinationen  
  
|Benutzeroberflächenabschnitt|Tastaturbefehl|  
|----------------|-----------------|  
|KPI-Basismeasure|ALT+B|  
|KPI-Status|ALT+S|  
|Measure|ALT+M|  
|Absoluter Wert|ALT+A|  
|Statusschwellenwerte definieren|ALT+C|  
|Symbolart auswählen|ALT+I|  
|Trend|ALT+T|  
|Beschreibungen|ALT+D|  
|Trend|ALT+T|  
  
## <a name="see-also"></a>Siehe auch  
 [KPIs](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [Measures](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Erstellen und Managemeasures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
