---
title: Verwalten von DQS-Protokolldateien
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 3e3de142823ebe0749e350c93b4891e20838ad5d
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85808782"
---
# <a name="manage-dqs-log-files"></a>Verwalten von DQS-Protokolldateien

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)-Protokolldateien unterstützen Sie bei der Diagnose und bei der Problembehandlung mit den Komponenten [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]und [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Für [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]und die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]werden separate Protokolldateien generiert.  
  
 Sie können die Einstellung des Protokollschweregrads für [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Funktionen und -Module mithilfe von [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] konfigurieren. Darüber hinaus können Sie auch andere (erweiterte) Einstellungen für die DQS-Protokolldateien konfigurieren, indem Sie die Einstellungen für die DQS-Protokollkonfiguration in der DQS_MAIN-Datenbank und in einer XML-Datei auf dem [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Computer manuell ändern.  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a>Data Quality Server-Protokolldatei  
 Die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei, DQServerLog.DQS_MAIN.log, enthält Protokolle der Aktivitäten, die in [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]ausgeführt werden. Wenn Sie die Standardinstanz von SQL Server installiert haben, ist die Protokolldatei DQServerLog.DQS_MAIN.log unter C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log verfügbar. Die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei enthält die folgenden Informationen, die jeweils durch ein Pipezeichen (|) begrenzt sind:  
  
-   Datum und Uhrzeit  
  
-   Threadname  
  
-   Thread-ID  
  
-   Protokollschweregrad (FATAL, ERROR, WARN, INFO und DEBUG)  
  
    > [!NOTE]  
    >  Der DEBUG-Protokollierungsschweregrad entspricht der Option Ausführlich.  
  
-   UID (interne DQS-Infrastruktur-ID)  
  
-   Namespace  
  
-   Klasse und Methode  
  
-   `Message`  
  
 Neben diesen Informationen werden in der Protokolldatei auch Informationen zur Anwendungsversion, zum Computernamen, Benutzernamen und Betriebssystem angezeigt.  
  
 Ein Beispieleintrag in der [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei sieht wie folgt aus:  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 Die Datei DQServerLog.DQS_MAIN.log [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ist eine Rolldatei. Eine neue Protokolldatei wird erstellt, sobald die vorhandene Protokolldatei die maximale Rolldateigröße überschreitet, die in den Konfigurationseinstellungen des -Protokolls angegeben ist. Weitere Informationen finden Sie unter [Configure Advanced Settings for DQS Log Files](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a>Data Quality-Client Protokolldatei  
 Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei, DQClientLog.log, enthält die clientseitigen Protokolle. Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei ist unter %APPDATA%\SSDQS\Log verfügbar. Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei enthält ähnliche Informationen wie die Serverprotokolldatei, jedoch auf Clientseite.  
  
 Wie die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei ist auch die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei eine Rolldatei, und eine neue Protokolldatei wird erstellt, sobald die vorhandene Protokolldatei die maximale Rolldateigröße überschreitet, die in den Konfigurationseinstellungen des [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolls angegeben ist. Weitere Informationen finden Sie unter [Configure Advanced Settings for DQS Log Files](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a>Protokolldatei der DQS-Bereinigungs Komponente  
 Die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] -Protokolldatei, DQSSSISLog.log, enthält Protokolle der Aktivitäten, die mithilfe der [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]ausgeführt werden. Die Protokolldatei der Komponente [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] ist unter %APPDATA%\SSDQS\Log verfügbar. Die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] -Protokolldatei enthält ähnliche Informationen wie die Serverprotokolldatei, jedoch für die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
##  <a name="related-tasks"></a><a name="RT"></a> Verwandte Aufgaben  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die Einstellungen des Protokollschweregrads für DQS-Protokolldateien mit [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]konfiguriert werden.|[Konfigurieren von Schweregraden für DQS-Protokolldateien](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Beschreibt, wie die erweiterten Einstellungen für DQS-Protokolldateien manuell konfiguriert werden.|[Konfigurieren der erweiterten Einstellungen für DQS-Protokolldateien](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [DQS-Administration](../data-quality-services/dqs-administration.md)  
  
  
