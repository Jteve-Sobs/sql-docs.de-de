---
title: Verlegerinformationen, Überwachungsliste für Abonnements (Mergeveröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publisherinfo.subscriptionssummary.merge.f1
ms.assetid: 4ec956bf-5cef-4377-a1d1-8c7f0107a6cb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cafbae856962fe7fda7ffb43fe1bc530bca204b7
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126650"
---
# <a name="publisher-information-subscription-watch-list-merge-publication"></a>Verlegerinformationen, Überwachungsliste für Abonnements (Mergeveröffentlichung)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Registerkarte **Überwachungsliste für Abonnements** ist für Verteiler verfügbar, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen ausgeführt werden. Sie ist dafür konzipiert, Informationen zu Abonnements von allen Veröffentlichungen anzuzeigen, die für den ausgewählten Verleger verfügbar sind. Sie können die Liste der Abonnements filtern, um Fehler, Warnungen und Abonnements mit schlechter Leistung anzuzeigen. Auf dieser Registerkarte können Administratoren sämtliche Replikationsaktivitäten auf einem Verleger überwachen: Der Replikationsmonitor zeigt entsprechend des ausgewählten Replikationstyps und der im Dropdown-Listenfeld **Anzeigen** ausgewählten Option alle Abonnements an, für die Handlungsbedarf besteht. Da die auf dieser Registerkarte angezeigten Elemente auf den aktuellen Daten für Status und Leistung basieren, werden auf dieser Seite nur Abonnements angezeigt, die mit der Option im Listenfeld **Anzeigen** zum aktuellen Zeitpunkt übereinstimmen.  
  
## <a name="options"></a>Optionen  
 Ausführliche Informationen und eine Liste der Aufträge für ein Abonnement können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Abonnements klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren:** Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren**.  
  
-   **Anzuzeigende Spalten auswählen:** Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern:** Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen**.  
  
-   **Filter löschen:** Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Mergeabonnements anzeigen**  
 Wählen Sie den Typ der Abonnements (Transaktionsreplikation, Momentaufnahme oder Mergereplikation) aus, die für den ausgewählten Verleger angezeigt werden sollen.  
  
 **Anzeigen**  
 Wählen Sie die Abonnementstatus aus, die für Abonnements des ausgewählten Typs angezeigt werden sollen. Sie können z. B. auswählen, dass nur die Abonnements angezeigt werden, die einen Fehler aufweisen.  
  
 **Status**  
 Der Status der einzelnen Abonnements, der durch den Status des Merge-Agents bestimmt wird.  
  
 Standardmäßig wird das Raster mit den Abonnementinformationen nach den Werten in der **Status** -Spalte sortiert (bei Abonnements mit demselben Status wird nach den Werten unter **Leistung** sortiert). In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt).  
  
-   Fehler  
  
-   Leistung ist kritisch  
  
-   Langer Mergevorgang  
  
-   Läuft demnächst ab/Abgelaufen  
  
-   Nicht initialisiertes Abonnement  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   Wird synchronisiert  
  
-   Synchronisierung wird nicht ausgeführt  
  
 Die Sortierreihenfolge bestimmt auch, welcher Wert angezeigt wird, wenn ein Abonnement mehr als einen Statuswert aufweist. Wenn ein Abonnement z. B. einen Fehler aufweist und bald abläuft, dann wird in der **Status** -Spalte der Eintrag **Fehler**angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Langer Mergevorgang**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiertes Abonnement** stellen Warnungen dar. Wenn eine Warnung angezeigt wird, wird unter **Status** auch angezeigt, ob ein Agent synchronisiert wird. Der Status kann also beispielsweise **Wird synchronisiert, Leistungskritisch**sein.  
  
 Die Statuswerte **Läuft demnächst ab/Abgelaufen** und **Langer Mergevorgang** können nur angezeigt werden, wenn Schwellenwerte festgelegt sind. Der Statuswert **Leistung ist kritisch** kann nur angezeigt werden, nachdem fünf Synchronisierungen mit demselben Verbindungstyp (DFÜ oder LAN) stattgefunden haben. Informationen zu Leistungsmessungen und zum Festlegen von Schwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) und [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name jedes Abonnements im Format: *Abonnentenname: Name_der_Abonnentendatenbank*.  
  
 **Anzeigename**  
 Die Beschreibung der einzelnen Abonnements. Die Beschreibung wird im Dialogfeld **Abonnementeigenschaften** eingegeben oder mit dem **@description** -Parameter von [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) oder [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)angezeigt. Benutzer verwenden die Beschreibung häufig als Anzeigename oder Spitzname des Abonnements.  
  
 **Veröffentlichung**  
 Der Name der Veröffentlichung, mit der ein Abonnement synchronisiert wird, im Format: *Name_der_Veröffentlichungsdatenbank: Veröffentlichungsname*.  
  
 **Leistung**  
 Die Leistungsbewertung für die einzelnen Abonnements auf der Grundlage der neuesten Messungen der Übermittlungsrate mithilfe des Replikationsmonitors. Die Bewertung wird bestimmt, indem die Leistung der einzelnen Abonnements mit der durchschnittlichen bisherigen Leistung der Veröffentlichungsabonnements mit dem gleichen Verbindungstyp (DFÜ oder LAN) verglichen wird. Der Replikationsmonitor zeigt einen Wert an, nachdem fünf Synchronisierungen mit jeweils mindestens 50 Änderungen über denselben Verbindungstyp stattgefunden haben. Falls weniger als fünf Synchronisierungen mit mindestens 50 Änderungen stattgefunden haben, oder wenn die letzte Synchronisierung nicht mindestens 50 Änderungen umfasst hat, ist diese Spalte leer.  
  
> [!NOTE]  
>  Die Leistung basiert auf dem in der **Verbindung** -Spalte angezeigten Verbindungstyp. Deshalb ist es möglich, dass für ein Abonnement mit einer geringeren Übermittlungsrate eine bessere Leistungsbewertung angezeigt wird, als für ein anderes Abonnement, wenn das erste Abonnement über eine langsamere Verbindung synchronisiert wird.  
  
 Die folgenden Werte sind für die Leistungsbewertung möglich:  
  
-   Hervorragend  
  
-   Gut  
  
-   Durchschnittlich  
  
-   Schlecht  
  
 Weitere Informationen zur Definition von Leistungsbewertungen und zum Festlegen von Leistungsschwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 **Übermittlungsrate**  
 Die Anzahl an Zeilen, die pro Sekunde vom Merge-Agent verarbeitet werden.  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung von Merge-Agent. Während dieser Synchronisierung können Änderungen verarbeitet worden sein oder nicht. Wenn sich eine Synchronisierung in Bearbeitung befindet, wird ein vollständiger Prozentwert angezeigt.  
  
 **Dauer**  
 Der Zeitraum der Ausführung von Merge-Agent während der letzten Synchronisierung. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit synchronisierten Merge-Agents oder die Gesamtzeit des zuvor synchronisierten Merge-Agents an.  
  
 **Verbindung**  
 Die Art der Verbindung zwischen dem Abonnenten und dem Verleger. Die Werte **LAN**, **DFÜ**und **Internet**sind möglich. Der Wert **Internet** wird angezeigt, wenn für das Abonnement die Websynchronisierung verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben für einen Verleger &#40;Replikationsmonitor&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Websynchronisierung für die Mergereplikation](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
