---
title: Abwärtskompatibilität von IIS Komponenten nicht wurden erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9cfae4d34ef825ac1781c90fda8d7e38c0299a1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094778"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>IIS-Abwärtskompatibilitätskomponenten wurden nicht erkannt (Upgrade Advisor)
  Upgrade Advisor hat keine IIS-Komponenten und -Einstellungen erkannt, die Informationen bereitstellen, mit denen Setup neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-URLs erstellt.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 IIS enthält Komponenten, die Informationen über die virtuellen Verzeichnisse des Berichtsservers und des Berichts-Managers bereitstellen. Diese Komponenten sind nicht auf dem Computer mit dem Berichtsserver installiert. Das Upgrade kann fortgesetzt werden, die URLs für den Berichtsserver oder den Berichts-Manager werden beim Upgrade jedoch nicht neu erstellt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach Abschluss des Upgrades das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, um die URLs für den Berichtsserver oder den Berichts-Manager festzulegen. Verwenden Sie IIS-Manager, um die virtuellen Verzeichnisse zu entfernen, die Sie nicht mehr benötigen.  
  
 Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
