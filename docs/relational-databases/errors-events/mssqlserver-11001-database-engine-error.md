---
title: MSSQLSERVER_11001 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5468b81930e1fd54602b0b91f9147b7c3b09c109
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048313"
---
# <a name="mssqlserver11001"></a>MSSQLSERVER_11001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|11001|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Fehler beim Herstellen einer Verbindung mit dem Server.  Beim Herstellen einer Verbindung mit SQL Server kann dieser Fehler durch den Umstand verursacht werden, dass die Standardeinstellungen von SQL Server keine Remoteverbindungen zulassen. (Anbieter: TCP-Anbieter, Fehler: 0 - No such host is known. (Es ist kein solcher Host bekannt) (.Net SqlClient-Datenanbieter)|  
  
## <a name="explanation"></a>Erklärung  
Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client kann keine Verbindung mit dem Server herstellen. Der Fehler ist möglicherweise darauf zurückzuführen, dass entweder der Name des Servers durch den Client nicht aufgelöst werden kann oder der Name des Servers falsch ist.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass Sie den richtigen Servernamen auf dem Client eingegeben haben und dass Sie den Namen des Servers auf dem Client auflösen können. Zum Überprüfen der TCP/IP-Namensauflösung können Sie den **ping**-Befehl im Windows-Betriebssystem verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Netzwerkprotokolle und Netzwerkbibliotheken](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Client-Netzwerkkonfiguration](~/database-engine/configure-windows/client-network-configuration.md)  
[Konfigurieren von Clientprotokollen](~/database-engine/configure-windows/configure-client-protocols.md)  
[Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
