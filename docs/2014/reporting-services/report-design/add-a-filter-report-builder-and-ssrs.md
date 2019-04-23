---
title: Hinzufügen eines Berichts (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 10ae54e7-0e8a-4dff-995d-05516c51d076
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca43df4b6dc42e15257ce7e3c31b2b91ec0a7b73
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972066"
---
# <a name="add-a-filter-report-builder-and-ssrs"></a>Hinzufügen eines Filters (Berichts-Generator und SSRS)
  Fügen Sie einem Dataset, einem Datenbereich oder einer Gruppe einen Filter hinzu, wenn Sie spezifische Werte in Berechnungen oder in die Anzeige einschließen bzw. davon ausschließen möchten. Filter werden zuerst auf das Dataset, dann auf den Datenbereich und anschließend auf die Gruppe angewendet (von oben nach unten bei Gruppenhierarchien). In einer Tabelle, Matrix oder Liste werden Filter für Zeilen- und Spaltengruppen sowie für angrenzende Gruppen unabhängig voneinander angewendet. In Diagrammen werden Filter für Kategorie- und Reihengruppen unabhängig voneinander angewendet.  
  
 Um einen Filter hinzuzufügen, müssen Sie eine oder mehrere Filtergleichungen angeben. Eine Filtergleichung besteht aus einem Ausdruck, der die zu filternden Daten definiert, einem Operator und dem Vergleichswert. Der Datentyp der gefilterten Daten und des Werts muss übereinstimmen. Bei Datasets und Datenbereichen wird das Filtern anhand aggregierter Werte nicht unterstützt.  
  
 Um Datenpunkte in einem Diagramm zu filtern, können Sie einen Filter für eine Kategoriegruppe oder eine Reihengruppe festlegen. Standardmäßig verwendet das Diagramm die integrierte Funktion „Sum“, um Werte, die zur selben Gruppe gehören, in einem einzelnen Datenpunkt in der Reihe zu aggregieren. Falls Sie die Aggregatfunktion einer Reihe ändern, müssen Sie auch die Aggregatfunktion im Filterausdruck ändern.  
  
 Weitere Informationen zum Filtern von eingebetteten und freigegebenen Datasets finden Sie unter [Hinzufügen eines Filters zu einem Dataset (Berichts-Generator und SSRS)](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-filter-on-a-data-region"></a>So legen Sie einen Filter für einen Datenbereich fest  
  
1.  Öffnen Sie einen Bericht in der **Entwurfssicht** .  
  
2.  Wählen Sie den Datenbereich auf der Entwurfsoberfläche aus, und klicken Sie anschließend mit der rechten Maustaste auf _\<Datenbereich>_**Eigenschaften**. Wählen Sie bei einem Messgerät **Messgerätbereichseigenschaften**aus. Das Dialogfeld _\<Datenbereich>_**Eigenschaften** wird geöffnet.  
  
    > [!NOTE]  
    >  Klicken Sie im Tablix-Datenbereich mit der rechten Maustaste auf das Handle in der Eckzelle, einer Zeile oder Spalte, und klicken Sie anschließend auf **Tablix-Eigenschaften**.  
  
3.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
4.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
5.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
6.  Wählen Sie im Dropdownfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
7.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
8.  Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](filter-equation-examples-report-builder-and-ssrs.md).  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-tablix-row-or-column-group"></a>So legen Sie einen Filter für eine Tablix-Zeilen- oder Spaltengruppe fest  
  
1.  Öffnen Sie einen Bericht in der **Entwurfssicht** .  
  
2.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf den Tabellen-, Matrix- oder Listendatenbereich, um ihn auszuwählen. Im Gruppierungsbereich werden die Gruppen für das ausgewählte Element angezeigt.  
  
3.  Klicken Sie im Gruppierungsbereich mit der rechten Maustaste auf die Gruppe, und klicken Sie anschließend auf **Gruppe bearbeiten**. Das Dialogfeld **Tablix-Gruppe** wird geöffnet.  
  
4.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
5.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
6.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
7.  Wählen Sie im Dropdownfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
8.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
9. Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](filter-equation-examples-report-builder-and-ssrs.md).  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-category-group"></a>So legen Sie einen Filter für eine Diagrammkategoriegruppe fest  
  
1.  Öffnen Sie einen Bericht in der **Entwurfssicht** .  
  
2.  Klicken Sie auf der Entwurfsoberfläche zwei Mal auf das Diagramm, um die Daten-, Reihen- und Kategoriefeldablagezonen anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Feld in der Kategoriefeldablagezone, und wählen Sie **Kategoriegruppeneigenschaften**aus.  
  
4.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
5.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
6.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
7.  Wählen Sie im Dropdownfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
8.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
9. Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](filter-equation-examples-report-builder-and-ssrs.md).  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-series-group"></a>So legen Sie einen Filter für eine Diagrammreihengruppe fest  
  
1.  Öffnen Sie einen Bericht in der **Entwurfssicht** .  
  
2.  Klicken Sie auf der Entwurfsoberfläche zwei Mal auf das Diagramm, um die Daten-, Reihen- und Kategoriefeldablagezonen anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Feld in der Reihenfeldablagezone, und wählen Sie **Reihengruppeneigenschaften**aus.  
  
4.  Klicken Sie auf **Filter**. Die aktuelle Liste mit Filtergleichungen wird angezeigt. Standardmäßig ist die Liste leer.  
  
5.  Klicken Sie auf **Hinzufügen**. Es wird eine neue leere Filtergleichung angezeigt.  
  
6.  Geben Sie unter **Ausdruck**einen Ausdruck für das zu filternde Feld ein, oder wählen Sie einen Ausdruck aus. Wenn Sie den Ausdruck bearbeiten möchten, klicken Sie auf die Ausdrucksschaltfläche (*fx*).  
  
7.  Wählen Sie im Dropdownfeld den Datentyp aus, der dem Typ der Daten in dem Ausdruck entspricht, den Sie in Schritt 5 erstellt haben.  
  
8.  Wählen Sie im Feld **Operator** den Operator aus, der vom Filter zum Vergleichen der Werte in den Feldern **Ausdruck** und **Wert** verwendet werden soll. Der gewählte Operator bestimmt, wie viele Werte ab dem nächsten Schritt verwendet werden.  
  
9. Geben Sie im Feld **Wert** den Ausdruck oder Wert ein, den der Filter mit dem Wert im Feld **Ausdruck**vergleichen soll.  
  
     Beispiele für Filtergleichungen finden Sie unter [Beispiele für Filtergleichungen (Berichts-Generator und SSRS)](filter-equation-examples-report-builder-and-ssrs.md).  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](gauges-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
