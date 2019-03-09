---
title: 'Analysis Services-Tutorial – Lektion 4: Erstellen von Beziehungen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 16fcf8e5f85464dbba7666f0f4ebebba829405af
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685611"
---
# <a name="create-relationships"></a>Erstellen von Beziehungen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion überprüfen Sie die Beziehungen, die automatisch, beim Importieren von Daten erstellt wurden und Hinzufügen neuer Beziehungen zwischen verschiedenen Tabellen. Eine Beziehung ist eine Verbindung zwischen zwei Tabellen, die festlegt, wie die Daten in diesen Tabellen miteinander in Beziehung gesetzt werden sollen. Die DimProduct-Tabelle und die DimProductSubcategory-Tabelle haben beispielsweise eine Beziehung, die darauf beruht, dass jedes Produkt zu einer Unterkategorie gehört. Weitere Informationen finden Sie unter [Beziehungen](../tabular-models/relationships-ssas-tabular.md).
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 3: Als Datumstabelle markieren](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md). 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Überprüfen vorhandener Beziehungen und Hinzufügen neuer Beziehungen  

Wenn Sie Daten mit Get Data importiert haben, haben Sie sieben Tabellen aus der Datenbank "AdventureWorksDW". Wenn Sie Daten aus einer relationalen Quelle importieren, werden im Allgemeinen vorhandene Beziehungen automatisch zusammen mit den Daten importiert. In der Reihenfolge Get Data im Datenmodell automatisch Beziehungen zu erstellen muss Beziehungen zwischen Tabellen in der Datenquelle vorhanden sein.

Bevor Sie mit der Erstellung Ihres Modells fortfahren, sollten Sie überprüfen, dass die Beziehungen zwischen Tabellen ordnungsgemäß erstellt wurden. In diesem Tutorial fügen Sie außerdem drei neue Beziehungen hinzu.  

  
#### <a name="to-review-existing-relationships"></a>So überprüfen Sie vorhandene Beziehungen  
  
1.  Klicken Sie auf die **Modell** Menü > **Modellansicht** > **Diagrammansicht**.  

    Im Modell-Designer wird jetzt angezeigt, in der Diagrammsicht importiert ein grafisches Format, in dem alle Tabellen dazwischen liegenden Zeilen. Die Zeilen zwischen den Tabellen geben die Beziehungen an, die automatisch beim Importieren der Daten erstellt wurden.
    
    ![Diagramm als lesson4](../tutorial-tabular-1400/media/as-lesson4-diagram.png)
  
    > [!NOTE]
    > Wenn Sie keine Beziehungen zwischen Tabellen nicht sehen, bedeutet es wahrscheinlich, dass keine Beziehungen zwischen diesen Tabellen in der Datenquelle vorhanden sind.

    Unter Verwendung der Minikarte in der unteren rechten Ecke des Modell-Designers können Sie beliebig viele Tabellen wie möglich einschließen. Sie können auch mittels Klick und Ziehen Tabellen verschieben, näher zu einander positionieren oder in einer bestimmten Reihenfolge anordnen. Verschieben von wirkt sich nicht auf die Beziehungen zwischen den Tabellen. Um alle Spalten in einer bestimmten Tabelle anzuzeigen, klicken Sie auf, und ziehen Sie auf einer Tabellenkante zu erweitern oder zu verkleinern.  
  
2.  Klicken Sie auf die durchgezogene Linie zwischen den **DimCustomer** Tabelle und die **DimGeography** Tabelle. Die durchgezogene Linie zwischen diesen beiden Tabellen zeigt, dass diese Beziehung aktiv ist, ist es bei der Berechnung von DAX-Formeln standardmäßig verwendet wird.  
  
    Beachten Sie, dass die **GeographyKey** -Spalte in der **DimCustomer** Tabelle und die **GeographyKey** -Spalte in der **DimGeography** Tabelle jetzt sowohl Jede in ein Feld angezeigt werden. Diese Spalten werden in der Beziehung verwendet. Die Eigenschaften der Beziehung ist jetzt auch im angezeigt der **Eigenschaften** Fenster.  
  
    > [!TIP]  
    > Sie können auch das Dialogfeld "Beziehungen verwalten" verwenden, um die Beziehungen zwischen allen Tabellen in einem Tabellenformat anzuzeigen. Im tabellarischen Modell-Explorer mit der Maustaste **Beziehungen** > **Beziehungen verwalten**.
  
