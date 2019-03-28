---
title: Konfigurieren der Serverkonfigurationsoption „Timeout für Remoteanmeldung“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3f2a3a0515674e5a6a5a9e4cb4788ddcf4a37da8
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530872"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Timeout für Remoteanmeldungen
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Timeout für Remoteanmeldung** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mit der Option **Timeout für Remoteanmeldung** können Sie den Zeitraum in Sekunden angeben, wie lange gewartet werden soll, bevor ein Remoteanmeldeversuch einen Fehler erzeugt. Wenn Sie z. B versuchen, sich an einem Remoteserver anzumelden, und dieser Server derzeit nicht betriebsbereit ist, wird durch **Timeout für Remoteanmeldung** sichergestellt, dass Sie nicht unbegrenzt warten müssen, bis der Computer seine Anmeldeversuche beendet. Der Standardwert für diese Option ist 10 Sekunden. Bei einem Wert von 0 ist eine unbegrenzte Wartezeit zulässig.  
  
> [!NOTE]  
>  Der Standardwert für diese Option in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ist 20 Sekunden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Timeout für Remoteanmeldung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option remote Login timeout](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Option **Timeout für Remoteanmeldung** wirkt sich auf Verbindungen mit OLE DB-Anbieter aus, die für heterogene Abfragen hergestellt wurden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a>So konfigurieren Sie die Option Timeout für Remoteanmeldung  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Wählen Sie unter **Netzwerk**einen Wert im Feld **Timeout für Remoteanmeldung** aus.  
  
     Sie können mithilfe der Option **Timeout für Remoteanmeldung** den Zeitraum in Sekunden angeben, wie lange gewartet werden soll, bevor für einen Remoteanmeldeversuch ein Fehler auftritt.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a>So konfigurieren Sie die Option Timeout für Remoteanmeldung  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `remote login timeout` auf `35` Sekunden festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option remote Login timeout  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
