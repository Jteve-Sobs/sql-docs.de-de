---
title: Verlegerinformationen, Überwachungsliste für Abonnements Liste (Transaktionsveröffentlichung, SqlServer 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.tran.f1
ms.assetid: 6bc64ddb-5c86-4681-a391-77fc1d3c4e6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53a19b1de1c8aa0be89d0a743007b141bdb169b2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52766912"
---
# <a name="publisher-information-subscription-watch-list-transactional-publication-sql-server-2005-and-later"></a>Verlegerinformationen, Überwachungsliste für Abonnements (Transaktionsveröffentlichung, SQL Server 2005 und später)
  Die Registerkarte **Überwachungsliste für Abonnements** ist für Verteiler verfügbar, die SQL Server 2005 oder spätere Versionen ausführen. Sie ist dafür konzipiert, Informationen zu Abonnements von allen Veröffentlichungen anzuzeigen, die für den ausgewählten Verleger verfügbar sind. Sie können die Liste der Abonnements filtern, um Fehler, Warnungen und Abonnements mit schlechter Leistung anzuzeigen. Diese Registerkarte enthält einen einzelnen Speicherort für den Administrator, um alle Replikationsaktivitäten bei einem Verleger zu überwachen: Der Replikationsmonitor zeigt alle Abonnements, die Aufmerksamkeit erfordern, Grundlage, auf der ausgewählte Replikationstyp und auf der ausgewählten Option in der **anzeigen** im Dropdown Listenfeld. Da die auf dieser Registerkarte angezeigten Elemente auf den aktuellen Daten für Status und Leistung basieren, werden auf dieser Seite nur Abonnements angezeigt, die mit der Option im Listenfeld **Anzeigen** zum aktuellen Zeitpunkt übereinstimmen.  
  
## <a name="options"></a>Optionen  
 Ausführliche Informationen und eine Liste der Aufträge für ein Abonnement können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Abonnements klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortierung**: Sortieren Sie nach einer oder mehreren Spalten in der **Sortierspalten** Dialogfeld.  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge, in der anzeigen in der **Spalten auswählen** Dialogfeld.  
  
-   **Filter**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte in die **Filtereinstellungen** Dialogfeld.  
  
-   **Filter löschen**: Deaktivieren Sie alle filtereinstellungen für das Raster an.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Transaktionsabonnements anzeigen**  
 Wählen Sie den Typ der Abonnements (Transaktionsreplikation, Momentaufnahme oder Mergereplikation) aus, die für den ausgewählten Verleger angezeigt werden sollen.  
  
 **Anzeigen**  
 Wählen Sie die Abonnementstatus aus, die für Abonnements des ausgewählten Typs angezeigt werden sollen. Sie können z. B. auswählen, dass nur die Abonnements angezeigt werden, die einen Fehler aufweisen.  
  
 **Status**  
 Der Status des jeweiligen Abonnements, der vom Status des Verteilungs-Agents bzw. Protokolllese-Agents bestimmt wird. (Es wird der Status mit der höheren Priorität angezeigt. Der Status kann auch durch den Warteschlangenlese-Agent bestimmt werden, wenn Abonnements mit verzögertem Update über eine Warteschlange verwendet werden.)  
  
 Standardmäßig wird das Raster mit den Abonnementinformationen nach den Werten in der **Status** -Spalte sortiert (bei Abonnements mit demselben Status wird nach den Werten unter **Leistung** sortiert). In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt).  
  
-   Fehler  
  
-   Leistung ist kritisch  
  
-   Läuft demnächst ab/Abgelaufen  
  
-   Nicht initialisiertes Abonnement  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   Wird nicht ausgeführt  
  
-   Wird ausgeführt  
  
 Die Sortierreihenfolge bestimmt auch, welcher Wert angezeigt wird, wenn ein Abonnement mehr als einen Statuswert aufweist. Wenn ein Abonnement z. B. einen Fehler aufweist und bald abläuft, dann wird in der **Status** -Spalte der Eintrag **Fehler**angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiertes Abonnement** stellen Warnungen dar. Wenn eine Warnung angezeigt wird, wird unter **Status** auch angezeigt, ob ein Agent ausgeführt wird. Der Status kann also beispielsweise **Wird ausgeführt, Leistungskritisch**sein.  
  
 Die Statuswerte **Leistung ist kritisch** und **Läuft demnächst ab/Abgelaufen** werden nur angezeigt, wenn Schwellenwerte festgelegt werden. Informationen zu Leistungsmessungen und zum Festlegen von Schwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md) und [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name des jeweiligen Abonnements in der Form: *SubscriberName: SubscriptionDatabaseName*.  
  
 **Veröffentlichung**  
 Der Name der Veröffentlichung, mit der ein Abonnement synchronisiert, in der Form wird: *PublicationDatabaseName: PublicationName*.  
  
 **Leistung**  
 Die Leistungsbewertung für jedes Abonnement basiert auf den neuesten Messungen, die vom Replikationsmonitor vorgenommen wurden, und reflektiert keinen Leistungsverlauf. Die Leistung wird für Abonnements von Veröffentlichungen gemessen, für die Leistungsschwellenwerte festgelegt sind. Wenn keine Leistungsschwellenwerte für eine Veröffentlichung festgelegt sind, wird in dieser Spalte **Nicht aktiviert**angezeigt. Die folgenden Werte sind für die Leistungsbewertung möglich:  
  
-   Hervorragend  
  
-   Gut  
  
-   Durchschnittlich  
  
-   Schlecht  
  
-   Kritisch  
  
 Wenn die Leistung kritisch ist, wird **Leistungskritisch** in der **Status** -Spalte angezeigt. Weitere Informationen zur Definition von Leistungsbewertungen und zum Festlegen von Leistungsschwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md).  
  
 **Latenzzeit**  
 Die durchschnittliche Zeit zwischen dem Ausführen eines Commits für eine Transaktion beim Verleger und der entsprechenden Ausführung des Commits für die Transaktion beim Abonnenten. Die angezeigte Latenzzeit basiert auf den neuesten Messungen des Replikationsmonitors. Weitere Informationen zur Messung von Latenzzeiten finden Sie unter [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung des Verteilungs-Agents. Wenn eine Synchronisierung ausgeführt wird, wird **Vorgang wird ausgeführt** angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben für einen Verleger &#40;Replikationsmonitor&#41;](monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
