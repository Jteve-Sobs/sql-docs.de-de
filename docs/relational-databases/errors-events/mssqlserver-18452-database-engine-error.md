---
description: MSSQLSERVER_18452
title: MSSQLSERVER_18452 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0704998c40476ae040d3f8263ab3a47b1817f1e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88385656"
---
# <a name="mssqlserver_18452"></a>MSSQLSERVER_18452
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|18452|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOGON_INVALID_CONNECT|  
|Meldungstext|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Die Anmeldung ist eine SQL Server-Anmeldung und kann nicht mit der Windows-Authentifizierung verwendet werden.%.\*ls|  
  
## <a name="explanation"></a>Erklärung  
Der Benutzer hat versucht, sich mit Anmeldeinformationen anzumelden, die nicht überprüft werden können. Mögliche Ursachen sind:  
  
-   Die Anmeldung ist möglicherweise eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung, aber der Server akzeptiert nur Windows-Authentifizierung.  
  
-   Sie versuchen, eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung herzustellen, aber die Anmeldeinformationen sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht vorhanden.  
  
-   Die Anmeldung verwendet möglicherweise die Windows-Authentifizierung, aber die Anmeldung ist ein nicht erkannter Windows-Prinzipal. Ein nicht erkannter Windows-Prinzipal bedeutet, dass die Anmeldung nicht von Windows überprüft werden kann. Das konnte daran liegen, dass die Windows-Anmeldung von einer nicht vertrauenswürdigen Domäne stammt.  
  
Ähnliche Probleme können den weniger spezifischen Fehler 18456 verursachen.  
  
## <a name="user-action"></a>Benutzeraktion  
Wenn Sie versuchen, eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung herzustellen, überprüfen Sie, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im gemischten Authentifizierungsmodus konfiguriert ist.  
  
Wenn Sie versuchen, eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung herzustellen, überprüfen Sie, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldeinformationen vorhanden sind.  
  
Wenn Sie versuchen, eine Verbindung mit Windows-Authentifizierung herzustellen, überprüfen Sie, dass Sie ordnungsgemäß bei der richtigen Domäne angemeldet sind.  
  
