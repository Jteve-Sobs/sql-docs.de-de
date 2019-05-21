---
title: Broker:Activation (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 67578d83b1845086186cc791fd6750115842c9fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701198"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Activation** -Ereignis, wenn eine Warteschlangenüberwachung eine gespeicherte Aktivierungsprozedur startet oder eine QUEUE_ACTIVATION-Benachrichtigung sendet oder wenn eine gespeicherte Aktivierungsprozedur, die von einer Warteschlangenüberwachung gestartet wurde, beendet wird.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Datenspalten der Broker:Activation-Ereignisklasse  
  
|Datenspalte|Typ|Beschreibung|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**EventClass**|**int**|Der Typ der aufgezeichneten Ereignisklasse. Immer **163** für **Broker:Activation**.|27|nein|  
|**EventSequence**|**int**|Die Sequenznummer für dieses Ereignis.|51|nein|  
|**EventSubClass**|**nvarchar**|Die spezielle Aktion, die von diesem Ereignis gemeldet wird. Einer der folgenden Werte:<br /><br /> **Gestartet**:   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat eine gespeicherte Aktivierungsprozedur gestartet.<br /><br /> **Abgeschlossen**: Die gespeicherte Aktivierungsprozedur wurde normal beendet.<br /><br /> **Abgebrochen**: Die gespeicherte Aktivierungsprozedur wurde mit einem Fehler beendet.|21|nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|**IntegerData**|**int**|Die Anzahl der in dieser Warteschlange aktiven Aufgaben.|25|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Benutzerkontensteuerung|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Benutzerkontensteuerung|  
|**ObjectID**|**int**|Die diesem Ereignis zugeordnete Warteschlange.|22|nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SPID**|**int**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|nein|  
  
  
