---
title: Filtern von Daten in einer Analysis Services-Tabellenmodell-Tabelle | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b1fcdda5bd49f8056a6035ec10da8fb52f1c5d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162811"
---
# <a name="filter-data-in-a-table"></a>Filtern von Daten in einer Tabelle 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sie können beim Importieren von Daten Filter anwenden, um zu steuern, welche Zeilen in eine Tabelle geladen werden. Nachdem Sie die Daten importiert haben, können Sie keine einzelnen Zeilen löschen. Sie können jedoch benutzerdefinierte Filter anwenden, um zu steuern, wie Zeilen angezeigt werden. Zeilen, die die Filterkriterien nicht erfüllen, werden ausgeblendet. Sie können nach einer oder mehreren Spalten filtern. Filter sind additiv. Das bedeutet, dass jeder zusätzliche Filter auf dem aktuellen Filter basiert und die Teilmenge der Daten weiter reduziert.  
  
> [!NOTE]  
>  Das Filtervorschaufenster schränkt die Anzahl der unterschiedlichen Werte ein, die angezeigt werden. Wenn die Grenze überschritten wird, wird eine Meldung angezeigt.  
  
### <a name="to-filter-data-based-on-column-values"></a>So filtern Sie Daten auf Grundlage von Spaltenwerten  
  
1.  Wählen Sie im Modell-Designer eine Tabelle aus, und klicken Sie dann auf den Pfeil in der Kopfzeile der Spalte, nach der Sie filtern möchten.  
  
2.  Führen Sie im Menü AutoFilter einen der folgenden Schritte aus:  
  
    -   Wählen Sie in der Liste der Spaltenwerte mindestens einen Wert aus, nach dem gefiltert werden soll, bzw. heben Sie die Auswahl auf, und klicken Sie auf **OK**.  
  
         Wenn die Anzahl der Werte sehr groß ist, kann es sein, dass einzelne Elemente nicht in der Liste angezeigt werden. Stattdessen wird eine Meldung angezeigt, dass zu viele Elemente zum Anzeigen vorhanden sind.  
  
    -   Klicken Sie je nach Typ der Spalte auf **Zahlenfilter** oder **Textfilter** , und klicken Sie anschließend auf einen der Vergleichsoperatorbefehle (wie **Ist gleich**), oder klicken Sie auf **Benutzerdefinierter Filter**. Erstellen Sie im Dialogfeld **Benutzerdefinierter Filter** den Filter, und klicken Sie dann auf **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>So löschen Sie einen Filter für eine Spalte  
  
1.  Klicken Sie auf den Pfeil in der Kopfzeile der Spalte, für die Sie den Filter löschen möchten.  
  
2.  Klicken Sie auf **Filter löschen aus \<Spaltenname >** .  
  
### <a name="to-clear-all-filters-for-a-table"></a>So löschen Sie alle Filter für eine Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, für die Sie die Filter löschen möchten.  
  
2.  Klicken Sie auf das Menü **Spalte** und dann auf **Alle Filter löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Filtern und Sortieren von Daten](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Perspektiven](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
