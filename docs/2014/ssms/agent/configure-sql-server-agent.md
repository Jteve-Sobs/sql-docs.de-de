---
title: Konfigurieren des SQL Server-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0e7c8cb2230a7b6923514f0928b844f72c216d58
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796122"
---
# <a name="configure-sql-server-agent"></a>Konfigurieren des SQL Server-Agents
  In diesem Thema wird beschrieben, wie Sie einige Konfigurationsoptionen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent während der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angeben. Die vollständigen Konfigurationsoptionen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent sind nur in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) oder den gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verfügbar.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   [Sie konfigurieren Sie den SQL Server-Agent](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Klicken Sie im Objekt-Explorer von **auf** SQL Server-Agent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um Aufträge, Operatoren, Warnungen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst zu verwalten. Der Objekt-Explorer zeigt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Knoten jedoch nur dann an, wenn Sie die Berechtigung haben, ihn zu verwenden.  
  
-   Für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst sollte in Failoverclusterinstanzen kein automatischer Neustart aktiviert werden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienstkonten und Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>Sie konfigurieren Sie den SQL Server-Agent  
  
1.  Klicken Sie auf die Schaltfläche **Start** und anschließend im Menü **Start**  auf **Systemsteuerung**.  
  
2.  Klicken Sie in der Systemsteuerung unter **System und Sicherheit**auf **Verwaltung**, und wählen Sie dann **Lokale Sicherheitsrichtlinie**aus.  
  
3.  Klicken Sie in Lokale Sicherheitsrichtlinie auf das Chevron, um den Ordner **Sicherheitsrichtlinien** zu erweitern, und klicken Sie dann auf den Ordner **Zuweisen von Benutzerrechten** .  
  
4.  Klicken Sie mit der rechten Maustaste auf eine Berechtigung, die Sie zur Verwendung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfigurieren möchten, und wählen Sie **Eigenschaften**aus.  
  
5.  Überprüfen Sie im Eigenschaftendialogfeld der Berechtigung, ob das Konto aufgeführt ist, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird. Falls dies nicht der Fall ist, klicken Sie auf **Benutzer oder Gruppe hinzufügen**, geben Sie im Dialogfeld zum Auswählen von Benutzern, Computern, Dienstkonten oder Gruppen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**das Konto ein, unter dem der** -Agent ausgeführt wird, und klicken Sie dann auf **OK**.  
  
6.  Wiederholen Sie diese Schritte für jede Berechtigung, die Sie für die Ausführung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent hinzufügen möchten. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
