---
title: QN:Subscription (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], QN:Subscription
ms.assetid: 4916167e-8541-43b4-900e-ec8e6adcbc34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 04228a12dfec0aa7d8bb63869b332432dc274300
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51665016"
---
# <a name="qnsubscription-event-class"></a>QN:Subscription (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Das QN:Subscription-Ereignis übermittelt Informationen über Benachrichtigungsabonnements.  
  
## <a name="qnsubscription-event-class-data-columns"></a>Datenspalten der QN:Subscription-Ereignisklasse  
  
|Datenspalte|Typ|Beschreibung|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|ClientProcessID|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|DatabaseID|**int**|Die ID der Datenbank, die durch die USE *Datenbank* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *Datenbank*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die Server Name-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|**nvarchar**|Der Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventClass|**int**|Ereignistyp = 199.|27|nein|  
|EventSequence|**int**|Die Sequenznummer für dieses Ereignis.|51|nein|  
|EventSubClass|**nvarchar**|Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert. Diese Spalte kann die folgenden Werte enthalten:<br /><br /> **Subscription registered**: Gibt an, wann das Abfragebenachrichtigungsabonnement erfolgreich in der Datenbank registriert wird.<br /><br /> **Subscription rewound**: Gibt an, wann [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Abonnementanforderung erhält, die genau mit einem bereits vorhandenen Abonnement übereinstimmt. In diesem Fall legt [!INCLUDE[ssDE](../../includes/ssde-md.md)] für den Timeoutwert des vorhandenen Abonnements den in der neuen Abonnementanforderung festgelegten Timeoutwert fest.<br /><br /> **Subscription fired**: Gibt an, wann ein Benachrichtigungsabonnement eine Benachrichtigungsmeldung erzeugt.<br /><br /> **Firing failed with broker error**: Gibt an, wann eine Benachrichtigungsmeldung aufgrund eines [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Fehlers nicht ausgeführt werden kann.<br /><br /> **Firing failed without broker error**: Gibt an, wann eine Benachrichtigungsmeldung nicht ausgeführt werden kann, ohne dass ein [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Fehler vorliegt.<br /><br /> **Broker error intercepted**: Gibt an, dass [!INCLUDE[ssSB](../../includes/sssb-md.md)] in der von der Abfragebenachrichtigung verwendeten Konversation einen Fehler übermittelt hat.<br /><br /> **Subscription deletion attempt**: Gibt an, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] versucht hat, ein abgelaufenes Abonnement zu löschen, um Ressourcen freizugeben.<br /><br /> **Subscription deletion failed**: Gibt an, dass beim Löschen eines abgelaufenen Abonnement ein Fehler generiert wurde. Die Löschung des Abonnements wird in [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatisch erneut geplant, um Ressourcen frei zu geben.<br /><br /> **Subscription destroyed**: Gibt an, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] erfolgreich ein abgelaufenes Abonnement gelöscht hat.|21|Benutzerkontensteuerung|  
|GroupID|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IsSystem|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.<br /><br /> 0 = Benutzer<br /><br /> 1 = System|60|nein|  
|LoginName|**nvarchar**|Der Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder Windows-Anmeldeinformationen im Format DOMAIN\Username).|11|nein|  
|LoginSID|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NTDomainName|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|Benutzerkontensteuerung|  
|NTUserName|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Benutzerkontensteuerung|  
|RequestID|**int**|Der Bezeichner der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn beispielsweise eine Anwendung mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt und eine Anweisung als Login2 ausführt, zeigt SessionLoginName "Login1" an, und LoginName zeigt "Login2" an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|**ntext**|Gibt ein XML-Dokument mit spezifischen Informationen zu diesem Ereignis zurück. Dieses Dokument stimmt mit dem XML-Schema überein, das auf der Seite [SQL Server Query Notification Profiler Event Schema](https://go.microsoft.com/fwlink/?LinkId=63331) (in englischer Sprache) zur Verfügung gestellt wird.|1|Benutzerkontensteuerung|  
  
  
