---
title: Erstellen einer Market Basket-Struktur und eines Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 207d82f740b7b5ff174e220e647d67d5bac7f9ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190832"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer Warenkorbstruktur und eines Warenkorbmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Sie haben nun eine Datenquellensicht erstellt und erstellen mithilfe des Data Mining-Assistenten eine neue Miningstruktur. In dieser Aufgabe legen Sie eine Miningstruktur und ein Miningmodell an, die auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus basieren.  
  
> [!NOTE]  
>  Wenn Sie eine Fehlermeldung erhalten, nach der "vAssocSeqLineItems" nicht in einer geschachtelten Tabelle verwendet werden kann, kehren Sie zur vorherigen Aufgabe in dieser Lektion zurück, und erstellen Sie den n:1-Join, indem Sie ihn aus der Tabelle "vAssocSeqLineItems" (die n-Seite) in die Tabelle "vAssocSeqOrders" (die 1-Seite) ziehen. Sie können die Beziehung zwischen den Tabellen auch bearbeiten, indem Sie mit der rechten Maustaste auf die Joinlinie klicken.  
  
### <a name="to-create-an-association-mining-structure"></a>So legen Sie die Miningstruktur Association an  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur** zu Data Mining-Assistenten zu öffnen.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** überprüfen Sie, ob Seite **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Erstellen von Data Mining-Struktur** Seite **welche Datamining-Technik möchten Sie verwenden?** Option **Microsoft Association Rules** aus der Liste aus, und klicken Sie dann auf **Weiter**. Die **Datenquellensicht auswählen** Seite wird angezeigt.  
  
5.  Wählen Sie **Bestellungen**unter **verfügbare Datenquellensichten**, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Tabellentypen angeben** Seite in der Zeile für die Tabelle "vassocseqlineitems", wählen Sie die **geschachtelte** aus, und wählen Sie in der Zeile für die geschachtelte Tabelle vAssocSeqOrders, die **Fall** Kontrollkästchen. Klicken Sie auf **Weiter**.  
  
7.  Auf der **Trainingsdaten** Seite, deaktivieren Sie alle Kontrollkästchen, die überprüft werden können. Legen Sie den Schlüssel für die Falltabelle vAssocSeqOrders durch Aktivieren der **Schlüssel** das Kontrollkästchen neben OrderNumber fest.  
  
     Da der Zweck der Market Basket-Analyse ist, um zu bestimmen, welche Produkte in einer einzelnen Transaktion enthalten sind, müssen Sie nicht verwenden die **CustomerKey** Feld.  
  
8.  Legen Sie den Schlüssel für die geschachtelte Tabelle vAssocSeqLineItems durch Aktivieren der **Schlüssel** Kontrollkästchen neben dem Modell. Die **Eingabe** Kontrollkästchen wird auch automatisch ausgewählt, wenn Sie dies tun. Wählen Sie die **vorhersagbar** Kontrollkästchen `Model` ebenfalls.  
  
     In einem Market Basket-Modells, Sie ist nicht wichtig die Reihenfolge der Produkte im Einkaufswagen und aus diesem Grund sollten Sie nicht einschließen **LineNumber** als Schlüssel für die geschachtelte Tabelle. Verwenden Sie **LineNumber** als Schlüssel nur in einem Modell, in dem die Sequenz wichtig ist. In Lektion 4 erstellen Sie ein Modell, das den [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus verwendet.  
  
9. Wählen Sie das Kontrollkästchen links neben IncomeGroup und Region, aber nehmen Sie keine anderen Angaben. Durch Aktivieren der äußerst linken Spalte fügen Sie der Struktur die Spalten zur späteren Bezugnahme hinzu. Die Spalten werden jedoch nicht im Modell verwendet. Ihre Auswahl sollte wie folgt aussehen:  
  
     ![wie Sie im Dialogfeld aussehen soll](../../2014/tutorials/media/tutorial-configassocmodel.gif "wie das Dialogfeld aussehen soll")  
  
10. Klicken Sie auf **Weiter**.  
  
11. Auf der **Inhalt und Datentyp der Spalten angeben**überprüfen Sie die Auswahl, in dem sein, wie in der folgenden Tabelle dargestellt, und klicken Sie dann auf **Weiter**.  
  
    |Spalte|Inhaltstyp|Datentyp|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discrete|Textmodus|  
    |Order Number|Key|Textmodus|  
    |Region|Discrete|Textmodus|  
    |vAssocSeqLineItems|||  
    |Model|Key|Textmodus|  
  
12. Auf der **erstellen Tests legen** Seite, der Standardwert für die Option **Prozentsatz der Testdaten** liegt bei 30 Prozent. Ändern Sie diese Option, um **0**. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt andere Diagramme zum Messen der Modellgenauigkeit bereit. Einige Genauigkeitsdiagrammtypen, z. B. das Prognosegütediagramm und der Kreuzvalidierungsbericht, dienen jedoch der Klassifizierung und Schätzung. Eine Unterstützung für assoziative Vorhersagen ist nicht vorgesehen.  
  
13. Auf der **Abschließen des Assistenten** auf der Seite **Miningstrukturname**, Typ `Association`.  
  
14. In **Miningmodellname**, Typ `Association`.  
  
15. Wählen Sie die Option **Drillthrough zulassen**, und klicken Sie dann auf **Fertig stellen**.  
  
     Data Mining-Designer wird geöffnet und zeigt die `Association` Miningstruktur, die Sie gerade erstellt haben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ändern und Verarbeiten der Market Basket-Modells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Inhaltstypen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
