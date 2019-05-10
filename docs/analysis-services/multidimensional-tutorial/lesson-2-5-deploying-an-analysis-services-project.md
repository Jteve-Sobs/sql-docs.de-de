---
title: Bereitstellen eines Analysis Services-Projekt | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3d6fe74ecf361392da9000286427679194e15de9
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404042"
---
# <a name="lesson-2-5---deploying-an-analysis-services-project"></a>Lektion 2 – 5: Bereitstellen eines Analysis Services-Projekts
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Zum Anzeigen von Cube- und Dimensionsdaten für die Objekte im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Projekt müssen Sie das Projekt auf einer bestimmten Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitstellen und dann den Cube und seine Dimensionen verarbeiten. Durch das *Bereitstellen* eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekts werden die definierten Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt. Durch das*Verarbeiten* der Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden Daten von den zugrunde liegenden Datenquellen in die Cubeobjekte kopiert. Weitere Informationen finden Sie unter [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md) und [Konfigurieren von Analysis Services-Projekteigenschaften &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
An diesem Punkt des Entwicklungsprozesses stellen Sie den Cube im Allgemeinen für eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf einem Entwicklungsserver bereit. Sobald Sie die Entwicklung Ihres Business Intelligence-Projekts abgeschlossen haben, verwenden Sie im Allgemeinen den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , um Ihr Projekt statt auf dem Entwicklungsserver auf einem Produktionsserver bereitzustellen. Weitere Informationen finden Sie unter [Mehrdimensionale Modelllösungsbereitstellung](../multidimensional-models/multidimensional-model-solution-deployment.md) und [Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](../multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md).  
  
In der folgenden Aufgabe überprüfen Sie die Bereitstellungseigenschaften des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Projekts und stellen dann das Projekt für Ihre lokale Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereit.  
  
### <a name="to-deploy-the-analysis-services-project"></a>So stellen Sie das Analysis Services-Projekt bereit  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **Analysis Services Tutorial** und anschließend auf **Eigenschaften**.  
  
    Das Dialogfeld **Analysis Services Tutorial-Eigenschaftenseiten** wird angezeigt, in dem die Eigenschaften der aktiven Bereitstellungskonfiguration angezeigt werden. Sie können mehrere Konfigurationen mit jeweils unterschiedlichen Eigenschaften definieren. Ein Entwickler möchte beispielsweise das gleiche Projekt so konfigurieren, dass es für verschiedene Entwicklungscomputer und mit verschiedenen Bereitstellungseigenschaften bereitgestellt wird, beispielsweise verschiedenen Datenbanknamen oder Verarbeitungseigenschaften. Beachten Sie den Wert für die **Ausgabepfad** -Eigenschaft. Durch diese Eigenschaft wird der Speicherort angegeben, an dem die XMLA-Bereitstellungsskripts für das Projekt gespeichert werden, wenn das Projekt erstellt wird. Dabei handelt es sich um Skripts, die zum Bereitstellen der Objekte im Projekt für eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwendet werden.  
  
2.  Klicken Sie im Knoten **Konfigurationseigenschaften** im linken Bereich auf **Bereitstellung**.  
  
    Überprüfen Sie die Bereitstellungseigenschaften für das Projekt. Standardmäßig wird von der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projektvorlage ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt so konfiguriert, dass alle Projekte inkrementell für die Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf dem lokalen Computer bereitgestellt werden, um eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank mit dem gleichen Namen wie das Projekt zu erstellen und die Objekte nach der Bereitstellung zu verarbeiten, indem die Standardverarbeitungsoption verwendet wird. Weitere Informationen finden Sie unter [Konfigurieren von Analysis Services-Projekteigenschaften &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)erstellt.  
  
    > [!NOTE]  
    > Wenn Sie das Projekt für eine benannte Instanz von bereitstellen möchten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf dem lokalen Computer oder für eine Instanz auf einem Remoteserver, Ändern der **Server** Eigenschaft mit der entsprechenden Instanz umbenennen, z. B. \<  *ServerName**>\\<** InstanceName ** >*.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das **Analysis Services Tutorial** -Projekt und anschließend auf **Bereitstellen**. Sie müssen möglicherweise einen Moment warten.  
  
    > [!NOTE]  
    > Wenn während der Bereitstellung Fehler auftreten, überprüfen Sie die Datenbankberechtigungen mithilfe von SQL Server Management Studio. Das Konto, das Sie für die Datenquellenverbindung angegeben haben, muss über einen Anmeldenamen in der SQL Server-Instanz verfügen. Doppelklicken Sie auf den Anmeldenamen, um Eigenschaften für die Benutzerzuordnung anzuzeigen. Dieses Konto muss in der **AdventureWorksDW2012** -Datenbank über db_datareader-Berechtigungen verfügen.  
  
    [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] stellt nun das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Projekt erstellt und mit einem Bereitstellungsskript für die angegebene Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereit. Der Status der Bereitstellung wird in zwei Fenstern angezeigt: die **Ausgabe** Fenster und die **Bereitstellungsstatus – Analysis Services Tutorial** Fenster.  
  
    Öffnen Sie gegebenenfalls das Ausgabefenster, indem Sie im Menü **Ansicht** auf **Ausgabe** klicken. Im Fenster **Ausgabe** wird der allgemeine Bereitstellungsstatus angezeigt. Die **Bereitstellungsstatus – Analysis Services Tutorial** Fenster werden Details zu den einzelnen Bereitstellungsschritten angezeigt. Weitere Informationen finden Sie unter [Erstellen von Analysis Services-Projekten &#40;SSDT&#41;](../multidimensional-models/build-analysis-services-projects-ssdt.md) und [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
5.  Überprüfen Sie den Inhalt von der **Ausgabe** Fenster und die **Bereitstellungsstatus – Analysis Services Tutorial** , stellen Sie sicher, dass der Cube erstellt wurde, bereitgestellt und ohne Fehler verarbeitet.  
  
6.  Um das Fenster **Bereitstellungsstatus – Analysis Services Tutorial** auszublenden, klicken Sie auf das Pushpin-ähnliche Symbol **Automatisch im Hintergrund** in der Symbolleiste des Fensters.  
  
7.  Blenden Sie das Fenster **Ausgabe** aus, indem Sie auf der Symbolleiste des Fensters auf das Symbol **Automatisch im Hintergrund** klicken.  
  
Sie haben erfolgreich den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial-Cube für Ihre lokale Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitgestellt und dann den bereitgestellten Cube verarbeitet.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Durchsuchen des Cubes](lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>Siehe auch  
[Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
[Konfigurieren von Analysis Services-Projekteigenschaften &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  
  
