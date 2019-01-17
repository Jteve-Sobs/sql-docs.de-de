---
title: Hilfe zu SQL Server-Konfigurations-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/01/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 34942a33e71c2d9f17f77a9f595cf873d71fbc4e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204719"
---
# <a name="sql-server-configuration-manager-help"></a>Hilfe zu SQL Server-Konfigurations-Manager
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager zum Konfigurieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten und Netzwerkkonnektivität. Zum Erstellen und Verwalten von Datenbankobjekten, dem Konfigurieren der Sicherheit und dem Erstellen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Weitere Informationen über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  

 > [!TIP]
 > Wenn Sie konfigurieren müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Linux verwenden die **Mssql-Conf** Tool. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](../../linux/sql-server-linux-configure-mssql-conf.md).

 Dieser Abschnitt enthält die F1-Hilfethemen für die Dialogfelder in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Mit dem Konfigurations-Manager können keine Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]konfiguriert werden.  
  
## <a name="services"></a>Dienste  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager werden Dienste im Zusammenhang mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Obwohl viele dieser Aufgaben mithilfe des Dialogfensters Windows-Dienst von [!INCLUDE[msCoName](../../includes/msconame-md.md)] abgeschlossen werden können, ist der folgende Hinweis wichtig: Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager werden zusätzliche Vorgänge auf den Diensten ausgeführt, die vom Konfigurations-Manager verwaltet werden, beispielsweise das Anwenden der zutreffenden Berechtigungen beim Ändern des Dienstkontos. Das Verwenden des normalen Dialogfensters Windows-Dienste zum Konfigurieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten kann unter Umständen zu Fehlfunktionen des Diensts führen.  
  
 Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager für die folgenden Aufgaben für Dienste:  
  
-   Starten, Beenden und Anhalten von Diensten  
  
-   Konfigurieren von Diensten zum automatischen oder manuellen Starten, Deaktivieren der Dienste oder Ändern anderer Diensteinstellungen  
  
-   Ändern der Kennwörter für die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten verwendeten Konten  
  
-   Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Ablaufverfolgungsflags (Befehlszeilenparameter)  
  
-   Anzeigen der Eigenschaften von Diensten  
  
## <a name="sql-server-network-configuration"></a>SQL Server-Netzwerkkonfiguration  
 Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager für die folgenden Aufgaben im Zusammenhang mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten auf diesem Computer:  
  
-   Aktivieren oder Deaktivieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Netzwerkprotokolls  
  
-   Konfigurieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Netzwerkprotokolls  
  
> [!NOTE]  
>  Ein kurzes Tutorial zum Konfigurieren von Protokollen und zum Herstellen einer Verbindung mit [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] finden Sie unter [Tutorial: Erste Schritte mit der Datenbank-Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
## <a name="sql-server-native-client-configuration"></a>SQL Server Native Client-Konfiguration  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients werden Verbindungen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Netzwerkbibliothek hergestellt. Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager für die folgenden Aufgaben im Zusammenhang mit Clientanwendungen auf diesem Computer:  
  
-   Geben Sie bei der Verbindungsherstellung zu Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Protokollreihenfolge für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clientanwendungen auf diesem Computer an.  
  
-   Konfigurieren Sie Clientverbindungsprotokolle.  
  
-   Erstellen Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clientanwendungen Aliase für Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sodass von Clients mithilfe einer benutzerdefinierten Verbindungszeichenfolge eine Verbindung hergestellt werden kann.  
  
 Weitere Informationen zu jeder dieser Aufgaben finden Sie in der F1-Hilfe.  
  
#### <a name="to-open-sql-server-configuration-manager"></a>So öffnen Sie SQL Server-Konfigurations-Manager  
  
-   Klicken Sie auf **Start** , zeigen Sie auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server** (Version), zeigen Sie auf **Konfigurationstools**, und klicken Sie anschließend auf **SQL Server-Konfigurations-Manager**.  
  
  
 **So greifen Sie unter [!INCLUDE[win8](../../includes/win8-md.md)]** auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager zu  
  
 Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager bei Verwendung von [!INCLUDE[win8](../../includes/win8-md.md)]nicht als Anwendung angezeigt. Geben Sie **SQLServerManager12.msc** (für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) oder **SQLServerManager11.msc** (für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) ein, und drücken Sie anschließend die **EINGABETASTE**, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager im Charm **Suchen** unter **Apps** zu öffnen.  
  

## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Dienste](../../tools/configuration-manager/sql-server-services.md)   
 [SQL Server-Netzwerkkonfiguration](../../tools/configuration-manager/sql-server-network-configuration.md)   
 [SQL Native Client 11.0-Konfiguration](../../tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Auswählen eines Netzwerkprotokolls](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
