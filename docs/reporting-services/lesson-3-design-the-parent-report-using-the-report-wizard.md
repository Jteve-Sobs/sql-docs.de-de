---
title: 'Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation'
description: Hier erfahren Sie, wie Sie mithilfe des Berichts-Assistenten im Berichts-Designer einen übergeordneten Bericht erstellen, nachdem Sie eine Datenverbindung und eine Datentabelle für Ihren übergeordneten Bericht erstellt haben.
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 74b71002f5f84f4d9b80966f6b44721b9942c8b4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247529"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten
Nachdem Sie eine Datenverbindung und eine Datentabelle für den übergeordneten Bericht erstellt haben, entwerfen Sie im nächsten Schritt den übergeordneten Bericht mithilfe des Berichts-Assistenten im Berichts-Designer. Weitere Informationen zum Berichts-Designer finden Sie unter [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>So entwerfen Sie den übergeordneten Bericht mithilfe des Berichts-Assistenten  
  
1.  Stellen Sie sicher, dass die Website der obersten Ebene im **Projektmappen-Explorer**ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Website, und wählen Sie **Neues Element hinzufügen**aus.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Berichts-Assistent**aus, geben Sie einen Namen für die Berichtsdatei ein, und wählen Sie anschließend **Hinzufügen**aus.  
  
    Daraufhin wird der Berichts-Assistent gestartet.  
  
4.  Wählen Sie auf der Seite **Dataseteigenschaften** im Feld **Datenquelle** das **DataSet1** aus, das Sie in [Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)erstellt haben.  
  
    Das Feld **Verfügbare Datasets** wird automatisch anhand der oben erstellten **DataTable** aktualisiert.  
  
5.  Wählen Sie **Weiter** aus.  
  
6.  Gehen Sie auf der Seite **Felder anordnen** wie folgt vor:  
  
    1.  Ziehen Sie **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**und **ReorderLevel** vom Feld **Verfügbare Felder** auf das Feld **Werte** .  
  
    2.  Klicken Sie auf den Pfeil neben **Sum(ProductID)** , **Sum(SafetyStockLevel)** und **Sum(ReorderLevel)** , und löschen Sie die Auswahl **Sum** .  
  
7.  Klicken Sie zweimal auf **Weiter** und anschließend auf **Fertig stellen** , um den **Berichts-Assistenten**zu schließen.  
  
    Die RDLC-Datei ist jetzt erstellt. Die Datei wird im Berichts-Designer geöffnet. Die entworfene Tablix wird jetzt auf der Entwurfsoberfläche angezeigt.  
  
8.  Speichern Sie die RDLC-Datei.  
  
## <a name="next-task"></a>Nächste Aufgabe  
Sie haben erfolgreich den übergeordneten Bericht mithilfe des Berichts-Assistenten entworfen. Als Nächstes erstellen Sie eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht. Siehe [Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  

