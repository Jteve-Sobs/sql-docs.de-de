---
title: SQL Server XTP-Phantomprozessor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba3422dacac62346012d5631fd036fe6a8a8ed93
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52159138"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP-Phantomprozessor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Das SQL Server-XTP-Leistungsobjekt „Phantomprozessor“ enthält Leistungsindikatoren, die sich auf den für das zur Phantomverarbeitung verwendete Subsystem der XTP-Engine beziehen. Diese Komponente ist dafür verantwortlich, Phantomzeilen in Transaktionen zu erkennen, die auf der SERIALIZABLE-Isolationsstufe ausgeführt werden sowie Einschränkungsvalidierung in Parallelitätsszenarios.  
  
 In dieser Tabelle werden die Leistungsindikatoren für **SQL Server-XTP-Phantomprozessor** beschrieben.  
  
|Leistungsindikator|und Beschreibung|  
|-------------|-----------------|  
|**Dusty-Corner-Scanwiederholungen/s (durch Phantom ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch den Phantomprozessor ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Entfernte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans entfernt werden.|  
|**Berührte abgelaufene Phantomzeilen/s**|Die durchschnittliche Anzahl abgelaufener Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte ablaufende Phantomzeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Berührte Phantomzeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von Phantomscans berührt werden.|  
|**Gestartete Phantomscans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Phantomscans.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
