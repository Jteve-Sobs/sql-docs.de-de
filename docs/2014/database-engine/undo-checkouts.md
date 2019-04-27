---
title: Rückgängigmachen von Auscheckvorgängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2057c78f953645c9b1a5915b9912ab99263cb005
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773396"
---
# <a name="undo-checkouts"></a>Rückgängigmachen von Auscheckvorgängen
  Sie können die **Rückgängig: Auschecken** Befehl aus, um einen vorhandenen Auscheckvorgang abbrechen. Dies bietet sich vor allem an, wenn Sie eine Datei geändert und gespeichert haben und zu einem späteren Zeitpunkt ein Rollback für die Änderungen ausführen müssen.  
  
 Abhängig von den Optionen legen Sie in der **Rückgängig: Auschecken erweiterte Optionen** im Dialogfeld die Studio-Umgebung die Arbeitskopie des Elements verlässt, auf dem lokalen Datenträger oder durch die neueste Version unter quellcodeverwaltung ersetzt. Wenn ein Benutzer das Element außerhalb des Kontexts des Quellcodeverwaltungssystems geändert hat, handelt es sich bei der abgerufenen Version möglicherweise nicht um die letzte Version.  
  
### <a name="to-undo-a-checkout"></a>So machen Sie einen Auscheckvorgang rückgängig  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Auf der **Datei** Startmenü **Quellcodeverwaltung**, und klicken Sie dann auf **Rückgängig: Auschecken**.  
  
3.  In der **Rückgängig: Auschecken** (Dialogfeld), wählen die gewünschten Optionen aus, und klicken Sie dann auf die **Rückgängig: Auschecken** Schaltfläche.  
  
     **Spalten**  
     Bestimmt die anzuzeigenden Spalten und die Reihenfolge, in der sie angezeigt werden.  
  
     **Flache Ansicht**  
     Zeigt die Elemente als flache Listen unter der entsprechenden Verbindung mit der Quellcodeverwaltung an.  
  
     **Name**  
     Zeigt die Namen der Elemente an, für die das Auschecken rückgängig gemacht werden soll. Die Elemente werden mit einem aktivierten Kontrollkästchen neben dem Namen angezeigt. Wenn für ein Element das Auschecken nicht rückgängig gemacht werden soll, deaktivieren Sie das entsprechende Kontrollkästchen.  
  
     **Optionen**  
     Zeigt die für das Quellcodeverwaltungs-Plug-In spezifischen Optionen zum Rückgängigmachen des Auscheckens, wenn Sie auf den Pfeil rechts neben der Schaltfläche klicken.  
  
     **Sort**  
     Sortiert die Reihenfolge der Anzeigespalten.  
  
     **Strukturansicht**  
     Zeigt den Ordner und die Elementhierarchie für die Elemente an, für die das Auschecken rückgängig gemacht wird.  
  
     **Rückgängig: Auschecken**  
     Macht das Auschecken rückgängig, wobei alle Änderungen an der ausgecheckten Datei verworfen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auschecken von Dateien](../../2014/database-engine/check-out-files.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
