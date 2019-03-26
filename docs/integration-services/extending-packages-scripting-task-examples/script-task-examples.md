---
title: Skripttask-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 61aabb951b05da511ccea7315ed7f4bddbecb4e1
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58279604"
---
# <a name="script-task-examples"></a>Skripttask-Beispiele
  Bei Skripttask handelt es sich um ein Mehrzwecktool, das Sie in einem Paket verwenden können, um nahezu alle Anforderungen zu erfüllen, die von den Tasks nicht erfüllt werden, die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthalten sind. In diesem Thema werden Skripttaskcodebeispiele aufgeführt, in denen einige der verfügbaren Funktionen veranschaulicht werden.  
  
> [!NOTE]  
>  Wenn Sie Tasks erstellen möchten, die Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesen Skripttaskbeispielen als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
### <a name="example-topics"></a>Beispielthemen  
 Dieser Abschnitt enthält Codebeispiele, die verschiedene Einsatzbereiche der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klassen veranschaulichen, die Sie in einen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Skripttask integrieren können:  
  
 [Erkennen einer leeren flachen Datei mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 Überprüft eine Flatfile auf vorhandene Datenzeilen, und speichert das Ergebnis in einer Variablen zur Verzweigung der Ablaufsteuerung.  
  
 [Erfassen einer Liste für die ForEach-Schleife mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 Erstellt eine Liste mit Dateien, die benutzerspezifische Kriterien erfüllen, und füllt eine Variable für den späteren Gebrauch durch den Foreach from-Variablenenumerator.  
  
 [Abfragen des Active Directory mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 Ruft Benutzerinformationen von Active Directory basierend auf dem Wert einer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Variable ab, indem im System.DirectoryServices-Namespace Klassen verwendet werden.  
  
 [Überwachen von Leistungsindikatoren mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 Erstellt einen benutzerdefinierten Leistungsindikator, mit dem der Ausführungsfortschritt eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets überprüft werden kann, indem im System.Diagnostics-Namespace Klassen verwendet werden.  
  
 [Arbeiten mit Bildern mithilfe des Skripttasks](../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 Komprimiert Bilder in das JPEG-Format und erstellt aus ihnen Miniaturbilder, indem im System.Drawing-Namespace Klassen verwendet werden.  
  
 [Suchen installierter Drucker mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 Sucht installierte Drucker, die ein bestimmtes Papierformat unterstützen, indem im System.Drawing.Printing-Namespace Klassen verwendet werden.  
  
 [Senden einer HTML-E-Mail mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 Sendet eine Mail-Nachricht im HTML-Format anstatt im Nur-Text-Format.  
  
 [Arbeiten mit Excel-Dateien mit dem Skripttask](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Listet die Arbeitsblätter in einer Excel-Datei auf und überprüft das Vorhandensein eines bestimmten Arbeitsblatts.  
  
 [Senden mit dem Skripttask an eine private Remotemeldungswarteschlange](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 Sendet eine Meldung an eine private Remotenachrichten-Warteschlange.  
  
### <a name="other-examples"></a>Andere Beispiele:  
 Die folgenden Themen enthalten ebenfalls Codebeispiele, die mit dem Skripttask verwendet werden können:  
  
 [Verwenden von Variablen im Skripttask](../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Fordert vom Benutzer eine Bestätigung an, ob das Paket weiterhin ausgeführt werden soll, basierend auf dem Wert einer Paketvariablen, der die in einer anderen Variablen festgelegte Begrenzung überschreiten kann.  
  
 [Herstellen einer Verbindung zu Datenquellen im Skripttask](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Ruft eine Verbindung oder Verbindungsinformationen von Verbindungs-Managern ab, die im Paket definiert sind.  
  
 [Auslösen von Ereignissen im Skripttask](../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Gibt einen Fehler, eine Warnung oder eine Meldung basierend auf dem Status der Internetverbindung auf dem Server aus.  
  
 [Protokollieren im Skripttask](../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Protokolliert die Anzahl der Elemente, die vom Task zu aktivierten Protokollanbietern verarbeitet wird.  
  
  
