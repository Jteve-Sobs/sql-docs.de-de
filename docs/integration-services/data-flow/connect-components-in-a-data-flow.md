---
title: Verbinden von Komponenten in einem Datenfluss | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d353876938b3e64317f461240b2333e71217449
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727123"
---
# <a name="connect-components-in-a-data-flow"></a>Verbinden von Komponenten in einem Datenfluss

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  In diesem Verfahren wird das Verbinden der Ausgabe von Komponenten in einem Datenfluss mit anderen Komponenten innerhalb desselben Datenflusses beschrieben.  
Den Datenfluss in einem Paket erstellen Sie auf der Entwurfsoberfläche der Registerkarte **Datenfluss** im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer. Falls ein Datenfluss zwei Datenflusskomponenten enthält, können Sie diese verbinden, indem Sie die Ausgabe einer Quelle oder Transformation mit der Eingabe einer Transformation oder eines Zieles verbinden. Der Konnektor zwischen den beiden Datenflusskomponenten wird als Pfad bezeichnet.  
  
 Im folgenden Diagramm wird ein einfacher Datenfluss mit einer Quellkomponente, zwei Transformationen, einer Zielkomponente und den Pfaden, die diese verbinden, angezeigt.  
  
 ![Data flow](../../integration-services/data-flow/media/mw-dts-08.gif "Data flow")  
  
 Wenn zwei Komponenten verbunden sind, können Sie die Metadaten der Daten, die über den Pfad verschoben werden, und die Eigenschaften des Pfades in **Datenflusspfad-Editor**anzeigen. Weitere Informationen finden Sie unter [Integration Services Paths](../../integration-services/data-flow/integration-services-paths.md).  
  
 Sie können Pfaden auch Daten-Viewer hinzufügen. Mit einem Daten-Viewer können Sie Daten anzeigen, die zwischen Datenflusskomponenten verschoben werden, wenn das Paket ausgeführt wird.  
  
### <a name="connect-components-in-a-data-flow"></a>Verbinden von Komponenten in einem Datenfluss  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , und doppelklicken Sie anschließend auf den Datenflusstask, der den Datenfluss enthält, in dem Sie Komponenten verbinden möchten.  
  
4.  Wählen Sie auf der Entwurfsoberfläche der Registerkarte **Datenfluss** die Transformation oder Quelle aus, die Sie verbinden möchten.  
  
5.  Ziehen Sie den grünen Ausgabepfeil einer Transformation oder Quelle auf eine Transformation oder ein Ziel. Manche Datenflusskomponenten weisen Fehlerausgaben auf, die Sie auf die gleiche Weise verbinden können.  
  
    > [!NOTE]  
    >  Für manche Datenflusskomponenten sind mehrere Ausgaben möglich, und Sie können jede Ausgabe mit einer anderen Transformation oder einem anderen Ziel verbinden.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen einer Komponente im Datenfluss](../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)   
 [Debuggen des Datenflusses](../../integration-services/troubleshooting/debugging-data-flow.md) [Datenfluss](../../integration-services/data-flow/data-flow.md)  
  
  
