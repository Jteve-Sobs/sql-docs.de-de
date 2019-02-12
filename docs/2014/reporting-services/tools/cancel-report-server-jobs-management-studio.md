---
title: Berichtsserveraufträge abbrechen (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 59ab630cfbae4dc642eb7dbe200d913e36720b47
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013169"
---
# <a name="cancel-report-server-jobs-management-studio"></a>Berichtsserveraufträge abbrechen (Management Studio)
  Verwenden Sie das Dialogfeld **Berichtsserveraufträge abbrechen** , um ausgeführte Berichte anzuzeigen oder abzubrechen. Dieses Dialogfeld zeigt alle Aufträge an, die gerade auf dem Berichtsserver ausgeführt werden. Zwar können Sie gerade bearbeitete Aufträge nicht anhalten oder neu starten, jedoch können Sie alle oder einzelne Aufträge abbrechen, wenn ihr Abschluss zu lange dauert.  
  
 Sie können sowohl Benutzer- als auch Systemaufträge abbrechen.  
  
-   Als Benutzerauftrag wird ein Auftrag bezeichnet, der durch einen einzelnen Benutzer initiiert wird. Dazu zählt das Ausführen eines Berichts bei Bedarf, das manuelle Erstellen einer Momentaufnahme zum Berichtsverlauf oder das manuelle Erstellen einer Momentaufnahme zur Berichtsausführung. Ein ausgeführtes Standardabonnement wird ebenfalls als Benutzerauftrag bezeichnet.  
  
-   Als Systemauftrag wird ein Auftrag bezeichnet, der durch den Berichtsserver initiiert wird. Systemaufträge schließen die geplante Berichtsverarbeitung ein.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einem Berichtsserver herstellen. Klicken Sie mit der rechten Maustaste auf **Aufträge**, und klicken Sie anschließend auf **Alle Aufträge abbrechen**. Sie können auch **Aufträge**öffnen und mit der rechten Maustaste auf einen auf dem Berichtsserver ausgeführten Auftrag klicken. Klicken Sie anschließend auf **Aufträge abbrechen**.  
  
 Vor dem Abbrechen eines Auftrags können Sie seine Eigenschaften anzeigen, um zu bestimmen, wann der Auftrag gestartet wurde. Weitere Informationen finden Sie unter [Auftragseigenschaften (Management Studio)](job-properties-management-studio.md).  
  
> [!NOTE]  
>  Diese Funktion wird in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services nicht unterstützt. Die Seite wird nicht angezeigt, wenn Sie [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]ausführen.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Zeigt den Berichtsnamen an. Abonnements werden durch ihre Beschreibung identifiziert.  
  
 **Typ**  
 Die gültigen Werte sind **Benutzer** und **System**.  
  
 **Startzeit**  
 Zeigt an, wann der Auftrag gestartet wurde.  
  
 **Benutzername**  
 Bei Aufträgen, die von einem Benutzer initiiert wurden, zeigt diese Spalte den Namen des Benutzers an.  
  
 **Status**  
 Zeigt den Status des Auftrags an. Gültige Werte sind **Neu** und **Wird ausgeführt**. Bei Beginn des Auftrags ist der Status immer **Neu** . Nach 60 Sekunden ändert sich der Status in **Wird ausgeführt**. Sie müssen die Seite aktualisieren, damit die Änderung übernommen wird.  
  
 **OK**  
 Brechen Sie einen einzelnen Auftrag oder mehrere Aufträge ab. Die Aufträge werden sofort abgebrochen und können nicht wiederaufgenommen werden. Wenn Sie versehentlich einen Auftrag abgebrochen haben, müssen sie den Bericht oder das Abonnement erneut anfordern, um einen neuen Auftrag zu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Verwalten eines ausgeführten Prozesses](../subscriptions/manage-a-running-process.md)  
  
  
