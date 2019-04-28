---
title: 'Lektion 9: Erstellen von Hierarchien | Microsoft-Dokumentation'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da8f3d0fb3f733c5a9307d633025bb67a1a4d8cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017261"
---
# <a name="lesson-9-create-hierarchies"></a>Lektion 9: Erstellen von Hierarchien
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie Hierarchien. Hierarchien sind Gruppen von Spalten, die in Ebenen angeordnet werden. Beispielsweise könnte eine Geografiehierarchie Unterebenen für Land, Status, Landkreis und Stadt beinhalten. Hierarchien können getrennt von anderen Spalten in der Feldliste einer Clientanwendung zur Berichtserstellung angezeigt werden, sodass Clientbenutzer einfacher darin navigieren und sie in einen Bericht aufnehmen können. Weitere Informationen finden Sie unter [Hierarchien](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Verwenden Sie zum Erstellen von Hierarchien den Modell-Designer in *Diagrammansicht*. Erstellen und Verwalten von Hierarchien wird in der Datensicht nicht unterstützt.  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 8: Erstellen von Perspektiven](../analysis-services/lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Erstellen von Hierarchien  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>So erstellen Sie eine Kategoriehierarchie in der DimProduct-Tabelle  
  
1.  Im Modell-Designer (Diagrammsicht) mit der Maustaste der **DimProduct** Tabelle > **Hierarchie erstellen**. Eine neue Hierarchie wird am unteren Rand des Tabellenfensters angezeigt. Benennen Sie die Hierarchie **Kategorie**.  
  
2.  Klicken Sie auf, und ziehen Sie die **"productcategoryname"** Spalte mit dem neuen **Kategorie** Hierarchie.  
  
3.  In der **Kategorie** Hierarchie mit der rechten Maustaste die **"productcategoryname"** > **umbenennen**, und geben Sie dann **Kategorie**.  
  
    > [!NOTE]  
    > Durch das Umbenennen einer Spalte in einer Hierarchie wird die betreffende Spalte in der Tabelle nicht umbenannt. Eine Spalte in einer Hierarchie ist nur eine Darstellung der Spalte in der Tabelle.  
  
4.  Klicken Sie auf, und ziehen Sie die **ProductSubcategoryName** Spalte die **Kategorie** Hierarchie. Benennen Sie sie **Subcategory**. 
  
5.  Mit der rechten Maustaste die **ModelName** Spalte > **zur Hierarchie hinzufügen**, und wählen Sie dann **Kategorie**. Gleiches gilt für **EnglishProductName**. Benennen Sie diese Spalten in der Hierarchie **Modell** und **Produkt**.  

    ![as-tabular-lesson9-category](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>So erstellen Sie Hierarchien in der DimDate-Tabelle  
  
1.  In der **DimDate** Tabelle, erstellen Sie eine neue Hierarchie, die mit dem Namen **Kalender**.  
  
3.  Fügen Sie die folgenden Spalten in dieser Reihenfolge hinzu:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  In der **DimDate** Tabelle, erstellen Sie eine **Geschäftskalender** Hierarchie. Sind die folgenden Spalten:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Schließlich wird in der **DimDate** Tabelle, erstellen Sie eine **ProductionCalendar** Hierarchie. Sind die folgenden Spalten:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 10: Erstellen von Partitionen](../analysis-services/lesson-10-create-partitions.md). 
  
  
