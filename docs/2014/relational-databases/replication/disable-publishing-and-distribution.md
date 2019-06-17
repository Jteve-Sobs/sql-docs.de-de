---
title: Deaktivieren der Veröffentlichung und Verteilung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46cdf7ad91de4eacae513399dc7b0c88ad9831fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721450"
---
# <a name="disable-publishing-and-distribution"></a>Deaktivieren der Veröffentlichung und Verteilung
  In diesem Thema wird beschrieben, wie die Veröffentlichung und die Verteilung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) deaktiviert werden.  
  
 Sie können folgendermaßen vorgehen:  
  
-   Löschen aller Verteilungsdatenbanken auf dem Verteiler.  
  
-   Deaktivieren aller Verleger, die den Verteiler verwenden, und Löschen aller Veröffentlichungen auf diesen Verlegern.  
  
-   Löschen aller Abonnements für die Veröffentlichungen. Daten in den Veröffentlichungs- und Abonnementdatenbanken werden nicht gelöscht. Allerdings geht die Synchronisierungsbeziehung zu allen Veröffentlichungsdatenbanken verloren. Falls Sie die Daten auf dem Abonnenten löschen möchten, müssen Sie diese manuell löschen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
-   **So deaktivieren Sie die Veröffentlichung und Verteilung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Zum Deaktivieren der Veröffentlichung und Verteilung müssen sämtliche Verteilungs- und Veröffentlichungsdatenbanken online sein. Wenn für Verteilungs- oder Veröffentlichungsdatenbanken *Datenbankmomentaufnahmen* vorhanden sind, müssen diese gelöscht werden, bevor die Veröffentlichung und Verteilung deaktiviert werden kann. Eine Datenbankenmomentaufnahme ist eine schreibgeschützte Offlinekopie einer Datenbank, die in keinem Bezug zu einer Replikationsmomentaufnahme steht. Weitere Informationen finden Sie unter [Datenbankmomentaufnahmen &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Sie können die Veröffentlichung und die Verteilung mithilfe des Veröffentlichungs- und Verteilungsdeaktivierungs-Assistenten deaktivieren.  
  
#### <a name="to-disable-publishing-and-distribution"></a>So deaktivieren Sie die Veröffentlichung und Verteilung  
  
1.  Stellen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger oder Verteiler her, den Sie deaktivieren möchten, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** , und klicken Sie dann auf **Veröffentlichung und Verteilung deaktivieren**.  
  
3.  Führen Sie die Schritte des Veröffentlichungs- und Verteilungsdeaktivierungs-Assistenten vollständig aus.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die Veröffentlichung und die Verteilung können mit gespeicherten Replikationsprozeduren programmgesteuert deaktiviert werden.  
  
#### <a name="to-disable-publishing-and-distribution"></a>So deaktivieren Sie die Veröffentlichung und Verteilung  
  
1.  Beenden Sie alle replikationsbezogenen Aufträge. Eine Auflistung der Auftragsnamen finden Sie im Abschnitt "Agentsicherheit mit SQL Server-Agent" unter [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md).  
  
2.  Führen Sie für jeden Abonnenten der Abonnementdatenbank [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) aus, um Replikationsobjekte aus der Datenbank zu entfernen. Diese gespeicherte Prozedur entfernt keine Replikationsaufträge vom Verteiler.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) aus, um Replikationsobjekte aus der Datenbank zu entfernen.  
  
4.  Wenn der Verleger einen Remoteverteiler verwendet, führen Sie [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)aus.  
  
5.  Führen Sie auf dem Verteiler [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)aus. Diese gespeicherte Prozedur sollte für jeden auf dem Verteiler registrierten Verleger einmal ausgeführt werden.  
  
6.  Führen Sie auf dem Verteiler [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) aus, um die Verteilerdatenbank zu löschen. Diese gespeicherte Prozedur sollte für jede Verteilungsdatenbank auf dem Verteiler einmal ausgeführt werden. Dadurch werden außerdem alle der Verteilungsdatenbank zugeordnete Warteschlangenlese-Agentaufträge entfernt.  
  
7.  Führen Sie auf dem Verteiler [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) aus, um die Verteilerbezeichnung vom Server zu entfernen.  
  
    > [!NOTE]  
    >  Wenn nicht alle Replikationsveröffentlichungs- und Verteilungsobjekte gelöscht wurden, bevor Sie [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) und [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)ausführen, geben diese Prozeduren einen Fehler zurück. Damit alle replikationsbezogenen Objekte gelöscht werden, wenn ein Verleger oder ein Verteiler gelöscht wird, muss der **@no_checks** -Parameter auf **1**. Wenn ein Verleger oder Verteiler offline oder nicht erreichbar ist, kann der **@ignore_distributor** -Parameter auf **1** festgelegt werden, damit der Verleger/Verteiler gelöscht werden kann: Jedoch müssen verbleibende Veröffentlichungs- und Verteilungsobjekte manuell entfernt werden.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Dieses Beispielskript entfernt Replikationsobjekte aus der Abonnementdatenbank.  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 Dieses Beispielskript deaktiviert die Veröffentlichung und die Verteilung auf einem Server, der ein Verleger und Verteiler ist, und löscht die Verteilungsdatenbank.  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
#### <a name="to-disable-publishing-and-distribution"></a>So deaktivieren Sie die Veröffentlichung und Verteilung  
  
1.  Entfernen Sie alle Abonnements von Veröffentlichungen, für die der Verteiler verwendet wird. Weitere Informationen finden Sie unter [Delete a Pull Subscription](delete-a-pull-subscription.md) und [Delete a Push Subscription](delete-a-push-subscription.md).  
  
2.  Entfernen Sie alle Veröffentlichungen, für die der Verteiler verwendet wird, und deaktivieren Sie die Veröffentlichung für alle Datenbanken, wenn sich Verleger und Verteiler auf dem gleichen Server befinden. Weitere Informationen finden Sie unter [Delete a Publication](publish/delete-a-publication.md).  
  
3.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
4.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.DistributionPublisher> -Klasse. Geben Sie die <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> -Eigenschaft an, und übergeben Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 3.  
  
5.  (Optional) Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen und zu verifizieren, dass der Verleger vorhanden ist. Wenn diese Methode `false` zurückgibt, war der in Schritt 4 festgelegte Verlegername falsch, oder der Verleger wird von diesem Verteiler nicht verwendet.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A>-Methode auf. Übergeben Sie den Wert `true` für *erzwingen* dem Verleger und Verteiler auf verschiedenen Servern sind und, wenn der Verleger auf dem Verteiler ohne vorherige Überprüfung deinstalliert werden soll, die Veröffentlichungen auf nicht mehr vorhanden sind die Herausgeber.  
  
7.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer> -Klasse. Übergeben Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 3.  
  
8.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A>-Methode auf. Übergeben Sie den Wert `true` für *erzwingen* entfernt alle Replikationsobjekte auf dem Verteiler ohne vorherige Überprüfung, die lokalen Veröffentlichungsdatenbanken deaktiviert und Verteilungsdatenbanken deinstalliert wurden.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel werden die Verlegerregistrierung auf dem Verteiler entfernt, die Verteilungsdatenbank gelöscht und der Verteiler deinstalliert.  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 In diesem Beispiel wird der Verteiler deinstalliert, ohne dass zuvor die lokalen Veröffentlichungsdatenbanken deaktiviert oder die Verteilungsdatenbank gelöscht wurde.  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a>Siehe auch  
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Konzepte für gespeicherte Systemprozeduren für die Replikation](concepts/replication-system-stored-procedures-concepts.md)  
  
  
