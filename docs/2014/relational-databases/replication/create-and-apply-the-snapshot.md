---
title: Erstellen und Anwenden der Momentaufnahme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], applying
- snapshots [SQL Server replication], creating
ms.assetid: 631f48bf-50c9-4015-b9d8-8f1ad92d1ee2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bd78bf7da1a68e7e053af52c4fa8f9cf0cd71094
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52755642"
---
# <a name="create-and-apply-the-snapshot"></a>Erstellen und Anwenden der Momentaufnahme
  Momentaufnahmen werden nach dem Erstellen einer Veröffentlichung vom Momentaufnahme-Agent generiert. Sie können folgendermaßen generiert werden:  
  
-   Sofort. Standardmäßig wird eine Momentaufnahme für eine Mergeveröffentlichung sofort nach dem Erstellen der Veröffentlichung im Assistenten für neue Veröffentlichung generiert.  
  
-   Zu einem geplanten Zeitpunkt. Geben Sie auf der Seite **Momentaufnahme-Agent** des Assistenten für neue Veröffentlichung oder beim Verwenden von gespeicherten Prozeduren bzw. Replikationsverwaltungsobjekten (RMO) einen Zeitpunkt an.  
  
-   Manuell. Führen Sie den Momentaufnahme-Agent von der Eingabeaufforderung oder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aus. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](concepts/replication-agent-executables-concepts.md) und [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
 Bei der Mergereplikation wird jedes Mal eine Momentaufnahme generiert, wenn der Momentaufnahme-Agent ausgeführt wird. Bei der Transaktionsreplikation hängt die Momentaufnahmegenerierung von der Einstellung der **immediate_sync**-Veröffentlichungseigenschaft ab. Ist die Eigenschaft auf TRUE festgelegt (die Standardeinstellung bei der Verwendung des Assistenten für neue Veröffentlichung), wird bei jedem Ausführen des Momentaufnahme-Agents eine Momentaufnahme generiert, der jederzeit auf einen Abonnenten angewendet werden kann. Ist die Eigenschaft auf FALSE festgelegt (die Standardeinstellung bei der Verwendung von **sp_addpublication**), wird die Momentaufnahme nur dann generiert, wenn seit dem letzten Ausführen des Momentaufnahme-Agents ein neues Abonnement hinzugefügt wurde. Abonnenten können erst synchronisiert werden, nachdem der Momentaufnahme-Agent abgeschlossen ist.  
  
 Generierte Momentaufnahmen werden im Standardmomentaufnahmeordner auf dem Verteiler gespeichert. Sie können Momentaufnahmedateien aber auch auf Wechselmedien wie z. B. Wechseldatenträgern, CD-ROMs oder an anderen Speicherorten als dem Standardmomentaufnahmeordner speichern. Darüber hinaus können Sie die Momentaufnahmedateien komprimieren, sodass sie leichter zu speichern und zu übertragen sind, und Skripts vor oder nach der Anwendung der Momentaufnahme auf den Abonnenten ausführen. Weitere Informationen zu diesen Optionen finden Sie unter [Snapshot Options](snapshot-options.md).  
  
 Handelt es sich um eine Momentaufnahme für eine Mergeveröffentlichung, die parametrisierte Filter verwendet, wird die Momentaufnahme mit einem zweiteiligen Prozess erstellt. Zuerst wird eine Schemamomentaufnahme erstellt, die die Replikationsskripts und das Schema der veröffentlichten Objekte enthält, nicht jedoch die Daten. Jedes Abonnement wird dann mit einer Momentaufnahme initialisiert, die die aus der Schemamomentaufnahme kopierten Skripts und das Schema sowie die Daten enthält, die zur Partition des Abonnements gehören. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 Nachdem die Momentaufnahme auf dem Verleger erstellt und am standardmäßigen bzw. einem anderen Momentaufnahmespeicherort gespeichert wurde, kann sie an den Abonnenten übertragen und auf diesen angewendet werden. Der Verteilungs-Agent (bei Momentaufnahme- oder Transaktionsreplikation) bzw. der Merge-Agent (bei Mergereplikation) überträgt die Momentaufnahme und wendet die Schema- und Datendateien während der Erstsynchronisierung auf die Abonnement-Datenbank auf dem Abonnenten an. Standardmäßig erfolgt die Erstsynchronisierung unmittelbar nach dem Erstellen einer Abonnements, wenn Sie den Assistenten für neue Veröffentlichung verwenden. Dieses Verhalten wird von der Option **Initialisierungszeitpunkt** auf der Seite **Abonnements initialisieren** des Assistenten gesteuert. Wenn Momentaufnahmen generiert werden, nachdem ein Abonnement initialisiert wurde, werden sie nicht auf den Abonnenten angewendet, es sei denn, ein Abonnement ist für die erneute Initialisierung markiert. Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](reinitialize-subscriptions.md).  
  
 Nachdem der Verteilungs- bzw. der Merge-Agent die Anfangsmomentaufnahme angewendet hat, gibt er nachfolgende Updates und andere Datenänderungen weiter. Wenn Momentaufnahmen an Abonnenten verteilt und auf ihnen angewendet werden, sind nur die Abonnenten betroffen, die auf eine Anfangsmomentaufnahme oder neue Momentaufnahmen warten. Andere Abonnenten dieser Veröffentlichung (diejenigen, die bereits Einfügungen, Updates, Löschungen oder andere Änderungen der veröffentlichten Daten empfangen) sind nicht betroffen.  
  
 Informationen zum Erstellen und Anwenden der Anfangsmomentaufnahme finden Sie unter [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
 Informationen zum Anzeigen oder Ändern des Standardspeicherorts für den Momentaufnahmeordner finden Sie im entsprechenden Abschnitt.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Geben Sie den standardmäßigen Momentaufnahmespeicherort &#40;SQL Server Management Studio&#41;](specify-the-default-snapshot-location-sql-server-management-studio.md)  
  
-   Replikations- und RMO-Programmierung: [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)   
 [Sichern des Momentaufnahmeordners](security/secure-the-snapshot-folder.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)  
  
  
