---
title: Winsockproxykonfiguration nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Winsock proxy configuration [SQL Server]
ms.assetid: abf71f7b-8bd7-49d2-92f7-9ddf72924d8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e9f73710f1cdb13477736d3b7496fb26b76f90e3
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583203"
---
# <a name="winsock-proxy-configuration-not-supported"></a>Winsockproxykonfiguration nicht unterstützt
  Der Winsockproxy kann nicht konfiguriert werden, mithilfe von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tools.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tools können keine Windows-Komponenten konfigurieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie Microsoft Internet Security and Acceleration (ISA) Server, um einen Computer zu veröffentlichen. Weitere Informationen zum Konfigurieren von Winsockproxy finden Sie in Ihrer Proxyserverdokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
