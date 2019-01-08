---
title: SQL Server-Verbindung für die Instanzerstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 778fd81b148f6fd7407d78d9ea04acd5bcf65e95
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801652"
---
# <a name="sql-server-connection-for-instance-creation"></a>SQL Server-Verbindung für die Instanzerstellung
  Einer der ersten Schritte beim Erstellen einer Oracle CDC-Instanz ist die Erstellung einer CDC-Datenbank auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz. Diese CDC-Datenbank wird für SQL Server CDC aktiviert, und für diese Aktivierung ist eine Anmeldung durch einen Benutzer erforderlich, der Mitglied der festen Serverrolle `sysadmin` ist.  
  
 Wenn ein Benutzer, der den Assistenten zum **Erstellen einer Oracle-CDC-Instanz** startet, kein Mitglied der festen Serverrolle `sysadmin` ist, wird das Dialogfeld **Verbindung mit SQL Server herstellen** geöffnet. Darin werden die Anmeldeinformationen für ein Mitglied der Rolle `sysadmin` angefordert, damit der Task zum Aktivieren der Datenbank für SQL Server CDC ausgeführt werden kann. Wenn die CDC-Datenbank erstellt wird, wird die `sysadmin` -Anmeldung verworfen, und der Vorgang wird mit der ursprünglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung fortgesetzt, die beim Zugreifen auf die Oracle Designer Console verwendet wurde.  
  
## <a name="task-list"></a>Aufgabenliste  
 Geben Sie im Dialogfeld **Verbindung mit SQL Server herstellen** die folgenden Informationen ein.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
 **Authentifizierung**  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, geben Sie die **Anmeldung** und **Kennwort** für den Benutzer in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt.  
  
 Der angemeldete Benutzer muss über eine Datenbankrolle verfügen, die den Zugriff auf die MSXCDCDB-Datenbank ermöglicht. Es wird empfohlen, dass der angemeldete Benutzer außerdem Zugriff auf weitere Datenbanken hat, die verwendet werden, da der Benutzer die Daten in diesen Datenbanken sonst nicht anzeigen kann.  
  
 **Optionen**  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
-   **Verbindungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange der CDC Service for Oracle auf eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] warten soll, bevor ein Timeout eintritt. Der Standardwert lautet **15**.  
  
-   **Timeout für berichtsausführung**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange der Oracle CDC-Windows-Dienst auf die Ausführung eines Befehls wartet, bis ein Timeout eintritt. Der Standardwert ist **30**.  
  
-   **Verbindung verschlüsseln**: Wählen Sie **Verbindung verschlüsseln** für die Kommunikation zwischen dem Oracle CDC Service und dem Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz über eine verschlüsselte Verbindung.  
  
-   **Erweitert**: Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
     Weitere Informationen zum Dialogfeld „Erweiterte Verbindungseigenschaften“ finden Sie unter [Erweiterte Verbindungseigenschaften](advanced-connection-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen der SQL Server-Änderungsdatenbank](create-the-sql-server-change-database.md)   
 [SQL Server-Verbindung erfordert Berechtigungen für den CDC Designer](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
