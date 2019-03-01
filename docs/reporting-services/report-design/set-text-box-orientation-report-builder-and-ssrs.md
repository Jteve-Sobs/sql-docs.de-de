---
title: Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS) |- Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 34331a7ac53f7a36694c397964b1be20ae2c1f9c
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298618"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS)
In einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Bericht können Sie ein Textfeld auf verschiedene Weise drehen:   
* Horizontal   
* Vertikal (um 90 Grad gedreht, die Leserichtung verläuft von oben nach unten)  
* Um 270 Grad gedreht (die Leserichtung verläuft von unten nach oben)   
  
Da die Drehung für das Textfeld und nicht den Text selbst festgelegt wird, wird sie auf den gesamten Text im Textfeld angewendet. Sie können für Textteile keine unterschiedlichen Ausrichtungen angeben. Passen Sie die Spaltenbreite und die Zeilenhöhe manuell an, damit der gedrehte Text vollständig angezeigt wird.  
  
 Die WritingMode-Eigenschaft, mit der die Textausrichtung angegeben wird, befindet sich nicht im Dialogfeld **Textfeldeigenschaften** . Sie ist im Eigenschaftenbereich zu finden. Legen Sie die Eigenschaft dort fest.   
  
## <a name="to-rotate-text"></a>So drehen Sie Text  
  
1.  Erstellen Sie einen Bericht oder öffnen Sie einen vorhandenen, und [fügen Sie der Entwurfsoberfläche ein Textfeld hinzu](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) .  
  
3.  Wählen Sie das Textfeld aus, das Sie drehen möchten.  
  
2.  Wenn der Eigenschaftenbereich nicht geöffnet ist, aktivieren Sie auf der Registerkarte **Ansicht** das Kontrollkästchen **Eigenschaften** .  
  
4.  Suchen Sie die WritingMode-Eigenschaft im Eigenschaftenbereich, und wählen Sie die Textausrichtung aus, die auf das Textfeld angewendet werden soll.  
  
    > [!NOTE]  
    >  Wenn die Eigenschaften im Eigenschaftenbereich in Kategorien angeordnet sind, befindet sich WritingMode in der Kategorie **Lokalisierung** .  
  
5.  Wählen Sie im Listenfeld **Horizontal**, **Vertical**oder **Rotate270**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Textfelder &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Tutorial: Formatieren von Text &#40;Berichts-Generator&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
