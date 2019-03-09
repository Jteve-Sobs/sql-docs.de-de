---
title: 'Analysis Services-Tutorial – Lektion 2: Abrufen von Daten | Microsoft-Dokumentation'
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
ms.openlocfilehash: 01bf31c3d4f89b77ebdceae2e69d4054a578b03f
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685317"
---
# <a name="get-data"></a>Abrufen von Daten

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion verwenden Sie **Datenabruf** zur Verbindung mit der Beispieldatenbank "AdventureWorksDW" Wählen Sie Daten, die Vorschau und Filter aus, und klicken Sie dann in den Modellarbeitsbereich zu importieren.  
  
Abrufen von Daten wird im Hintergrund Power Query, der eine riesige Auswahl von Tools zum Herstellen einer Verbindung mit und Neustrukturieren von Daten für die Modellierung und Analyse. Weitere Informationen finden Sie unter [Power Query-Dokumentation](https://docs.microsoft.com/power-query/). 

> [!NOTE]
> Aufgaben und Bilder in diesem Tutorial wird gezeigt, Herstellen einer Verbindung mit einer AdventureWorksDW2014-Datenbank auf einem lokalen Server. In einigen Fällen kann eine AdventureWorksDW-Datenbank zu Azure SQL Data Warehouse über verschiedene Objekte anzeigen; Allerdings sind sie im Grunde identisch.
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 1: Erstellen ein neuen tabellarischen modellprojekts](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Erstellen einer Verbindung  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>Um eine Verbindung mit der AdventureWorksDW-Datenbank zu erstellen.  
  
1.  In **tabellarischer Modell-Explorer**, mit der rechten Maustaste **Datenquellen** > **aus Datenquelle importieren**.  
  
    Dadurch wird **Datenabruf**, dort werden Sie durch Herstellen einer Verbindung mit einer Datenquelle. Wenn Sie nicht im tabellarischen Modell-Explorer sehen **Projektmappen-Explorer**, doppelklicken Sie auf **Model.bim** um das Modell im Designer zu öffnen. 
    
    ![as-lesson2-getdata](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  Abrufen der Daten, klicken Sie auf **Datenbank** > **SQL Server-Datenbank** > **Connect**.  
  
3.  In der **SQL Server-Datenbank** Dialogfeld im **Server**, geben Sie den Namen des Servers, auf dem Sie die Datenbank "AdventureWorksDW" installiert, und klicken Sie dann auf **Connect**.  

4.  Wenn Sie aufgefordert, Anmeldeinformationen einzugeben, müssen Sie die Anmeldeinformationen angeben, die Analysis Services für die Verbindung mit der Datenquelle beim Importieren und Verarbeiten von Daten verwendet. In **Identitätswechselmodus**Option **Identität des Kontos**, geben Sie dann die Anmeldeinformationen ein, und klicken Sie dann auf **Connect**. Es wird empfohlen, dass Sie ein Konto verwenden, in dem das Kennwort nicht abläuft.

    ![as-lesson2-account](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > Die Verwendung eines Windows-Benutzerkontos und -Kennworts stellt die sicherste Methode für das Herstellen einer Verbindung mit einer Datenquelle dar.
  
5.  Wählen Sie im Navigator die **"AdventureWorksDW"** Datenbank, und klicken Sie dann auf **OK**. Dadurch wird die Verbindung mit der Datenbank erstellt. 
  
6.  Wählen Sie im Navigator das Kontrollkästchen für die folgenden Tabellen: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**,  **DimProductSubcategory**, und **"factinternetsales"**.  

    ![as-lesson2-select-tables](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
Nachdem Sie auf "OK" klicken, wird die Abfrage-Editor geöffnet. Im nächsten Abschnitt wählen Sie nur die Daten, die Sie importieren möchten.

  
## <a name="filter-the-table-data"></a>Filtern der Tabellendaten  

Tabellen in der AdventureWorksDW-Beispieldatenbank haben Daten, die nicht in das Modell eingeschlossen werden sollen, erforderlich ist. Wenn möglich, möchten Sie unnötige Daten vom Modell verwendeten in-Memory-Speicher zu sparen herausfiltern. Sie filtern einige der Spalten aus den Tabellen, damit sie nicht importiert werden in die arbeitsbereichsdatenbank oder die Modelldatenbank nachdem er bereitgestellt wurde. 
  
#### <a name="to-filter-the-table-data-before-importing"></a>Zum Filtern der Tabellendaten vor dem Importieren  
  
1.  Wählen Sie im Abfrage-Editor die **DimCustomer** Tabelle. Eine Ansicht der DimCustomer-Tabelle in der Datenquelle (der AdventureWorksDW-Beispieldatenbank) wird angezeigt. 
  
2.  Mehrfachauswahl (Strg + Klick) **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**, klicken Sie dann mit der rechten Maustaste, und klicken Sie dann auf **Spalten entfernen**. 

    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    Da die Werte für diese Spalten nicht relevant für die Analyse von Internetverkäufen sind, müssen die Spalten nicht importiert werden. Entfernen nicht erforderlicher Spalten wird das Modell kleiner und effizienter.  

    > [!TIP]
    > Wenn Sie einen Fehler machen, können Sie sichern, indem Sie einen Schritt in löschen **ANGEWENDETE Schritte**.   
    
    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
4.  Filtern Sie die verbleibenden Tabellen um, indem Sie die folgenden Spalten in jeder Tabelle entfernen:  
    
    **DimDate**
    
      |Spalte|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |Spalte|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |Spalte|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |Spalte|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |Spalte|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      Keine Spalten entfernt.
  
## <a name="Import"></a>Import the selected tables and column data  

Nun, dass Sie in der Vorschau angezeigt und nicht benötigte Daten herausgefiltert haben, können Sie die restlichen Daten importieren, die Sie wünschen. Der Assistent importiert die Tabellendaten zusammen mit allen Beziehungen zwischen Tabellen. Neue Tabellen und Spalten im Modell erstellt werden, und Daten, die von Ihnen herausgefilterten wird nicht importiert werden.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>So importieren Sie ausgewählte Tabellen- und Spaltendaten  
  
1.  Überprüfen Sie Ihre Auswahl. Wenn alles korrekt erscheint, klicken Sie auf **Import**. Das Dialogfeld "Datenverarbeitung" zeigt den Status der aus Ihrer Datenquelle in Ihre arbeitsbereichsdatenbank importierten Daten.
  
    ![als lesson2-Erfolg](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  Klicken Sie auf **Schließen**.  

  
## <a name="save-your-model-project"></a>Speichern Sie Ihres modellprojekts  

Es ist wichtig, um das Modellprojekt häufig zu speichern.  
  
#### <a name="to-save-the-model-project"></a>So speichern Sie das Modellprojekt  
  
-   Click **Datei** > **Alle speichern**.  
  
## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 3: Als Datumstabelle markieren](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md).

  
  
