---
title: Programmgesteuertes Erstellen von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 188e2b824a033365ec366d3b5f7474b261b1bbf2
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393648"
---
# <a name="building-packages-programmatically"></a>Programmgesteuertes Erstellen von Paketen
  Wenn Sie Pakete dynamisch erstellen oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete außerhalb der Entwicklungsumgebung verwalten und ausführen müssen, können Sie Pakete programmgesteuert ändern. Dieser Ansatz bietet Ihnen eine breite Palette von Optionen:  
  
-   Laden und Ausführen eines vorhandenen Pakets ohne Änderung  
  
-   Laden, Neukonfigurieren (z. B. für eine andere Datenquelle) und Ausführen eines vorhandenen Pakets  
  
-   Erstellen eines neuen Pakets, Hinzufügen und Konfigurieren von Komponenten Objekt um Objekt und Eigenschaft um Eigenschaft, Speichern und Ausführen des Pakets  
  
 Sie können das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell verwenden, um in einer beliebigen verwalteten Programmiersprache Code zu schreiben, mit dem Pakete erstellt, konfiguriert und ausgeführt werden. Möglicherweise möchten Sie metadatengesteuerte Pakete erstellen, die ihre Verbindungen oder Datenquellen, Transformationen und Ziele basierend auf der gewählten Datenquelle und ihren Tabellen und Spalten konfigurieren.  
  
 In diesem Abschnitt wird beschrieben und veranschaulicht, wie Pakete programmgesteuert Zeile um Zeile erstellt und konfiguriert werden. Als einfache Möglichkeit der Paketprogrammierung bietet es sich an, ein vorhandenes Paket ohne Änderungen zu laden und auszuführen. Dies wird unter [Programmgesteuerte Ausführung und Verwaltung von Paketen](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) beschrieben.  
  
 Eine etwas kompliziertere und hier nicht erläuterte Möglichkeit besteht darin, ein vorhandenes Paket als Vorlage zu laden, diese neu zu konfigurieren (beispielsweise für eine andere Datenquelle) und das Paket dann auszuführen. Anhand der Informationen in diesem Abschnitt können Sie auch die vorhandenen Objekte in einem Paket ändern.  
  
> [!NOTE]  
>  Wenn Sie ein bestehendes Paket als Vorlage verwenden und vorhandene Spalten im Datenfluss ändern, müssen Sie möglicherweise vorhandene Spalten entfernen und die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>-Methode der betroffenen Komponenten aufrufen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Programmgesteuertes Erstellen eines Pakets](../building-packages-programmatically/creating-a-package-programmatically.md)  
 Beschreibt, wie ein Paket programmgesteuert erstellt wird.  
  
 [Programmgesteuertes Hinzufügen von Tasks](../building-packages-programmatically/adding-tasks-programmatically.md)  
 Beschreibt, wie dem Paket Tasks hinzugefügt werden.  
  
 [Programmgesteuertes Verbinden von Tasks](../building-packages-programmatically/connecting-tasks-programmatically.md)  
 Beschreibt, wie die Ausführung von Containern und Tasks in einem Paket basierend auf dem Ergebnis der Ausführung eines vorhergehenden Tasks oder Containers gesteuert wird.  
  
 [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)  
 Beschreibt, wie Verbindungs-Manager zu einem Paket hinzugefügt werden.  
  
 [Programmgesteuertes Arbeiten mit Variablen](../building-packages-programmatically/working-with-variables-programmatically.md)  
 Beschreibt, wie Variablen während der Paketausführung hinzugefügt und verwendet werden.  
  
 [Programmgesteuerte Behandlung von Ereignissen](../building-packages-programmatically/handling-events-programmatically.md)  
 Beschreibt, wie Paket- und Taskereignisse behandelt werden.  
  
 [Programmgesteuertes Aktivieren der Protokollierung](../building-packages-programmatically/enabling-logging-programmatically.md)  
 Beschreibt, wie die Protokollierung für ein Paket oder einen Task aktiviert wird und wie benutzerdefinierte Filter auf Protokollereignisse angewendet werden.  
  
 [Programmgesteuertes Hinzufügen des Datenflusstasks](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
 Beschreibt, wie der Datenflusstask und seine Komponenten hinzugefügt und konfiguriert werden.  
  
 [Programmgesteuertes Auffinden von Datenflusskomponenten](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
 Beschreibt, wie die Komponenten, die auf dem lokalen Computer installiert sind, erkannt werden.  
  
 [Programmgesteuertes Hinzufügen von Datenflusskomponenten](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
 Beschreibt, wie eine Komponente zu einem Datenflusstask hinzugefügt wird.  
  
 [Programmgesteuertes Verbinden von Datenflusskomponenten](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
 Beschreibt, wie zwei Datenflusskomponenten verbunden werden.  
  
 [Programmgesteuertes Auswählen von Eingabespalten](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
 Beschreibt, wie aus den Eingabespalten, die einer Komponente von Upstreamkomponenten im Datenfluss bereitgestellt werden, Spalten ausgewählt werden.  
  
 [Programmgesteuertes Speichern von Paketen](../building-packages-programmatically/saving-a-package-programmatically.md)  
 Beschreibt, wie ein Paket programmgesteuert gespeichert wird.  
  
## <a name="reference"></a>Referenz  
 [Fehler- und Meldungsreferenz von Integration Services](../integration-services-error-and-message-reference.md)  
 Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Paketen mit Skripts](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Erläutert, wie die Ablaufsteuerung mithilfe des Skripttasks und der Datenfluss mithilfe der Skriptkomponente erweitert werden können.  
  
 [Erweitern von Paketen mit benutzerdefinierten Objekten](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Beschreibt, wie benutzerdefinierte Tasks, Datenflusskomponenten und andere Paketobjekte für die Verwendung in mehreren Paketen erstellt und programmiert werden.  
  
 [Programmgesteuerte Ausführung und Verwaltung von Paketen](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 Erläutert, wie Pakete und die Ordner, in denen sie gespeichert sind, aufgezählt, ausgeführt und verwaltet werden.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   CodePlex-Beispiele, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), auf www.codeplex.com/MSFTISProdSamples  
  
-   Blogeintrag [Leistungsprofilerstellung für benutzerdefinierte Erweiterungen](https://go.microsoft.com/fwlink/?LinkId=238831)auf blogs.msdn.com.  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
