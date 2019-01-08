---
title: Agentsicherheit (Assistent für neue Veröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7acd2c6ab698a8fafb8e89c21376973163d88c2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758202"
---
# <a name="agent-security-new-publication-wizard"></a>Agentsicherheit (Assistent für neue Veröffentlichung)
  Mithilfe der Seite **Agentsicherheit** können Sie die Konten angeben, unter denen die folgenden Agents ausgeführt werden und Verbindungen mit den Computern in einer Replikationstopologie herstellen:  
  
-   Der Momentaufnahme-Agent für alle Veröffentlichungen.  
  
-   Der Protokolllese-Agent für alle Transaktionsveröffentlichungen.  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit Aktualisierung gestatten. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag wird erstellt, wenn Sie **Transaktionsveröffentlichung mit aktualisierbaren Abonnements** auf der Seite **Veröffentlichungstyp** angegeben haben, unabhängig vom Typ der verwendeten aktualisierbaren Abonnements. Weitere Informationen zu aktualisierbaren Abonnements finden Sie unter [Aktualisierbare Abonnements für die Transaktionsreplikation](transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 Weitere Informationen zu den für Agents erforderlichen Berechtigungen und zu bewährten Methoden der Replikationssicherheit finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md) und [Replication Security Best Practices](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Optionen  
 **Momentaufnahme-Agent**  
 Wird für alle Veröffentlichungen angezeigt. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Momentaufnahme-Agent** anzugeben.  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Momentaufnahme-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Momentaufnahme-Agent verwendeten Konten erforderlich sind.  
  
 **Protokolllese-Agent**  
 Wird für alle Transaktionsveröffentlichungen angezeigt. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Protokolllese-Agent** anzugeben.  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Protokolllese-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Protokolllese-Agent verwendeten Konten erforderlich sind.  
  
> [!NOTE]  
>  Es gibt einen Protokolllese-Agent für jede Datenbank, die mithilfe der Transaktionsreplikation veröffentlicht wird. Wenn bereits eine Transaktionsveröffentlichung in der Datenbank vorhanden ist, sind die Sicherheitseinstellungen schreibgeschützt. Sie können die Einstellungen im Dialogfeld **Veröffentlichungseigenschaften** ändern, diese Änderungen wirken sich jedoch auf alle Transaktionsveröffentlichungen in der Datenbank aus.  
  
 **Warteschlangenlese-Agent**  
 Wird für Momentaufnahme- oder Transaktionsveröffentlichungen angezeigt, die aktualisierbare Abonnements zulassen. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** anzugeben. Bei Abschluss dieses Assistenten wird ein Auftrag des Warteschlangenlese-Agents erstellt, unabhängig davon, ob Sie Abonnements mit verzögertem Update über eine Warteschlange erstellen. Wenn Sie keine Abonnements mit verzögertem Update über eine Warteschlange erstellen möchten, können Sie den Auftrag deaktivieren. Mit der rechten Maustaste klicken Sie auf den Auftrag (mit dem Namen in der Form: *[\<Publisher >].\< ganze Zahl >*.) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Aufträge** Ordner, und klicken Sie dann auf **Deaktivieren**  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Warteschlangenlese-Agent verwendeten Konten erforderlich sind.  
  
> [!NOTE]  
>  Für jede Verteilungsdatenbank (und alle dazugehörigen Verleger) gibt es einen Warteschlangenlese-Agent. Wenn eine Transaktionsveröffentlichung, die Abonnements mit verzögertem Update über eine Warteschlange gestattet, bereits auf einem der Verleger vorhanden ist, die eine bestimmte Verteilungsdatenbank verwenden, sind die Sicherheitseinstellungen schreibgeschützt. Sie können das Konto, unter dem der Warteschlangenlese-Agent ausgeführt wird und Verbindungen herstellt, im Dialogfeld **Verteilereigenschaften** ändern. Die Änderungen wirken sich jedoch auf alle Veröffentlichungen aller Verleger aus, die die Verteilungsdatenbank verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](create-updatable-subscription-transactional-publication-transact-sql.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](security/manage-logins-and-passwords-in-replication.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Übersicht über Replikations-Agents](agents/replication-agents-overview.md)  
  
  
