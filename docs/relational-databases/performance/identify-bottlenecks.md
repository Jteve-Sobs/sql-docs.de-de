---
title: Identifizieren von Engpässen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 213df75d1883de730a0231c009f1d178814ed463
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62636304"
---
# <a name="identify-bottlenecks"></a>Identifizieren von Engpässen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Der gleichzeitige Zugriff auf freigegebene Ressourcen verursacht Engpässe. Im Allgemeinen entstehen Engpässe in jedem Softwaresystem und sind unvermeidlich. Eine überhöhte Nachfrage nach freigegebenen Ressourcen führen jedoch zu einer schlechten Antwortzeit. Dieses Situation muss identifiziert und optimiert werden.  
  
 Mögliche Ursachen für Engpässe:  
  
-   Unzureichende Ressourcen, wodurch zusätzliche oder aktualisierte Komponenten notwendig werden.  
  
-   Ressourcen desselben Typs, auf die die Arbeitsauslastung nicht gleichmäßig verteilt wird (z. B., wenn ein Datenträger monopolisiert wird).  
  
-   Fehlerhaft funktionierende Ressourcen.  
  
-   Falsch konfigurierte Ressourcen.  
  
## <a name="analyzing-bottlenecks"></a>Analysieren von Engpässen  
 Sehr lange Ausführungszeiten für verschiedene Ereignisse sind Anzeichen von Engpässen, die optimiert werden können.  
  
 Beispiel:  
  
-   Eine andere Komponente verhindert, dass die Arbeitsauslastung diese Komponente erreicht, wodurch die erforderliche Zeit zum Verarbeiten der Arbeitsauslastung zunimmt.  
  
-   Clientanforderungen können aufgrund einer Netzwerküberlastung länger dauern.  
  
 Es gibt die folgenden fünf Schlüsselbereiche, die Sie überwachen sollten, um die Serverleistung nachzuverfolgen und Engpässe zu identifizieren.  
  
|Mögliche Bereiche für Engpässe|Auswirkungen auf den Server|  
|------------------------------|---------------------------|  
|Speicherauslastung|Ein für Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unzureichender Arbeitsspeicherumfang beeinträchtigt die Leistung. Die Daten müssen vom Datenträger gelesen werden, anstatt direkt aus dem Datencache. Microsoft Windows-Betriebssysteme lagern zu häufig aus, indem Daten vom Datenträger hin und her übertragen werden, wenn die Seiten benötigt werden.|  
|CPU-Auslastung|Eine konstant hohe CPU-Auslastungsrate kann ein Hinweis darauf sein, dass [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen optimiert werden müssen oder dass ein CPU-Upgrade erforderlich ist.|  
|Datenträger-E/A|[!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen können optimiert werden, um unnötige E/A zu reduzieren. Dies geschieht beispielsweise durch die Verwendung von Indizes.|  
|Benutzerverbindungen|Möglicherweise greifen zu viele Benutzer gleichzeitig auf den Server zu, wodurch die Leistung beeinträchtigt wird.|  
|Blockierende Sperren|Fehlerhaft entworfene Anwendungen können zu Sperren führen und behindern die Parallelität, wodurch sich längere Antwortzeiten und niedrigere Durchsatzraten für Transaktionen ergeben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der CPU-Auslastung](../../relational-databases/performance-monitor/monitor-cpu-usage.md)   
 [Überwachen der Datenträgerverwendung](../../relational-databases/performance-monitor/monitor-disk-usage.md)   
 [Überwachen der Speicherauslastung](../../relational-databases/performance-monitor/monitor-memory-usage.md)   
 [SQL Server, Allgemeine Statistik-Objekt](../../relational-databases/performance-monitor/sql-server-general-statistics-object.md)   
 [SQL Server, Sperren-Objekt](../../relational-databases/performance-monitor/sql-server-locks-object.md)  
  
  
