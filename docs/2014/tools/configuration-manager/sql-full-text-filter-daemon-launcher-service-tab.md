---
title: Startprogramm für SQL-Volltextfilterdaemon (Registerkarte „Dienst“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f5129771e5d487075ad2223317047fbbb3c09fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211161"
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a>Startprogramm für SQL-Volltextfilterdaemon (Registerkarte Dienst)
  Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]wird der FDHOST (SQL-Volltextfilterdaemon)-Startprogrammdienst vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Volltext verwendet. Dieser Dienst muss ausgeführt werden, wenn Sie die Volltextsuche verwenden. Informationen über die Prozesse des Filterdaemonhosts finden Sie unter "Architektur der Volltextsuche" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 Verwenden Sie im Startprogramm für SQL-Volltextfilterdaemon die Registerkarte **Dienst**im Dialogfeld **Eigenschaften des SQL Full-text Filter Daemon-Programmstarters** (SQL-Volltextfilterdaemon-LauncherProperties), um die folgenden Optionen anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
 **Binärer Pfad**  
 Führt den Speicherort der Programmdateien auf, die von diesem Dienst verwendet werden.  
  
 **Fehler Steuerung**  
 1 steht für `SERVICE_ERROR_NORMAL`. Wenn der Dienst nicht zusammen mit dem Computer gestartet werden kann, wird der Fehler vom Startprogramm protokolliert und eine Popupmeldung angezeigt, der Startvorgang aber fortgesetzt. Dieser Wert kann nicht geändert werden.  
  
 **Exitcode**  
 Bei einem Fehler wird die dazu gehörende Nummer in diesem Feld angezeigt. Verwenden Sie diese Nummer für die Problembehandlung. Stellen Sie die Fehlernummer dem technischen Support zur Verfügung, oder durchsuchen Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.  
  
 **Hostname**  
 Zeigt den Namen des Computers oder Clusters an, auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem der-Dienst ausgeführt wird.  
  
 **Name**  
 Zeigt den Anzeigenamen des Dienstes an.  
  
 **Prozess-ID**  
 Zeigt die Prozess-ID von Windows an.  
  
 **SQL-Diensttyp**  
 Zeigt den für aufrufende Prozesse bereitgestellten Diensttyp an. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mehrere Dienste installiert.  
  
 **Start Modus**  
 Richten Sie den Dienst mit den folgenden Auswahlmöglichkeiten ein:  
  
-   Manuell: Dieser Dienst wird nicht automatisch zusammen mit dem Computer gestartet. Zum Starten des Dienstes verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder ein anderes Tool.  
  
-   Automatisch: Dieser Dienst wird zusammen mit dem Computer gestartet.  
  
-   Deaktiviert: Dieser Dienst kann nicht gestartet werden.  
  
 **State**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist. „**…**“ gibt einen ausstehenden Statuswechsel an.  
  
  
