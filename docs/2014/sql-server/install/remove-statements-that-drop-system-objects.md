---
title: Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1d420e2dba1dfdb284b0002eca6d8408c4e019e8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093075"
---
# <a name="remove-statements-that-drop-system-objects"></a>Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht werden
  Der Upgrade Advisor hat Anweisungen erkannt, die Systemobjekte löschen. Systemobjekte, einschließlich der erweiterte gespeicherte Prozeduren, werden bereitgestellt, in der schreibgeschützten **Ressource** (Mssqlsystemresource)-Datenbank und kann nicht gelöscht werden. Ändern Sie Ihre Anwendungen, sodass sie EXECUTE-Berechtigungen für Systemobjekte aufheben oder verweigern.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Anweisungen wie DROP TABLE, DROP PROCEDURE und **Sp_dropextendedproc** nicht zum Entfernen von Systemobjekten, verwendet werden, da diese Objekte in der schreibgeschützten bereitgestellt werden **Ressource** Datenbank.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie alle Anweisungen, mit denen Systemobjekte aus Ihren Anwendungen gelöscht werden. Ändern Sie Ihre Anwendungen, sodass sie EXECUTE-Berechtigungen für Systemobjekte aufheben oder verweigern. Alternativ können Sie auch das Tool zur Oberflächenkonfiguration (Surface Area Configuration, SAC) verwenden, um einige dieser Objekte zu deaktivieren. Z. B. die **Xp_cmdshell** erweiterte gespeicherte Prozedur kann deaktiviert werden, oder mit dem SAC-Tool aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
