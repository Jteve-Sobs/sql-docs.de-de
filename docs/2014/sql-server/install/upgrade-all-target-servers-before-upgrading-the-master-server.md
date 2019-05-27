---
title: Aktualisieren Sie alle Zielserver vor dem Upgrade des Masterservers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b6e08a384e20d64a7002171059db0d35dfd94a7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091465"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Durchführen eines Upgrades aller Zielserver vor dem Upgrade des Masterservers
  Führen Sie vor dem Upgrade des Masterservers ein Upgrade aller Computer aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen und als Zielserver konfiguriert sind.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 Um die Verwaltung in Multiserverumgebungen zu automatisieren, benötigen Sie mindestens einen Masterserver und mindestens einen Zielserver. Ein Masterserver verteilt Aufträge an die Zielserver und empfängt Ereignisse von ihnen. Auf dem Masterserver ist zudem die zentrale Kopie der Auftragsdefinitionen für Aufträge gespeichert, die auf Zielservern ausgeführt werden.  
  
 Wenn der aktuelle Server als Masterserver konfiguriert ist, führen Sie zuerst ein Upgrade aller Zielserver durch, bevor Sie den Masterserver aktualisieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie vor dem Upgrade des Masterservers nicht alle Zielserver aktualisieren können, müssen Sie alle Zielserver austragen und nach dem Upgrade wieder eintragen.  
  
 Weitere Informationen finden Sie in den Themen "Automatisieren der Verwaltung in einem Unternehmen," unter "Vorgehensweise: Vollziehen des Austritts eines Zielservers aus einem Masterserver"und" Vorgehensweise: Eintragen ein Zielservers bei einem Masterauftrag für den"im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme für SQL Server-Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Probleme beim Upgrade des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
