---
title: SQL Server 2005 Report Server Web Service Group erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4f379675a4d7b37b9eab69598f7c04bc57306d46
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092110"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Berichtsserver-Webdienstgruppe von SQL Server 2005 erkannt (Upgrade Advisor)
  Upgrade Advisor hat erkannt, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz zugeordnet ist eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Berichtsserver-webdienstgruppe.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet nicht die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Berichtsserver-webdienstgruppe. Beim Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird diese Dienstgruppe gelöscht, und benutzerdefinierte Zugriffssteuerungslisten (Access Control Lists, ACLs) für diese Gruppe oder für Benutzer in dieser Gruppe werden nicht beibehalten.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sichern Sie vor dem Upgrade ggf. alle benutzerdefinierten ACLs oder Benutzer, die der Berichtsserver-Webdienstgruppe von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] angehören. Zu diesem Zweck können Sie die **Icacls.exe** Befehlszeilentool in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 und höher oder das Befehlszeilentool Cacls.exe in Windows-Betriebssystemen vor [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Weitere Informationen zur Syntax für diese Tools finden Sie in der Windows-Produktdokumentation. Wenden Sie nach dem erfolgreichen Abschluss der Installation die benutzerdefinierten ACLs oder Benutzer auf die Berichtsserver-Windows-Gruppe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für Ihre Berichtsserverinstanz an. Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server-Windows-Gruppe von hat das Format SQLServerReportServerUser$\<*Computer_name*>$\<*Instance_name*>.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