3.  Überprüfen Sie die folgenden Beziehungen erstellt wurden, als jede der Tabellen aus der AdventureWorksDW-Datenbank importiert wurde:  
  
    |Active|Tabelle|Verknüpfte Suchtabelle|  
    |----------|---------|------------------------|  
    |Ja|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |Ja|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |Ja|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |Ja|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |Ja|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    Wenn einige dieser Beziehungen fehlen, überprüfen Sie, ob Ihr Modell in den folgenden Tabellen enthält: DimCustomer, DimDate, DimGeography, DimProduct, DimProductCategory, DimProductSubcategory und FactInternetSales. Wenn Tabellen aus derselben datenquellenverbindung zu unterschiedlichen Zeitpunkten, Beziehungen zwischen importiert werden diese Tabellen werden nicht erstellt werden, und müssen manuell erstellt werden. Wenn keine Beziehungen angezeigt werden, bedeutet dies, dass in der Datenquelle keine Beziehungen vorhanden sind. Sie können diese manuell im Datenmodell erstellen.

### <a name="take-a-closer-look"></a>Ausführlichere Betrachtung

Beachten Sie in der Diagrammsicht einen Pfeil, ein Sternchen und eine Zahl auf die Zeilen, die die Beziehung zwischen Tabellen veranschaulichen.

![Zeile als lesson4](../tutorial-tabular-1400/media/as-lesson4-line.png)

Der Pfeil zeigt die filterrichtung. Das Sternchen zeigt an, diese Tabelle ist die *viele* -Seite in der Kardinalität der Beziehung, und der wird diese Tabelle ist die *eine* Seite der Beziehung. Wenn Sie eine Beziehung bearbeiten müssen. z. B. ändern Sie die Beziehung die filterrichtung oder Kardinalität zu, doppelklicken Sie auf die Beziehungslinie, um das Dialogfeld "Beziehung bearbeiten" zu öffnen.

![as-lesson4-edit](../tutorial-tabular-1400/media/as-lesson4-edit.png)

Diese Features sind nur für den erweiterten datenmodellierung und befinden sich außerhalb des Bereichs in diesem Tutorial. Weitere Informationen finden Sie unter [bidirektionale kreuzfilter für tabellarische Modelle in Analysis Services](../tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md).

In einigen Fällen müssen Sie möglicherweise zusätzliche Beziehungen zwischen Tabellen im Modell erstellen, um eine bestimmte Geschäftslogik zu unterstützen. Für dieses Tutorial müssen Sie drei zusätzliche Beziehungen zwischen der FactInternetSales-Tabelle und der DimDate-Tabelle erstellen.  
  
#### <a name="to-add-new-relationships-between-tables"></a>So fügen Sie neue Beziehungen zwischen Tabellen hinzu  
  
1.  Im Modell-Designer in der **"factinternetsales"** Tabellen, warten Sie, und klicken Sie auf der **OrderDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der  **DimDate** Tabelle, und veröffentlichen.  

    Eine durchgezogene Linie wird angezeigt, mit der Sie erstellt haben, eine aktive Beziehung zwischen der **OrderDate** -Spalte in der **Internetverkäufe** Tabelle und die **Datum** -Spalte in der  **Datum** Tabelle. 
  
      ![als-lesson4-neu](../tutorial-tabular-1400/media/as-lesson4-new.png) 
  
    > [!NOTE]  
    > Beim Erstellen von Beziehungen wird die Kardinalität und die filterrichtung zwischen der primären Tabelle und der zugehörigen Nachschlagetabelle automatisch ausgewählt.  
  
2.  In der **"factinternetsales"** Tabelle, klicken Sie auf, und warten Sie, den **DueDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der **DimDate** Tabelle, und klicken Sie dann Version.  
  
    Eine gepunktete Linie wird angezeigt, mit der Sie erstellt haben, eine inaktive Beziehung zwischen der **DueDate** -Spalte in der **"factinternetsales"** Tabelle und die **Datum** -Spalte in der  **DimDate** Tabelle. Mehrere Beziehungen zwischen Tabellen sind möglich. Doch nur eine Beziehung kann jeweils aktiv sein. Inaktive Beziehungen können aktiv sein, um spezielle Aggregationen in benutzerdefinierten DAX-Ausdrücken durchführen vorgenommen werden.  
  
3.  Erstellen Sie abschließend eine weitere Beziehung. In der **"factinternetsales"** Tabelle, klicken Sie auf, und warten Sie, den **ShipDate** Spalte ziehen Sie dann den Cursor zu der **Datum** -Spalte in der **DimDate** Tabelle, und klicken Sie dann Version.  
    
     ![als lesson4 newinactive](../tutorial-tabular-1400/media/as-lesson4-newinactive.png)
  
## <a name="whats-next"></a>Wie geht es weiter?

[Lesson 5: Erstellen von berechneten Spalten](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).
  
  
  
