---
title: Übermitteln einer Momentaufnahme über FTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d1a8989492c9efb670b00bda00dbfa757c549fca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62960064"
---
# <a name="deliver-a-snapshot-through-ftp"></a>Übermitteln einer Momentaufnahme über FTP
  In diesem Thema wird beschrieben, wie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]eine Momentaufnahme über FTP bereitgestellt wird.  
  
##  <a name="Restrictions"></a> Einschränkungen  
  
-   Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\ftpserver\home\snapshots. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../security/secure-the-snapshot-folder.md).  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Zum Übertragen von Momentaufnahmedateien über FTP (File Transfer Protocol) müssen Sie zuerst einen FTP-Server konfigurieren. Weitere Informationen finden Sie in der Dokumentation zu den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internetinformationsdiensten (IIS).  
  
###  <a name="Security"></a> Sicherheit  
 Implementieren Sie ein virtuelles privates Netzwerk (VPN), wenn Sie FTP-Momentaufnahmeübermittlung über das Internet verwenden, um die Sicherheit zu verbessern. Weitere Informationen finden Sie unter [Veröffentlichen von Daten über das Internet mithilfe von VPN](../publish-data-over-the-internet-using-vpn.md).  
  
 Lassen Sie als bewährte Sicherheitsmethode keine anonymen Anmeldungen am FTP-Server zu. Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\ftpserver\home\snapshots. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../security/secure-the-snapshot-folder.md).  
  
 Die Benutzer sollten nach Möglichkeit während der Laufzeit zur Eingabe von Anmeldeinformationen aufgefordert werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden, müssen Sie sicherstellen, dass die Datei geschützt ist.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Geben Sie nach dem Konfigurieren des FTP-Servers im Dialogfeld **Veröffentlichungseigenschaften \<Veröffentlichung>** ein Verzeichnis und Sicherheitsinformationen für diesen Server an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-ftp-information"></a>So geben Sie FTP-Informationen an  
  
1.  Aktivieren Sie im Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** die Option **Abonnenten das Herunterladen von Momentaufnahmedateien über FTP (File Transfer Protocol) ermöglichen** auf einer der folgenden Seiten:   
    -   Der Seite **FTP-Momentaufnahme** , für Momentaufnahme- und Transaktionsveröffentlichungen und für Mergeveröffentlichungen bei Verlegern, auf denen niedrigere Versionen als [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ausgeführt werden.    
    -   Der Seite **FTP-Momentaufnahme und Internet** , für Mergeveröffentlichungen von Verlegern, auf denen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird.    
2.  Geben Sie Werte für **FTP-Servername**, **Portnummer**, **Pfad des FTP-Stammordners**, **Anmeldename**und **Kennwort**an.    
     Wenn beispielsweise der FTP-Stammordner \\\ftpserver\home lautet und Momentaufnahmen in \\\ftpserver\home\snapshots gespeichert werden sollen, geben Sie \snapshots\ftp für die Eigenschaft **Pfad des FTP-Stammordners** an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).    
3.  Geben Sie an, dass der Momentaufnahme-Agent die Momentaufnahmedateien in das in Schritt 2 angegebene Verzeichnis schreiben soll. Wenn der Momentaufnahme-Agent beispielsweise die Momentaufnahmedateien in das Verzeichnis \\\ftpserver\home\snapshots\ftp schreiben soll, müssen Sie den Pfad \\\ftpserver\home\snapshots an einer von zwei Stellen angeben:    
    -   Dem Standardspeicherort für Momentaufnahmen für den Verteiler, dem diese Veröffentlichung zugeordnet ist.    
         Weitere Informationen zum Angeben des standardmäßigen momentaufnahmespeicherorts finden Sie unter [angeben des standardmäßigen Momentaufnahmespeicherorts](../snapshot-options.md#snapshot-folder-locations).    
    -   Einem alternativen Speicherort für den Momentaufnahmeordner für diese Veröffentlichung. Ein alternativer Speicherort ist erforderlich, wenn die Momentaufnahme komprimiert wird.    
         Geben Sie den Pfad im Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** auf der Seite „Momentaufnahme“ in das Textfeld **Dateien im folgenden Ordner speichern** ein.   
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die Option, Momentaufnahmedateien auf einem FTP-Server verfügbar zu machen, und die entsprechenden FTP-Einstellungen können mithilfe gespeicherter Replikationsprozeduren programmgesteuert festgelegt und geändert werden. Welche Prozedur verwendet wird, hängt vom Typ der Veröffentlichung ab. FTP-Momentaufnahmeübermittlung wird nur bei Pullabonnements verwendet.  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>So aktivieren Sie die FTP-Momentaufnahmeübermittlung für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Geben Sie **@publication** , einen Wert von `true` für **@enabled_for_internet** , und entsprechende Werte für die folgenden Parameter:    
    -   **@ftp_address** &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.    
    -   (Optional) **@ftp_port** &ndash; der vom FTP-Server verwendete Port.    
    -   (Optional) **@ftp_subdirectory** &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses. Wenn beispielsweise der FTP-Stammordner \\\ftpserver\home lautet und Momentaufnahmen in \\\ftpserver\home\snapshots gespeichert werden sollen, geben Sie **\snapshots\ftp** für **@ftp_subdirectory** an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).    
    -   (Optional) **@ftp_login** &ndash; das Anmeldekonto, das beim Herstellen einer Verbindung mit dem FTP-Server verwendet wird.    
    -   (Optional) **@ftp_password** &ndash; das Kennwort für die FTP-Anmeldung.  
  
     Dadurch wird eine Veröffentlichung erstellt, die FTP verwendet. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>So aktivieren Sie die FTP-Momentaufnahmeübermittlung für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus. Geben Sie **@publication** , einen Wert von `true` für **@enabled_for_internet** und entsprechende Werte für die folgenden Parameter:  
  
    -   **@ftp_address** &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.    
    -   (Optional) **@ftp_port** &ndash; der vom FTP-Server verwendete Port.    
    -   (Optional) **@ftp_subdirectory** &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses. Wenn beispielsweise der FTP-Stammordner \\\ftpserver\home lautet und Momentaufnahmen in \\\ftpserver\home\snapshots gespeichert werden sollen, geben Sie **\snapshots\ftp** für **@ftp_subdirectory** an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).    
    -   (Optional) **@ftp_login** &ndash; das Anmeldekonto, das beim Herstellen einer Verbindung mit dem FTP-Server verwendet wird.    
    -   (Optional) **@ftp_password** &ndash; das Kennwort für die FTP-Anmeldung.  
  
     Dadurch wird eine Veröffentlichung erstellt, die FTP verwendet. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>So erstellen Sie ein Pullabonnement für eine Momentaufnahme- oder Transaktionsveröffentlichung, die FTP-Snapshotübermittlung verwendet  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)aus. Geben Sie **@publisher** und **@publication** eine Momentaufnahme über FTP bereitgestellt wird.  
  
    -   Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** , [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Anmeldeinformationen, unter denen Verteilungs-Agent auf dem Abonnenten ausgeführt wird, für **@job_login** und **@job_password** , und den Wert `true` für **@use_ftp** .  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) aus, um das Pullabonnement zu registrieren. Weitere Informationen finden Sie unter [Create a Pull Subscription](../create-a-pull-subscription.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>So erstellen Sie ein Pullabonnement für eine Mergeveröffentlichung, die FTP-Momentaufnahmeübermittlung verwendet  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)aus. Geben Sie **@publisher** und **@publication** eine Momentaufnahme über FTP bereitgestellt wird.   
