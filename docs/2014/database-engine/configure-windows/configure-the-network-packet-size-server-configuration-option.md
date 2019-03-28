---
title: Konfigurieren der Serverkonfigurationsoption „Netzwerkpaketgröße“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4bd992f16158e7286db668256dc5963d83dbd4b8
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528262"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Netzwerkpaketgröße
  In diesem Thema wird beschrieben, wie so konfigurieren Sie die `network packet size` Serverkonfigurationsoption in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]. Die `network packet size` Option legt fest, die Paketgröße (in Byte), die im gesamten Netzwerk verwendet wird. Pakete sind die Datenabschnitte fester Größe, die Anforderungen und Ergebnisse zwischen Clients und Servern übertragen. Die Standardpaketgröße beträgt 4.096 Bytes.  
  
> [!NOTE]  
>  Sie sollten die Paketgröße nur dann ändern, wenn Sie sicher sind, dass die Leistung dadurch verbessert werden kann. Für die meisten Anwendungen empfiehlt sich die Standardpaketgröße.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Netzwerkpaketgröße mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option Netzwerkpaketgröße](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die maximale Netzwerkpaketgröße für verschlüsselte Verbindungen beträgt 16.383 Bytes.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Wenn eine Anwendung Massenkopiervorgänge ausführt oder große Mengen an Daten vom Typ text oder image sendet bzw. empfängt, kann eine über der Standardgröße liegende Paketgröße die Effizienz verbessern, da weniger Netzwerklesevorgänge und -schreibvorgänge ausgeführt werden. Sendet und empfängt eine Anwendung wenige Informationen, können Sie die Paketgröße auf 512 Bytes festlegen. Dies ist für die meisten Datenübertragungen ausreichend.  
  
-   Bei Systemen, die verschiedene Netzwerkprotokolle verwenden, sollten Sie die Option „Netzwerkpaketgröße“ auf die Größe festlegen, die das am häufigsten verwendete Protokoll vorgibt. Wenn Netzwerkprotokolle größere Pakete unterstützen, kann durch Netzwerkpaketgröße die Netzwerkleistung verbessert werden. Clientanwendungen können diesen Wert überschreiben.  
  
-   Sie können auch die Funktionen von OLE DB, ODBC (Open Database Connectivity) und der DB-Library aufrufen, um eine Änderung der Paketgröße anzufordern. Wenn der Server die angeforderte Paketgröße nicht unterstützt, sendet [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Warnmeldung an den Client. Unter gewissen Umständen führt das Ändern der Paketgröße möglicherweise zu einem Kommunikationsverbindungsfehler, wie beispielsweise:  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-network-packet-size-option"></a>So konfigurieren Sie die Option Netzwerkpaketgröße  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Wählen Sie unter **Netzwerk**einen Wert im Feld **Netzwerkpaketgröße** aus.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-network-packet-size-option"></a>So konfigurieren Sie die Option Netzwerkpaketgröße  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `network packet size` auf `6500` Byte festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option Netzwerkpaketgröße  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
