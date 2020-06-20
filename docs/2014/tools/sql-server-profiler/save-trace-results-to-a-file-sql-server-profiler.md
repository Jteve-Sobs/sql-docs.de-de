---
title: Speichern von Ablaufverfolgungsergebnissen in einer Datei (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5abe414a83a118fdc078f637384699280a08b995
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007175"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a>Speichern von Ablaufverfolgungsergebnissen in einer Datei (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Ablaufverfolgungsergebnisse mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]in einer Datei gespeichert werden.  
  
### <a name="to-save-trace-results-to-a-file"></a>So speichern Sie Ablaufverfolgungsergebnisse in einer Datei  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Aktivieren Sie das Kontrollkästchen **In Datei speichern** .  
  
     Das Dialogfeld **Speichern unter**wird angezeigt.  
  
4.  Geben Sie im Dialogfeld **Speichern unter**den Pfad und den Dateinamen an. Klicken Sie auf **Speichern**.  
  
    > [!NOTE]  
    >  Stellen Sie sicher, dass der SQL Server-Dienst die entsprechenden Berechtigungen hat, um in eine Datei im angegebenen Verzeichnis zu schreiben.  
  
5.  Geben Sie im Dialogfeld **Ablaufverfolgungseigenschaften** die maximale Dateigröße in das Textfeld **Maximale Dateigröße festlegen (MB)** ein. Der Standardwert ist 5 MB.  
  
6.  Geben Sie optional die folgenden Optionen an:  
  
    -   Aktivieren Sie das Kontrollkästchen **Dateirollover aktivieren** , damit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] neue Dateien für Ablaufverfolgungsdaten erstellt, wenn die maximale Dateigröße erreicht wird. Diese Option ist standardmäßig aktiviert.  
  
    -   Aktivieren Sie das Kontrollkästchen **Ablaufverfolgungsdaten von Serverprozessen** , um sicherzustellen, dass der Server jedes Ablaufverfolgungsereignis aufzeichnet.  
  
        > [!NOTE]  
        >  Wenn **Ablaufverfolgungsdaten von Serverprozessen**deaktiviert ist, zeichnet der Server keine Ereignisse auf, falls dadurch die Leistung erheblich beeinträchtigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
