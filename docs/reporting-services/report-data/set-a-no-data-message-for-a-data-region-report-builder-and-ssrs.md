---
title: Festlegen einer Meldung über fehlende Daten für einen Datenbereich (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a78a71caf85bad0df6d21f22c305a93898c122df
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579040"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>Festlegen einer Meldung über fehlende Daten für einen Datenbereich (Berichts-Generator und SSRS)
  Legen Sie die NoRowsMessage-Eigenschaft für eine Tabelle, eine Matrix oder einen Listendatenbereich, die NoDataMessage-Eigenschaft für einen Diagrammdatenbereich und die NoDataText-Eigenschaft für die Farbskala einer Karte fest, wenn Sie Text angeben möchten, der im gerenderten Bericht anstelle von Datenbereichen ohne Daten angezeigt wird. Zur Laufzeit führt der Berichtsprozessor die Abfrage für die einzelnen Datasets in einem Bericht aus. Bei einer Datasetabfrage kann es vorkommen, dass kein Resultset zurückgegeben wird. Für Datenbereiche, die an leere Datasets gebunden sind, können Sie Text angeben, der anstelle der leeren Datenbereiche angezeigt wird. Sie können die NoRowsMessage-Eigenschaft auch für Unterberichte festlegen, für deren Datasets zur Laufzeit keine Daten zurückgegeben werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>So legen Sie die NoRowsMessage-Eigenschaft für eine Tabelle, Matrix oder Liste fest  
  
1.  Klicken Sie in der Entwurfsansicht auf die Tabelle, die Matrix, den Listendatenbereich oder auf den Unterbericht auf der Entwurfsoberfläche, um ihn auszuwählen. Die Eigenschaften für das ausgewählte Element werden im Eigenschaftenbereich angezeigt.  
  
2.  Geben Sie im Eigenschaftenbereich den Text, der als Meldung angezeigt werden soll, in das **NoRowsMessage** -Eigenschaftenfeld ein.  
  
     Sie können auch in der Dropdownliste auf **Ausdruck** klicken, um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen.  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>So legen Sie die NoDataMessage-Eigenschaft für ein Diagramm fest  
  
1.  Klicken Sie in der Entwurfsansicht auf das Diagramm auf der Entwurfsoberfläche, um dieses auszuwählen. Die Eigenschaften für das ausgewählte Element werden im Eigenschaftenbereich angezeigt.  
  
2.  Erweitern Sie im Eigenschaftenbereich den Knoten **NoDataMessage**.  
  
3.  Geben Sie unter **Beschriftung**den Text in das Eigenschaftenfeld **NoDataMessage** ein, der als Meldung angezeigt werden soll.  
  
     Sie können auch in der Dropdownliste auf **Ausdruck** klicken, um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen.  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>So legen Sie die NoRowsMessage für einen Unterbericht fest  
  
1.  Klicken Sie in der Entwurfsansicht auf den Unterbericht auf der Entwurfsoberfläche, um diesen auszuwählen. Die Eigenschaften für das ausgewählte Element werden im Eigenschaftenbereich angezeigt.  
  
2.  Geben Sie im Eigenschaftenbereich den Text, der als Meldung angezeigt werden soll, in das **NoRowsMessage** -Eigenschaftenfeld ein.  
  
     Sie können auch in der Dropdownliste auf **Ausdruck** klicken, um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen.  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>So legen Sie die NoDataText-Eigenschaft für eine Farbskala für eine Karte fest  
  
1.  Klicken Sie in der Entwurfsansicht auf die Farbskala auf der Karte, um sie auszuwählen. Die Eigenschaften für das ausgewählte Element werden im Eigenschaftenbereich angezeigt.  
  
2.  Geben Sie im Bereich "Eigenschaften" in **NoDataText**den Text ein, der als Bezeichnung für Farben ohne Datenwert angezeigt werden soll.  
  
     Sie können auch in der Dropdownliste auf **Ausdruck** klicken, um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterberichte &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Karten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Unterberichte &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)  
  
  
