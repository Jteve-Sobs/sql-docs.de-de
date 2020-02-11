---
title: Starten von SQL Server im Einzelbenutzermodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 245ae929b9a267f06b675b9380760f3db6067d1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809054"
---
# <a name="start-sql-server-in-single-user-mode"></a>Starten von SQL Server im Einzelbenutzermodus
  Unter bestimmten Umständen müssen Sie möglicherweise eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Startoption **-m**im Einzelbenutzermodus starten. Dies ist z. B. der Fall, wenn Sie Serverkonfigurationsoptionen ändern oder eine beschädigte master-Datenbank oder andere Systemdatenbanken wiederherstellen möchten. Beide Aktionen erfordern das Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus zu starten, ermöglicht einem beliebigen Mitglied der lokalen Administratorengruppe des Computers, eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Mitglied der festen Serverrolle "sysadmin" herzustellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind](connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Beachten Sie beim Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus Folgendes:  
  
-   Nur ein einziger Benutzer kann die Verbindung mit dem Server herstellen.  
  
-   Der CHECKPOINT-Prozess wird nicht ausgeführt. Standardmäßig wird dieser Prozess beim Starten automatisch ausgeführt.  
  
> [!NOTE]  
>  Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst, bevor Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus herstellen, da andernfalls der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst diese Verbindung verwendet und somit blockiert.  
  
 Wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten, kann [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen. Der Objekt-Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] erzeugt möglicherweise einen Fehler, da einige Vorgänge mehr als eine Verbindung erfordern. Um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus zu verwalten, führen Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen aus, indem Sie nur durch den Abfrage-Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung herstellen oder das [Hilfsprogramm sqlcmd](../../tools/sqlcmd-utility.md)verwenden.  
  
 Wenn Sie die Option **-m** mit **sqlcmd** oder [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]verwenden, können Sie die Verbindungen auf eine angegebene Clientanwendung beschränken. 
  **-m"sqlcmd"** beschränkt Verbindungen z.B. auf eine einzelne Verbindung, und diese Verbindung muss sich als **sqlcmd** -Clientprogramm identifizieren. Verwenden Sie diese Option, wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten und eine unbekannte Clientanwendung die einzige verfügbare Verbindung belegt. Um die Verbindung über den Abfrage-Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]herzustellen, verwenden Sie **-m"Microsoft SQL Server Management Studio - Query"**.  
  
> [!IMPORTANT]  
>  Verwenden Sie diese Option nicht als Sicherheitsfunktion. Die Clientanwendung gibt den Clientanwendungsnamen an und kann als Teil der Verbindungszeichenfolge einen falschen Namen angeben.  
  
## <a name="note-for-clustered-installations"></a>Hinweis für gruppierte Installationen  
 Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation in einer Clusterumgebung verwendet die Clusterressourcen-DLL, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus gestartet wird, die verfügbare Verbindung, wodurch alle anderen Verbindungen mit dem Server blockiert werden. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diesen Status aufweist, wenn Sie versuchen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Ressource online zu schalten, wird möglicherweise ein Failover für die SQL-Ressource auf einen anderen Knoten ausgeführt, wenn die Ressource so konfiguriert ist, dass sie sich auf die Gruppe auswirkt.  
  
 Gehen Sie folgendermaßen vor, um das Problem zu verhindern:  
  
1.  Entfernen Sie den -m-Startparameter aus den erweiterten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Eigenschaften.  
  
2.  Schalten Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource offline.  
  
3.  Geben Sie aus dem aktuellen Benutzerknoten dieser Gruppe den folgenden Befehl an der Eingabeaufforderung aus:  
    net start MSSQLSERVER /m.  
  
4.  Überprüfen Sie in Konsole der Clusterverwaltung oder der Failoverclusterverwaltung, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource immer noch offline ist.  
  
5.  Stellen Sie nun unter Verwendung des folgenden Befehls eine Verbindung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, und führen Sie den erforderlichen Vorgang aus: SQLCMD -E -S\<servername>.  
  
6.  Schließen Sie die Eingabeaufforderung, nachdem der Vorgang abgeschlossen wurde, und schalten Sie die SQL-Ressource sowie andere Ressourcen über die Clusterverwaltung wieder online.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, anhalten oder Anhalten des SQL Server-Agent Dienstanbieter](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Diagnoseverbindung für Datenbankadministratoren](diagnostic-connection-for-database-administrators.md)   
 [sqlcmd-Hilfsprogramm](../../tools/sqlcmd-utility.md)   
 [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md)  
  
  
