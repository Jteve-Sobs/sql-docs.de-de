---
title: Neuerungen bei der CLR-Integration | Microsoft-Dokumentation
description: Microsoft SQL Server Hosting von CLR wird als CLR-Integration bezeichnet. In diesem Artikel werden neue Funktionen in der CLR-Integration in SQL Server 2012 beschrieben.
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: dfa53b1f40402189a6dc7c316d3d366addbab963
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789603"
---
# <a name="clr-integration---what39s-new"></a>CLR-Integration-What&#39;s new
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können weiterhin von den CLR-Datenbankkomponenten abgefangen werden, indem ein Code-Attribut (-[ \<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)) festgelegt wird. Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR, Version 4, generiert ein Format Fehler in einem **System. TimeSpan** -Wert **System. FormatExceptions**. Vor Version 4 der CLR wurde ein Format Fehler in einem **System. TimeSpan** -Wert ignoriert. Datenbankanwendungen, die auf dem Verhalten vor Version 4 der CLR basieren, sollten mit einem Datenbank-Kompatibilitäts Grad (**ALTER DATABASE-Kompatibilitäts Grad**) von 100 oder niedriger ausgeführt werden. Weitere Informationen finden Sie unter [<TimeSpan_LegacyFormatMode>-Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. Um die Legacy Sortierung zu aktivieren, muss der Datenbank-Kompatibilitäts Grad (**ALTER DATABASE-Kompatibilitäts Grad**) auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [\<CompatSortNLSVersion>Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten wurden zu [sys. dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)hinzugefügt: **total_processor_time_ms**, **total_allocated_memory_kb**und **survived_memory_kb**.  
  
  
