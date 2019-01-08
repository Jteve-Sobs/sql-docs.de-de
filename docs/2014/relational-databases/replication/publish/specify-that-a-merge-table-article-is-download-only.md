---
title: Angeben, dass ein neuer Mergetabellenartikel nur herunterladbar ist | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5594c811642225336586c8bce040f7f69724cadb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756192"
---
# <a name="specify-that-a-merge-table-article-is-download-only"></a>Angeben, dass ein neuer Mergetabellenartikel nur herunterladbar ist
  In diesem Thema wird beschrieben, wie angegeben wird, dass ein Mergetabellenartikel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]nur heruntergeladen werden kann. Nur herunterladbare Artikel sind für Anwendungen vorgesehen, deren Daten nicht auf den Abonnenten aktualisiert werden. Weitere Informationen finden Sie unter [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So geben Sie an, dass ein Mergetabellenartikel nur herunterladbar ist, mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie nach der Initialisierung von Abonnements angeben, dass ein Artikel nur herunterladbar sein soll, müssen sämtliche Clientabonnements, die den Artikel erhalten, erneut initialisiert werden. Serverabonnements müssen nicht erneut initialisiert werden. Weitere Informationen über die Auswirkungen von Eigenschaftsänderungen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Wenn Sie angeben möchten, dass ein Artikel nur herunterladbar sein soll, können Sie dies im Assistenten für neue Veröffentlichung auf der Seite **Artikel** oder auf der Registerkarte **Eigenschaften** des Dialogfelds **Artikeleigenschaften - \<Article>** tun. Dieses Dialogfeld ist im Assistenten für neue Veröffentlichung sowie über das Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-articles-page"></a>So geben Sie auf der Seite Artikel an, dass ein Artikel nur herunterladbar sein soll  
  
-   Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Artikel** eine Tabelle aus, und aktivieren Sie dann das Kontrollkästchen **Die durch die Hervorhebung markierte Tabelle ist nur herunterladbar**.  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-properties-tab-of-the-article-properties---article-dialog-box"></a>So geben Sie im Dialogfeld Artikeleigenschaften - auf der Registerkarte Eigenschaften an, dass ein \<Artikel> nur herunterladbar sein soll  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften – \<<Veröffentlichung>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.  
  
2.  Klicken Sie auf **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen** oder **Eigenschaften aller Tabellenartikel festlegen**.  
  
3.  Geben Sie im Abschnitt **Zielobjekt** der Registerkarte **Eigenschaften** des Dialogfelds **Artikeleigenschaften - \<Article>** einen der folgenden Werte für **Synchronisierungsrichtung** an:  
  
    -   **Nur herunterladbar auf Abonnenten, Abonnentenänderungen nicht zulassen**  
  
    -   **Nur herunterladbar auf Abonnenten, Abonnentenänderungen zulassen**  
  
4.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-specify-that-a-new-merge-table-article-is-download-only"></a>So geben Sie an, dass ein neuer Mergetabellenartikel nur herunterladbar ist  
  
1.  Führen Sie [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)unter Angabe des Werts **1** oder **2** für den Parameter **@subscriber_upload_options**nur heruntergeladen werden kann. Die Werte entsprechen dem folgenden Verhalten:  
  
    -   **0** &ndash; Keine Einschränkungen (Standard). Auf dem Abonnenten vorgenommene Änderungen werden auf den Verleger hochgeladen.  
  
    -   **1** &ndash; Änderungen sind auf dem Abonnenten zulässig, werden aber nicht auf den Verleger hochgeladen.  
  
    -   **2** &ndash; Änderungen sind auf dem Abonnenten nicht zulässig.  
  
        > [!NOTE]  
        >  Wenn die Quelltabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss für **@subscriber_upload_options** für beide Artikel der gleiche Wert angegeben werden.  
  
#### <a name="to-modify-an-existing-merge-table-article-to-be-download-only"></a>So ändern Sie einen vorhandenen Mergetabellenartikel dahingehend, dass er nur herunterladbar ist  
  
1.  Um zu ermitteln, ob ein Artikel nur herunterladbar ist, führen Sie [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)aus. Beachten Sie im Resultset den Wert von **upload_options** für den Artikel.  
  
2.  Wenn in Schritt 1 der Wert **0**zurückgegeben wird, führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)unter Angabe des Werts **subscriber_upload_options** für **@property**, des Werts **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**sowie des Werts **1** oder **2** für **@value**aus, was folgendem Verhalten entspricht:  
  
    -   **1** &ndash; Änderungen sind auf dem Abonnenten zulässig, werden aber nicht auf den Verleger hochgeladen.  
  
    -   **2** &ndash; Änderungen sind auf dem Abonnenten nicht zulässig.  
  
        > [!NOTE]  
        >  Wenn die Quelltabelle eines Artikels bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss das Verhalten nur herunterladbarer Artikel gleich sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](define-an-article.md)   
 [Anzeigen und Ändern von Artikeleigenschaften](view-and-modify-article-properties.md)  
  
  
