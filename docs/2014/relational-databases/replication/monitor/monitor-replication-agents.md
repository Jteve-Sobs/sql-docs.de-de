---
title: Überwachen der Replikations-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1456a3113feb8a32ce9876ef7ef060f96f66910b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800732"
---
# <a name="monitor-replication-agents"></a>Überwachen der Replikations-Agents
  Der Replikationsmonitor von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bietet einen systemischen Überblick über die Replikationsaktivität und erleichtert gleichzeitig die Suche nach Informationen zu einem bestimmten Agent. Die folgende Liste enthält alle Agents, die Registerkarten im Replikationsmonitor, auf denen die Agents zu finden sind, und einen Verweis darauf, wo Sie Informationen zum Zugreifen auf die jeweilige Registerkarte finden:  
  
-   Die folgenden Agents sind Veröffentlichungen im Replikationsmonitor zugeordnet:  
  
    -   Momentaufnahme-Agent  
  
    -   Protokolllese-Agent  
  
    -   Warteschlangenlese-Agent  
  
     Den Zugriff auf Informationen und Aufgaben im Zusammenhang mit diesen Agents kann über die folgenden Registerkarten: **Agents** (verfügbar für jeden Verleger und jede Veröffentlichung) und **Warnungen** (verfügbar für jede Veröffentlichung). Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben für die einer Veröffentlichung zugeordneten Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-publication-agents.md).  
  
-   Die folgenden Agents sind Abonnements im Replikationsmonitor zugeordnet:  
  
    -   Verteilungs-Agent  
  
    -   Merge-Agent  
  
     Den Zugriff auf Informationen und Aufgaben im Zusammenhang mit diesen Agents kann über die folgenden Registerkarten: **Überwachungsliste für Abonnements** (verfügbar für jeden Verleger) oder die **alle Abonnements** (verfügbar für jede Veröffentlichung). Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agent &#40;Replikationsmonitor &#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a>Überwachen der Replikations-Agents mit SQL Server Management Studio  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] stellt die folgenden Dialogfelder zum Überwachen von Replikations-Agents bereit:  
  
-   **Status des Momentaufnahme-Agents anzeigen** (bei allen Veröffentlichungen)  
  
-   **Status des Protokolllese-Agents anzeigen** (bei allen Transaktionsveröffentlichungen)  
  
-   **Synchronisierungsstatus anzeigen** (bei allen Abonnements; von diesem Dialogfeld aus können Sie auf den Verteilungs-Agent und den Merge-Agent zugreifen)  
  
 Der Replikationsmonitor stellt darüber hinaus zusätzliche Informationen zu den einzelnen Agents bereit und bietet außerdem die Möglichkeit der Überwachung des Warteschlangenlese-Agents, sofern dieser verwendet wird. Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben für die mit einer Veröffentlichung verknüpften Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-publication-agents.md), [Anzeigen von Informationen und Ausführen von Aufgaben für die mit einer Veröffentlichung verknüpften Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-publication-agents.md) und [Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a>So überwachen Sie den Momentaufnahme-Agent und den Protokokolllese-Agent  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Veröffentlichung, und klicken Sie dann auf **Status des Protokolllese-Agents anzeigen** bzw. **Status des Momentaufnahme-Agents anzeigen**.  
  
4.  Führen Sie im Dialogfeld **Status des Protokolllese-Agents anzeigen** bzw. **Status des Momentaufnahme-Agents anzeigen** einen oder mehrere der folgenden Schritte aus:  
  
    -   Zeigen Sie den Agentstatus an.  
  
    -   Starten oder beenden Sie den Agent bei Bedarf.  
  
    -   Klicken Sie auf **Überwachen** , um den **Replikationsmonitor**zu starten.  
  
5.  Klicken Sie auf **Schließen**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a>So überwachen Sie den Verteilungs-Agent und den Merge-Agent (vom Verleger aus)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Erweitern Sie die Veröffentlichung für das Abonnement, das überwacht werden soll.  
  
4.  Klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Synchronisierungsstatus anzeigen**.  
  
5.  Führen Sie im Dialogfeld **Synchronisierungsstatus anzeigen** einen oder mehrere der folgenden Schritte aus:  
  
    -   Zeigen Sie den Agentstatus an.  
  
    -   Starten oder beenden Sie den Agent bei Bedarf.  
  
    -   Klicken Sie bei Pushabonnements auf **Überwachen** , um den **Replikationsmonitor**zu starten.  
  
    -   Klicken Sie bei Pullabonnements auf **Auftragsverlauf anzeigen** , um den **Protokolldatei-Viewer**zu starten, in dem das Ergebnis aus dem Agentprotokoll angezeigt wird.  
  
6.  Klicken Sie auf **Schließen**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a>So überwachen Sie den Verteilungs-Agent und den Merge-Agent (vom Abonnenten aus)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das zu überwachende Abonnement, und klicken Sie dann auf **Synchronisierungsstatus anzeigen**.  
  
4.  Führen Sie im Dialogfeld **Synchronisierungsstatus anzeigen** einen oder mehrere der folgenden Schritte aus:  
  
    -   Zeigen Sie den Agentstatus an.  
  
    -   Starten oder beenden Sie den Agent bei Bedarf.  
  
    -   Klicken Sie auf **Auftragsverlauf anzeigen** , um den **Protokolldatei-Viewer**zu starten, in dem das Ergebnis aus dem Agentprotokoll angezeigt wird.  
  
5.  Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Replikation](../monitoring-replication.md)   
 [Übersicht über Replikations-Agents](../agents/replication-agents-overview.md)  
  
  
