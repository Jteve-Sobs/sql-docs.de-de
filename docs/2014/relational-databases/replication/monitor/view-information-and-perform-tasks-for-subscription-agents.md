---
title: Anzeigen von Informationen und Ausführen von Aufgaben für die Agents, die in Zusammenhang mit einem Abonnement (Replikationsmonitor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: fbb59d31-2424-4552-9195-0da8d83e755f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c1ded219b3b4a103b5cc8f98cdb86c2a8a52e21d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815712"
---
# <a name="view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-replication-monitor"></a>Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents (Replikationsmonitor)
  Im Replikationsmonitor gibt es zwei Registerkarten, über die Sie auf Informationen zu den Agents zugreifen können, die dem jeweiligen Abonnement zugeordnet sind:  
  
-   **Alle Abonnements**  
  
     Auf dieser Registerkarte werden Informationen zu allen Abonnements für die ausgewählte Veröffentlichung angezeigt.  
  
-   **Überwachungsliste für Abonnements**  
  
     Auf dieser Registerkarte werden Informationen zu Abonnements von allen auf dem ausgewählten Verleger vorhandenen Veröffentlichungen angezeigt, für die Fehlermeldungen oder Warnungen ausgegeben wurden bzw. bei denen Leistungsprobleme aufgetreten sind. Bei Verteilern, auf denen Versionen vor [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ausgeführt werden, wird diese Registerkarte nicht angezeigt.  
  
 Weitere Informationen zu den Optionen der einzelnen Registerkarten finden Sie, wenn Sie auf die Registerkarte im rechten Bereich und dann auf **Hilfe** auf der Menüleiste klicken. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-all-subscriptions-tab"></a>So können Sie für die einem Abonnement zugeordneten Agents Informationen anzeigen und Aufgaben ausführen (Registerkarte Alle Abonnements)  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** , um sich Informationen zu den Abonnements anzeigen zu lassen. Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:  
  
    -   Wenn Sie detaillierte Informationen zum Agent angezeigt bekommen möchten, der dem jeweiligen Abonnement zugeordnet ist, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Details anzeigen**. Zu den Detailinformationen gehören: Agentverlauf und Fehlermeldungen, bei der Transaktionsreplikation eine Leistungsstatistik und bei der Mergereplikation eine Synchronisierungsstatistik auf Artikelebene.  
  
         Welche Registerkarten das Detailfenster enthält, hängt von der Art des Abonnements ab: Bei Momentaufnahmeabonnements wird die Registerkarte **Verlauf Verteiler zu Abonnent**angezeigt, bei Transaktionsabonnements enthält das Fenster die Registerkarten **Verlauf Verleger zu Verteiler**, **Verlauf Verteiler zu Abonnent**und **Nicht verteilte Befehle**, und bei Mergeabonnements finden Sie hier die Registerkarte **Synchronisierungsverlauf**.  
  
    -   Wenn Sie ein Pushabonnement synchronisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Synchronisierung starten**.  
  
    -   Wenn Sie ein Abonnement erneut initialisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement erneut initialisieren**.  
  
    -   Wenn Sie ein einzelnes Mergeabonnement überprüfen möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement überprüfen**. Wenn Sie alle Abonnements für eine Mergeveröffentlichung überprüfen möchten, klicken Sie mit der rechten Maustaste auf die entsprechende Veröffentlichung, und klicken Sie dann auf **Alle Abonnements überprüfen**. Wenn alle Abonnements für eine Transaktionsveröffentlichung überprüft werden sollen, klicken Sie mit der rechten Maustaste auf die betreffende Veröffentlichung, und klicken Sie dann auf **Abonnements überprüfen**.  
  
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-subscription-watch-list-tab"></a>So können Sie für die einem Abonnement zugeordneten Agents Informationen anzeigen und Aufgaben ausführen (Registerkarte Überwachungsliste für Abonnements)  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, und klicken Sie dann auf einen Verleger.  
  
2.  Klicken Sie auf die Registerkarte **Überwachungsliste für Abonnements** , um sich Informationen zu den Abonnements anzeigen zu lassen. Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:  
  
    -   Wenn Sie detaillierte Informationen zum Agent angezeigt bekommen möchten, der dem jeweiligen Abonnement zugeordnet ist, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Details anzeigen**. Zu den Detailinformationen gehören: Agentverlauf und Fehlermeldungen, bei der Transaktionsreplikation eine Leistungsstatistik und bei der Mergereplikation eine Synchronisierungsstatistik auf Artikelebene.  
  
         Welche Registerkarten das Detailfenster enthält, hängt von der Art des Abonnements ab: Bei Momentaufnahmeabonnements wird die Registerkarte **Verlauf Verteiler zu Abonnent**angezeigt, bei Transaktionsabonnements enthält das Fenster die Registerkarten **Verlauf Verleger zu Verteiler**, **Verlauf Verteiler zu Abonnent**und **Leistung**, und bei Mergeabonnements finden Sie hier die Registerkarte **Synchronisierungsverlauf**.  
  
    -   Wenn Sie ein Pushabonnement synchronisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Synchronisierung starten**.  
  
    -   Wenn Sie ein Abonnement erneut initialisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement erneut initialisieren**.  
  
    -   Wenn Sie ein einzelnes Mergeabonnement überprüfen möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement überprüfen**. Wenn Sie alle Abonnements für eine Mergeveröffentlichung überprüfen möchten, klicken Sie mit der rechten Maustaste auf die entsprechende Veröffentlichung, und klicken Sie dann auf **Alle Abonnements überprüfen**. Wenn alle Abonnements für eine Transaktionsveröffentlichung überprüft werden sollen, klicken Sie mit der rechten Maustaste auf die betreffende Veröffentlichung, und klicken Sie dann auf **Abonnements überprüfen**.  
  
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Informationen und Ausführen von Aufgaben für ein Abonnement &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Überwachen der Replikation](../monitoring-replication.md)  
  
  
