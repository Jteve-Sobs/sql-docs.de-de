---
title: Legen Sie einen SQL Server-Alias für den SQL Server-Agent-Dienst (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 752796caafa86ece1b471beb25a77ea381497409
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588598"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ein [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Alias für einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent festgelegt wird, der für das Herstellen einer Verbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)] verwendet wird. Standardmäßig stellt der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienst eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über Named Pipes mithilfe dynamischer Servernamen her, die keine zusätzliche Clientkonfiguration erfordern. Einen Serververbindungsalias müssen Sie nur konfigurieren, wenn Sie nicht den standardmäßigen Netzwerktransport verwenden oder wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] herstellen, die an einer alternativen Named Pipe lauscht.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   [So legen Sie einen SQL Server-Alias für den für den SQL Server-Agent-Dienst mithilfe von SQL Server Management Studio fest](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent wird nur dann ordnungsgemäß ausgeführt, wenn Sie einen Aliasnamen auswählen, der auf die lokale Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent-Dienstkonto finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienstkonten und Berechtigungen](configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>So legen Sie einen SQL Server-Alias für den SQL Server-Agent-Dienst fest  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] her, und erweitern Sie diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaften des SQL Server-Agents**_Servername_ unter **Seite auswählen**auf **Verbindung**, und  
  
4.  geben Sie im Feld **Aliasname für den lokalen Hostserver** den Alias des Servers ein, mit dem der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent verbunden werden soll.  
  
5.  Klicken Sie auf **OK**.  
  
  
