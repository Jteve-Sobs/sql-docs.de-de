---
title: SQL Server, Sicherungsmedium-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 30371a600f59801710ce27db084f887eeb1727e0
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158978"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, Sicherungsmedium-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Das **Sicherungsmedium** -Objekt stellt Leistungsindikatoren bereit, die mit denen für Sicherungs- und Wiederherstellungsvorgänge verwendeten Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungsmedien überwacht werden können. Überwachen Sie Sicherungsmedien, wenn Sie den Durchsatz oder den Fortschritt und die Leistung der Sicherungs- und Wiederherstellungsvorgänge auf jedem Medium einzeln bestimmen möchten. Wenn Sie den Durchsatz des gesamten Sicherungs- oder Wiederherstellungsvorgangs der Datenbank überwachen möchten, sollten Sie den **Sicherungs-/Wiederherstellungsdurchsatz/Sekunde** -Leistungsindikator des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. Weitere Informationen finden Sie unter [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md).  
  
 In dieser Tabelle wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Sicherungsmedium** beschrieben.  
  
|Sicherungsmedium-Leistungsindikatoren von SQL Server|und Beschreibung|  
|---------------------------------------|-----------------|  
|**Mediumsdurchsatz Bytes/Sekunde**|Durchsatz von Lese-/Schreibvorgängen für ein Sicherungsmedium. Dieser Leistungsindikator ist nur vorhanden, während der Sicherungs- oder Wiederherstellungsvorgang ausgeführt wird.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
