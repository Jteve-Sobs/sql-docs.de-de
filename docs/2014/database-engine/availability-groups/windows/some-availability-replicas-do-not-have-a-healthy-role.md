---
title: Einige Verfügbarkeitsreplikate haben keine fehlerfreie Rolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 50518e78585b7e56f62411edc539d0f9ac3db9e9
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360304"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a>Einige Verfügbarkeitsreplikate haben keine fehlerfreie Rolle
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Verfügbarkeitsreplikat-Rollenstatus|  
|**Problem**|Einige Verfügbarkeitsreplikate haben keine fehlerfreie Rolle.|  
|**Kategorie**|**Warnung**|  
|**Facet**|Verfügbarkeitsgruppe|  
  
## <a name="description"></a>Description  
 Diese Richtlinie führt ein Rollup des Verbindungsstatus aller Verfügbarkeitsreplikate aus und überprüft, ob Verfügbarkeitsreplikate vorhanden sind, die keine fehlerfreie Rolle aufweisen. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn jedes Verfügbarkeitsreplikat weder primär noch sekundär ist. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Einige Verfügbarkeitsreplikate haben keine fehlerfreie Rolle](https://go.microsoft.com/fwlink/p/?LinkId=220854) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 In dieser Verfügbarkeitsgruppe verfügt mindestens ein Verfügbarkeitsreplikat derzeit nicht über die primäre oder sekundäre Rolle.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie den Verfügbarkeitsreplikat-Richtlinienstatus, um nach dem Verfügbarkeitsreplikat zu suchen, dessen Rolle nicht primär oder sekundär ist, und beheben Sie das Problem des Verfügbarkeitsreplikats.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
