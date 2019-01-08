---
title: Ändern von Zeitzonen und Systemuhreinstellungen auf einem Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 79df62b8215c242c7f2af2032bdb7671281178fd
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362332"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a>Ändern von Zeitzonen und Zeiteinstellungen auf einem Berichtsserver
  Ein Berichtsserver verwendet immer die lokale Zeit des Computers, auf dem dieser installiert ist. Es ist nicht möglich, die Verwendung einer anderen Zeitzone zu konfigurieren. Falls eine Clientanwendung auf einen Berichtsserver in einer anderen Zeitzone verweist, wird die Zeitzone des Berichtsservers zum Ausführen einer geplanten Operation verwendet. Im Berichts-Manager und auf den SharePoint-Verwaltungsseiten wird die Zeitzone auf jeder Zeitplanungsseite angezeigt, damit Sie genau wissen, wann ein geplanter Vorgang ausgeführt wird. Auf der Seite zum Erstellen benutzerdefinierter Zeitpläne kann beispielsweise „Uhrzeiten werden dargestellt in (UTC-08:00) Pazifische Zeit (USA und Kanada)“ angegeben sein.  
  
## <a name="changing-the-time-zone-native-mode"></a>Ändern der Zeitzone (einheitlicher Modus)  
 Falls Sie die Zeitzone auf einem Computer ändern, der einen Berichtsserver hostet, müssen Sie den Berichtsserverdienst neu starten, damit die Änderung der Zeitzone wirksam wird.  
  
 Timestampwerte vorhandener Berichtsverlaufs-Momentaufnahmen werden mit der neuen Zeitzoneneinstellung synchronisiert. Wenn Sie um 9:00 Uhr eine Berichtsverlaufs-Momentaufnahme generiert haben und dann die Zeitzone um eine Zeitzone vorstellen, wird der Timestamp der generierten Momentaufnahme von 9:00 auf 10:00 Uhr geändert.  
  
 Für Zeitpläne bleiben die vorhandenen Einstellungen erhalten, außer sie werden der neuen Zeitzone zugeordnet. Wird beispielsweise ein Zeitplan um 2:00 Uhr Pacific Standard Time ausgeführt, und Sie ändern die Zeitzone in East Australia Standard Time, wird der Zeitplan um 2:00 Uhr East Australia Standard Time ausgeführt.  
  
 Timestampwerte von Eigenschaften (z. B. die Zeit, zu der ein Ordner oder ein verknüpftes Berichtselement erstellt wurde) werden nicht mit einer neuen Zeitzoneneinstellung synchronisiert. Falls Sie ein Element am 25. Juni um 9:00 Uhr erstellen und dann die Zeitzone oder die Uhrzeit ändern, wird der Timestamp 25. Juni um 9:00 Uhr beibehalten.  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a>Ändern der Zeitzone (SharePoint-Modus)  
 Die Zeitzonenkonfiguration für den SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] werden im Rahmen der Regionaleinstellungen von SharePoint verwaltet. Weitere Informationen finden Sie unter [Ländereinstellungen (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx).  
  
## <a name="changing-the-clock-settings"></a>Ändern der Zeiteinstellungen  
 Die Änderung an der Computeruhr hat keine Auswirkung auf vorhandene Timestampwerte (z. B., wenn Sie die Computeruhr um eine Stunde vorstellen, werden die Timestamps von Berichtsverlaufs-Momentaufnahmen nicht geändert). Es kann etwa 10 Sekunden dauern, bis der Prozessor für Zeitplanung und Übermittlung die neue Einstellung verwendet. Diese Verzögerung kann variieren, wenn Sie Einstellungen für das Abfrageintervall in den Konfigurationsdateien geändert haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden des Berichtsserverdiensts](../report-server/start-and-stop-the-report-server-service.md)   
 [Zeitpläne](schedules.md)  
  
  
