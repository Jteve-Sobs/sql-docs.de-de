---
title: 'Lektion 3: Markieren als Datumstabelle | Microsoft-Dokumentation'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 664b7198f0924618316a5bb47a3ac1fb4da13f7a
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404152"
---
# <a name="lesson-3-mark-as-date-table"></a>Lektion 3: Als Datumstabelle markieren
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In Lektion 2: Hinzufügen von Daten, haben Sie eine Dimensionstabelle namens DimDate importiert. In Ihrem Modell mit DimDate benannte Tabelle ist, sie können auch bezeichnet werden als eine *Datumstabelle*, darin, dass es sich um Datums-und Uhrzeitdaten enthält.  
  
Wenn Sie DAX-zeitintelligenzfunktionen in Berechnungen verwenden, wie Sie erledigen, wenn Sie Measures erstellen, müssen Sie angeben, dass Eigenschaften von Datentabellen, darunter eine *Datumstabelle* und einen eindeutigen Bezeichner *Datum Spalte* in dieser Tabelle.
  
In dieser Lektion markieren Sie die DimDate-Tabelle als die *Datumstabelle* und die Spalte "Date" (in der Datumstabelle) als die *Datumsspalte* (Eindeutiger Bezeichner).  

Bevor wir die Datumstabelle und Datumsspalte markieren, müssen wir einige einfache Wartungsaufgaben, um unser Modell verständlicher zu machen. Sie sehen in der Tabelle DimDate eine Spalte namens **FullDateAlternateKey**. Es enthält eine Zeile für jeden Tag in jedem Kalenderjahr in der Tabelle. Wir werden diese Spalte viele in measureformeln und Berichten verwenden. Allerdings FullDateAlternateKey ist nicht wirklich kein guter Bezeichner für diese Spalte. Benennen wir es **Datum**, um zu identifizieren, und schließen Sie in Formeln zu vereinfachen. Wann immer möglich, ist es eine gute Idee, Umbenennen von Objekten wie Tabellen und Spalten, um sie leichter in Clientanwendungen zur berichterstellung wie Power BI und Excel identifiziert werden können. 
  
Geschätzte Zeit zum Abschließen dieser Lektion: **3 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 2: Hinzufügen von Daten](lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Zum Umbenennen der Spalte FullDateAlternateKey

1.  Klicken Sie im Modell-Designer auf die **DimDate** Tabelle.

2.  Klicken Sie mit der Doppelklicken auf die Kopfzeile für die **FullDateAlternateKey** Spalte, und benennen Sie sie in **Datum**.

  
### <a name="to-set-mark-as-date-table"></a>So legen Sie "Als Datumstabelle markieren" fest  
  
1.  Wählen Sie die **Datum** -Spalte und stellen Sie anschließend im Fenster **Eigenschaften** unter **Datentyp**sicher, dass  **Datum** ausgewählt ist.  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum**und anschließend auf **Als Datumstabelle markieren**.  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** die Spalte **Datum** als eindeutigen Bezeichner aus. Sie wird in der Regel standardmäßig ausgewählt. Klicken Sie auf **OK**. 

    ![as-tabular-lesson3-date-table](media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 4: Erstellen von Beziehungen](lesson-4-create-relationships.md).
  
