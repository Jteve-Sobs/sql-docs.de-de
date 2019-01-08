---
title: Übersicht über den Replikationsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ae9c89b3fa3d9392e27cce9199f7c1b1b8f31dee
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52771422"
---
# <a name="monitoring-replication"></a>Überwachen der Replikation
  Der[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsmonitor ist ein grafisches Tool, mit dem Sie die allgemeine Integrität der Replikationstopologie überwachen können. Der Replikationsmonitor stellt detaillierte Informationen zum Status und der Leistung von Veröffentlichungen und Abonnements bereit und unterstützt Sie bei der Beantwortung allgemeiner Fragen:  
  
-   Arbeitet das System fehlerfrei?  
  
-   Welche Abonnements sind langsam?  
  
-   Wie weit ist das Transaktionsabonnement in Verzug?  
  
-   Wie lange dauert es bei der Transaktionsreplikation, bis eine Transaktion, für die ein Commit ausgeführt wurde, den Abonnenten erreicht?  
  
-   Warum ist das Mergeabonnement langsam?  
  
-   Warum wird ein Agent nicht ausgeführt?  
  
 Zum Überwachen der Replikation muss ein Benutzer Mitglied der festen Serverrolle **sysadmin** auf dem Verteiler oder Mitglied der festen Datenbankrolle **replmonitor** in der Verteilungsdatenbank sein. Ein Systemadministrator kann jeden Benutzer zur **replmonitor** -Rolle hinzufügen. Anhand dieser Rolle kann ein Benutzer die Replikationsaktivität im Replikationsmonitor anzeigen. Er kann die Replikation jedoch nicht verwalten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen finden Sie Informationen zu den Funktionen des Replikationsmonitors.  
  
 [Übersicht über die Benutzeroberfläche des Replikationsmonitors](overview-of-the-replication-monitor-interface.md)  
 Beschreibt alle Fenster und Registerkarten des Replikationsmonitors und enthält Informationen zur Beantwortung der oben aufgeführten Fragen.  
  
 [Starten des Replikationsmonitors](start-the-replication-monitor.md)  
 Beschreibt, wie der Replikationsmonitor gestartet wird.  
  
 [Zulassen, dass Nichtadministratoren den Replikationsmonitor verwenden](allow-non-administrators-to-use-replication-monitor.md)  
 Beschreibt, wie Nicht-Administratoren Berechtigungen zugewiesen werden, damit sie Replikationsmonitor verwenden können.  
  
 [Hinzufügen und Entfernen von Verlegern vom Replikationsmonitor](add-and-remove-publishers-from-replication-monitor.md)  
 Beschreibt das Hinzufügen und Entfernen von Verlegern zum/aus dem Replikationsmonitor.  
  
 [Aktualisieren von Daten im Replikationsmonitor](refresh-data-in-replication-monitor.md)  
 Beschreibt das Aktualisieren von Daten im Replikationsmonitor.  
  
 [Überwachen der Leistung mit dem Replikationsmonitor](monitor-performance-with-replication-monitor.md)  
 Beschreibt, wie die Leistung im Replikationsmonitor überwacht wird, und enthält Informationen zum Festlegen von Leistungsschwellenwerten. Das Thema umfasst Informationen zu Statistiken der Mergereplikation auf Artikelebene, durch die die Verarbeitung detailliert veranschaulicht wird.  
  
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](measure-latency-and-validate-connections-for-transactional-replication.md)  
 Beschreibt Überwachungstoken, mit deren Hilfe Sie die Leistung einer Transaktionsreplikationstopologie messen können.  
  
 [Überwachen der Replikations-Agents](../agents/replication-agents.md)  
 Beschreibt, wie Sie Informationen zu den einzelnen Replikations-Agents finden.  
  
 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)  
 Beschreibt die Warnungen und Schwellenwerte, die Sie im Replikationsmonitor festlegen können. Sie sollten Warnungen für Ihre Topologie aktivieren, damit Sie rechtzeitig über Status und Leistung informiert werden.  
  
 [Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors](caching-refresh-and-replication-monitor-performance.md)  
 Beschreibt, wie der Replikationsmonitor Daten und Berechnungen zum Verbessern der Leistung zwischenspeichert; erläutert, wie eine Aktualisierung der Benutzeroberfläche mit der Aktualisierung des Cache zusammenhängt.  
  
 [Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor](view-publication-and-subscription-status-in-replication-monitor.md)  
 Beschreibt, wie Statusinformationen einer Veröffentlichung oder eines Abonnements mithilfe des Replikationsmonitors angezeigt werden.  
  
 [Anzeigen von Informationen und Ausführen von Aufgaben für einen Verleger &#40;Replication Monitor&#41;](view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Beschreibt das Anzeigen von Informationen und Ausführen von Aufgaben für einen Verleger mithilfe des Replikationsmonitors.  
  
 [Anzeigen von Informationen und Ausführen von Aufgaben für eine Veröffentlichung &#40;Replication Monitor&#41;](view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Beschreibt das Anzeigen von Informationen und Ausführen von Aufgaben für eine Veröffentlichung mithilfe des Replikationsmonitors.  
  
 [Anzeigen von Informationen und Ausführen von Aufgaben für die einer Veröffentlichung zugeordneten Agents &#40;Replication Monitor&#41;](view-information-and-perform-tasks-for-publication-agents.md)  
 Beschreibt das Anzeigen von Informationen und Ausführen von Aufgaben für die einer Veröffentlichung zugeordneten Agents mithilfe des Replikationsmonitors.  
  
 [Anzeigen von Informationen und Ausführen von Aufgaben für ein Abonnement &#40;Replication Monitor&#41;](view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Beschreibt das Anzeigen von Informationen und Ausführen von Aufgaben für ein Abonnement mithilfe des Replikationsmonitors.  
  
 [Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents &#40;Replication Monitor&#41;](view-information-and-perform-tasks-for-subscription-agents.md)  
 Beschreibt das Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents mithilfe des Replikationsmonitors.  
  
  