2.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** , die unter dem der Verteilungs-Agent auf dem Abonnenten ausgeführt, für die wird Windows-Anmeldeinformationen **@job_login** und **@job_password** , und den Wert `true` für **@use_ftp** .    
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) aus, um das Pullabonnement zu registrieren. Weitere Informationen finden Sie unter [Create a Pull Subscription](../create-a-pull-subscription.md).  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>So ändern Sie eine oder mehrere Einstellungen der FTP-Momentaufnahmeübermittlung für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus. Geben Sie einen der folgenden Werte für **@property** und einen neuen Wert für diese Einstellung für **@value** an:    
    -   `ftp_address` &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.    
    -   `ftp_port` &ndash; der vom FTP-Server verwendete Port.    
    -   `ftp_subdirectory` &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses.    
    -   `ftp_login` &ndash; der Anmeldenamen, der zum Herstellen einer Verbindung mit dem FTP-Server verwendet wird.    
    -   `ftp_password` &ndash; das Kennwort für die FTP-Anmeldung.  
  
2.  (Optional) Wiederholen Sie Schritt 1 für jede zu ändernde FTP-Einstellung.    
3.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) aus, um die FTP-Momentaufnahmeübermittlung zu deaktivieren. Geben Sie den Wert `enabled_for_internet` für **@property** und den Wert `false` für **@value** .  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>So ändern Sie die Einstellungen der FTP-Momentaufnahmeübermittlung für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie einen der folgenden Werte für **@property** und einen neuen Wert für diese Einstellung für **@value** an:  
  
    -   `ftp_address` &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.    
    -   `ftp_port` &ndash; der vom FTP-Server verwendete Port.    
    -   `ftp_subdirectory` &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses.   
    -   `ftp_login` &ndash; der Anmeldenamen, der zum Herstellen einer Verbindung mit dem FTP-Server verwendet wird.    
    -   `ftp_password` &ndash; das Kennwort für die FTP-Anmeldung.    
2.  (Optional) Wiederholen Sie Schritt 1 für jede zu ändernde FTP-Einstellung.    
3.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) aus, um die FTP-Momentaufnahmeübermittlung zu deaktivieren. Geben Sie den Wert `enabled_for_internet` für **@property** und den Wert `false` für **@value** .  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Im folgenden Beispiel wird eine Mergeveröffentlichung erstellt, die Abonnenten ermöglicht, über FTP auf die Momentaufnahmedaten zuzugreifen. Beim Zugreifen auf die FTP-Freigabe sollte der Abonnent eine sichere VPN-Verbindung verwenden. **sqlcmd** -Skriptvariablen werden verwendet, um Anmelde- und Kennwortwerte anzugeben. Weitere Informationen finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubftp.sql#sp_createmergepub_ftp)]  
  
 Im folgenden Beispiel wird ein Abonnement für eine Mergeveröffentlichung erstellt, bei dem der Abonnent die Momentaufnahme über FTP abruft. Beim Zugreifen auf die FTP-Freigabe sollte der Abonnent eine sichere VPN-Verbindung verwenden. **sqlcmd** -Skriptvariablen werden verwendet, um Anmelde- und Kennwortwerte anzugeben. Weitere Informationen finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsub_ftp)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsubagent_ftp)]  
  
## <a name="see-also"></a>Siehe auch  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Übertragen von Momentaufnahmen über FTP](../transfer-snapshots-through-ftp.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../initialize-a-subscription-with-a-snapshot.md)  
  
  
