---
title: Formatieren von Pageradressen für Warnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 535ae5f92fea0222468ed64f567154495e329a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044200"
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
  In diesem Thema wird beschrieben, wie Pager- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Adressen für- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Agent- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Warnungen [!INCLUDE[tsql](../../includes/tsql-md.md)]in mithilfe von oder formatiert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So formatieren Sie Pager-Adressen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** Information über eine Warnung anzeigen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>So formatieren Sie Pageradressen  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der die Warnung enthält, die Sie an einen Pager senden möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Wählen Sie unter **Seite auswählen**die Option **Warnungssystem**aus.  
  
4.  Geben Sie in die Felder **An-Zeile** und **Cc-Zeile** des Felds **Adressformatierung für Pager-E-Mails:** das Präfix oder das Suffix der Pageradresse ein. Die eigentliche Pageradresse des Operators wird beim Senden einer Benachrichtigung eingefügt.  
  
5.  Geben Sie in das Feld **Betreff** das Präfix oder Suffix der Betreffzeile ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Nachrichtenbereich der E-Mail in Benachrichtigungsseite aufnehmen** , um die vollständige E-Mail-Nachricht in die Pagernachricht einzuschließen (statt lediglich die Betreffzeile).  
  
7.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
