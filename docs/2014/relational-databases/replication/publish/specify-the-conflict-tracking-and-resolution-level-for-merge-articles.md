---
title: Angeben der Konfliktnachverfolgungs- und -lösungsebene für Mergeartikel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], levels
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3ff61c601be83ac27c4febb7f31598bdb8fce037
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52810272"
---
# <a name="specify-the-conflict-tracking-and-resolution-level-for-merge-articles"></a>Angeben der Konfliktnachverfolgungs- und -lösungsebene für Mergeartikel
  In diesem Thema wird beschrieben, wie die Konfliktnachverfolgung und die Auflösungsebene für Mergeartikel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]angegeben werden.  
  
 Wenn ein Abonnement für eine Mergeveröffentlichung synchronisiert wird, prüft die Replikation auf Konflikte, die sich ergeben, wenn der Verleger und der Abonnent die gleichen Daten ändern. Sie können angeben, ob Konflikte auf Zeilenebene erkannt werden, wobei jede Änderung in der Zeile als Konflikt eingestuft wird, oder auf Spaltenebene, wobei nur die Änderungen in derselben Spalte und derselben Zeile als Konflikte eingestuft werden. Die Konfliktlösung für Artikel wird auf Zeilenebene ausgeführt. Weitere Informationen zur Konflikterkennung und -lösung bei logischen Datensätzen finden Sie unter [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So geben Sie die Konfliktnachverfolgungs- und -lösungsebene für Mergeartikel an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie die Nachverfolgungsebene nach dem Initialisieren von Abonnements ändern, müssen diese Abonnements erneut initialisiert werden. Weitere Informationen über die Auswirkungen von Eigenschaftsänderungen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
-   Bei der Nachverfolgung auf Zeilen- oder Spaltenebene erfolgt die Konfliktlösung immer auf Zeilenebene: die gewinnende Zeile überschreibt die verlierende Zeile. Bei der Mergereplikation können Sie auch angeben, dass Konflikte auf der Ebene logischer Datensätze nachverfolgt und gelöst werden. Diese Optionen sind in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]jedoch nicht verfügbar. Informationen zum Festlegen dieser Optionen über gespeicherte Replikationsprozeduren finden Sie unter [Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Geben Sie die Nachverfolgung auf Zeilen- oder Spaltenebene für Mergeartikel im Dialogfeld **Artikeleigenschaften** auf der Registerkarte **Eigenschaften** an. Dieses Dialogfeld ist im Assistenten für neue Veröffentlichung und im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-row--or-column-level-tracking"></a>So geben Sie die Nachverfolgung auf Zeilen- oder Spaltenebene an  
  
1.  Wählen Sie auf der Seite **Artikel** des Assistenten für neue Veröffentlichung bzw. des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** eine Tabelle aus.  
  
2.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Tabellenartikels festlegen** bzw. **Eigenschaften aller Tabellenartikel festlegen**.  
  
3.  Auf der **Eigenschaften** Registerkarte die **Artikeleigenschaften \<Artikel >** wählen Sie im Dialogfeld einen der folgenden für Werte die **Nachverfolgungsebene** Eigenschaft: **Zeilenebene** oder **nachverfolgung auf Spaltenebene**.  
  
4.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-specify-conflict-tracking-options-for-a-new-merge-article"></a>So geben Sie Konfliktverfolgungsoptionen für einen neuen Mergeartikel an  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus, und geben Sie einen der folgenden Werte für **@column_tracking**an:  
  
    -   **true** &ndash; Nachverfolgung auf Spaltenebene für den Artikel verwenden.  
  
    -   **false** &ndash; Nachverfolgung auf Zeilenebene verwenden (Standard).  
  
#### <a name="to-change-conflict-tracking-options-for-a-merge-article"></a>So ändern Sie die Konfliktverfolgungsoptionen für einen Mergeartikel  
  
1.  Um die Konfliktverfolgungsoptionen für einen Mergeartikel zu bestimmen, führen Sie [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)aus. Achten Sie auf den Wert der **column_tracking** -Option im Resultset für den Artikel. Der Wert **1** bedeutet, dass die Nachverfolgung auf Spaltenebene verwendet wird, und der Wert **0** bedeutet, dass die Nachverfolgung auf Zeilenebene verwendet wird.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **column_tracking** für **@property** und einen der folgenden Werte für **@value**an:  
  
    -   **true** &ndash; Nachverfolgung auf Spaltenebene für den Artikel verwenden.  
  
    -   **false** &ndash; Nachverfolgung auf Zeilenebene verwenden (Standard).  
  
     Geben Sie den Wert **1** sowohl für **@force_invalidate_snapshot** und **@force_reinit_subscription**angegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Erkennen und Beseitigen von Konflikten bei der Mergereplikation](../merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
