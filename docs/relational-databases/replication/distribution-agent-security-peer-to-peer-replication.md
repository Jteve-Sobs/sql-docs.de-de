---
title: Sicherheit für den Verteilungs-Agent (Peer-zu-Peer)
description: In diesem Artikel wird die Seite „Sicherheit für den Verteilungs-Agent“ für eine Peer-zu-Peer-Replikationstopologie in SQL Server Management Studio beschrieben.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d1329f2b432727731565da796baf021328b9b606
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321787"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>Sicherheit für den Verteilungs-Agent (Peer-zu-Peer-Replikation)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe der Seite **Sicherheit für den Verteilungs-Agent** können Sie die Konten angeben, unter denen der Verteilungs-Agent ausgeführt wird und Verbindungen mit den Computern in einer Peer-zu-Peer-Topologie hergestellt werden. Informationen zu erforderlichen Berechtigungen für Agents und bewährten Methoden für die Replikationssicherheit finden Sie unter [Sicherheitsmodell des Replikations-Agent](../../relational-databases/replication/security/replication-agent-security-model.md) und [Replikationssicherheit, bewährte Methoden](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Wenn der Verteilungs-Agent für ein Abonnement bereits in einer früheren Ausführung dieses Assistenten konfiguriert wurde, können Sie die entsprechenden in diesem Assistenten verwendeten Anmeldeinformationen nicht ändern. Von Ihnen neu angegebene Anmeldeinformationen werden ignoriert. Sie können die Anmeldeinformationen im Dialogfeld **Abonnementeigenschaften** ändern. Weitere Informationen finden Sie unter [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Tastatur  
 Klicken Sie in der Zeile für jeden Abonnenten auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um auf das Dialogfeld **Sicherheit für den Verteilungs-Agent** zuzugreifen. Klicken Sie im geöffneten Dialogfeld **Sicherheit für den Verteilungs-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die von den Agents verwendeten Konten erforderlich sind.  
  
 Wenn Sie die Einstellungen in einem der beiden Dialogfelder eingegeben haben, werden im Raster die Verbindungsinformationen zu dem Abonnenten angezeigt.  
  
 **Agent für Abonnent**  
 Der Name der einzelnen Peers.  
  
 **Peerdatenbank**  
 Die Datenbank auf dem Peer, der sowohl als Veröffentlichungs- als auch als Abonnementdatenbank dient.  
  
 **Verbindung mit Verteiler**  
 Der Kontext, unter dem die Verbindung mit dem Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird. Dieser Assistent erstellt Pushabonnements (die Verbindung mit dem Verteiler ist gleichzeitig die lokale Verbindung), sodass in dem betreffenden Feld immer **Impersonate '\<Domain>\\<Login\>'** oder **Impersonate '\<Computer>\\<Login\>'** angezeigt wird.  
  
 **Verbindung mit Abonnent**  
 Der Kontext, unter dem die Verbindung mit dem Abonnenten hergestellt wird. Die Verbindung kann entweder mithilfe des Kontexts des Windows-Kontos hergestellt werden, unter dem der Agent ausgeführt wird, oder mithilfe des Kontexts einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung. Das Feld zeigt eine der folgenden Angaben **Use login '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** oder **Impersonate '\<Computer>\\<Login\>'** an. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
