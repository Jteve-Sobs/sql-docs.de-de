---
title: Erstellen eines Berichtsverlaufs (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie in den Reporting Services im integrierten SharePoint-Modus einen Berichtsverlauf erstellen. Dabei handelt es sich um eine Sammlung von Berichtsmomentaufnahmen, die Sie im Laufe der Zeit erstellt haben.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1f27689e6f1e573c85c869fda36881a53401084d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547442"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a>Erstellen eines Berichtsverlaufs (Reporting Services im integrierten SharePoint-Modus)
  Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Jede Momentaufnahme ist eine Kopie des Berichts in dem Zustand, in dem er zum Zeitpunkt der Momentaufnahme vorlag. Er enthält das Layout und die Daten, die für den Bericht aktuell waren, als die Momentaufnahme erstellt wurde. Renderinginformationen werden nicht mit der Momentaufnahme gespeichert. Wenn Sie eine Momentaufnahme im Berichtsverlauf öffnen, wird er in HTML-Code im Berichts-Viewer-Webpart geöffnet. Nachdem er gerendert wurde, können Sie ihn in andere Anwendungsformate exportieren.  
  
 Damit ein Berichtsverlauf erstellt werden kann, muss der Bericht unbeaufsichtigt ausgeführt werden können (d. h., der Bericht muss vom Berichtsserver ohne Benutzerinteraktion ausgeführt werden können). Sie müssen über die Berechtigung zum Bearbeiten von Elementen für die Bibliothek, die den Bericht beinhaltet, verfügen. Zum Anzeigen und Löschen des Berichtsverlaufs müssen Sie über die Berechtigung zum Anzeigen von Versionen oder zum Löschen von Versionen verfügen.  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a>So erstellen Sie eine Momentaufnahme oder den Berichtsverlauf  
  
1.  Zeigen Sie auf den Bericht.  
  
2.  Klicken Sie darauf, um den Pfeil nach unten anzuzeigen, und wählen Sie dann **Berichtsverlauf anzeigen**aus.  
  
3.  Klicken Sie auf **Neue Momentaufnahme**. Ist die Schaltfläche nicht sichtbar, sind Sie nicht zum Erstellen von Momentaufnahmen im Berichtsverlauf berechtigt.  
  
4.  Wählen Sie die soeben erstellte Momentaufnahme in der Liste aus, um ihn anzuzeigen. Jede Momentaufnahme wird durch einen Timestamp identifiziert, der angibt, wann die Momentaufnahme erstellt wurde. Sie können die Momentaufnahme nicht umbenennen, ihn nicht an eine andere Position verschieben und ihn nicht ändern.  
  
### <a name="to-schedule-report-history"></a>So planen Sie den Berichtsverlauf  
  
1.  Zeigen Sie auf den Bericht.  
  
2.  Klicken Sie darauf, um den Pfeil nach unten anzuzeigen, und wählen Sie dann **Verarbeitungsoptionen verwalten**aus.  
  
3.  Klicken Sie unter **Optionen für Verlaufsmomentaufnahmen**auf **Berichtsverlaufs-Momentaufnahmen nach einem Zeitplan erstellen**.  
  
4.  Wenn ein freigegebener Zeitplan vorhanden ist, der die gewünschten Zeitplaninformationen enthält, klicken Sie auf **Nach einem freigegebenen Zeitplan** , und wählen Sie den gewünschten Zeitplan aus. Andernfalls klicken Sie auf **Nach einem benutzerdefinierten Zeitplan**, und klicken Sie dann auf **Konfigurieren** , um Optionen zum Erstellen des Berichtsverlaufs nach einem sich wiederholenden Zeitplan anzugeben.  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a>So erstellen Sie einen Berichtsverlauf, wenn Daten in einem Bericht aktualisiert werden  
  
1.  Zeigen Sie auf den Bericht.  
  
2.  Klicken Sie darauf, um den Pfeil nach unten anzuzeigen, und wählen Sie dann **Verarbeitungsoptionen verwalten**aus.  
  
3.  Klicken Sie unter **Optionen für Verlaufsmomentaufnahmen**auf **Alle Berichtsdaten-Momentaufnahmen im Berichtsverlauf speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Verarbeitungsoptionen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
