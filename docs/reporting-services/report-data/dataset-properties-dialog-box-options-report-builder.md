---
title: Dataseteigenschaften (Dialogfeld), Optionen (Berichts-Generator) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie über das Dialogfeld „Dataseteigenschaften“ Datenoptionen ändern, z. B. Sortierungsoptionen oder die Behandlung von Zwischensummen als Detaildaten.
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10020"
- sql13.rtp.rptdesigner.datasetproperties.options.f1
- "10130"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 141e2f9639ecd89113f738546f47053d9ab630fd
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812265"
---
# <a name="dataset-properties-dialog-box-options-report-builder"></a>Dataseteigenschaften (Dialogfeld), Optionen (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Optionen** aus, um Datenoptionen, wie Sortierungsoptionen und die Behandlung von Zwischensummen als Detaildaten, für die Abfrage zu ändern. Weitere Informationen zur Sortierung finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 Datenoptionen, die Teil einer freigegebenen Datasetdefinition auf dem Berichtsserver sind, wirken sich auf alle Berichte aus, die das freigegebene Dataset verwenden. Sie können Optionen für das freigegebene Dataset überschreiben, nachdem es einem Bericht hinzugefügt wurde. Diese Änderungen wirken sich nur auf den Bericht aus, in dem sie definiert werden.  
  
 Datenoptionen für ein eingebettetes Dataset wirken sich nur auf den Bericht aus, in dem sie definiert werden.  
  
 Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Sortierung**  
 Wählen Sie ein Gebietsschema aus, das die zum Sortieren der Daten verwendete Sortierreihenfolge bestimmt. Der Wert**Standard** gibt an, dass der Bericht diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Wert nicht hergeleitet werden kann, wird der Standardwert von der Gebietsschemaeinstellung des Computers hergeleitet.  
  
 **Unterscheidung nach Groß-/Kleinschreibung**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Groß-/Kleinschreibung zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten die Groß-/Kleinschreibung unterschieden wird. Sie können **Unterscheidung nach Groß-/Kleinschreibung** auf **Wahr**, **Falsch**oder **Automatisch**festlegen. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Groß- und Kleinschreibung unterstützt, wird der Bericht so ausgeführt, als sei **FALSE**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Akzent**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Akzent zu bestimmen. Mithilfe der Option**Unterscheidung nach Akzent** wird angegeben, ob bei den Daten nach Akzent unterschieden wird. Mögliche Werte sind **Wahr**, **Falsch**und **Automatisch**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Akzent unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Kanatyp**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Kanatyp zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten nach Kanatyp unterschieden wird. Mögliche Werte sind **Wahr**, **Falsch**und **Automatisch**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Kanatyp unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Breite**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Breite zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten nach Breite unterschieden wird. Mögliche Werte sind **TRUE**, **FALSE**oder **Auto**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Breite unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Teilergebnisse als Detailzeilen interpretieren**  
 Wählen Sie einen Wert aus, der angibt, ob Teilergebniszeilen als Detailzeilen statt als Aggregatzeilen interpretiert werden sollen. Der Standardwert **Auto**gibt an, dass die Teilergebniszeilen als Detailzeilen behandelt werden sollen, wenn der Bericht für den Zugriff auf Felder im Dataset nicht die **Aggregate**()-Funktion verwendet. Wenn Teilergebniszeilen als Aggregatzeilen interpretiert werden sollen, wählen Sie **False**aus. Wenn die Teilergebniszeilen als Detailzeilen interpretiert werden sollen und Sie wissen, dass sie die **Aggregate**()-Funktion nicht verwenden, wählen Sie **TRUE**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aggregatfunktion (Berichts-Generator und SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-function.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Dialogfeld Dataseteigenschaften, Abfrage (Berichts-Generator)](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md)  
  
  
