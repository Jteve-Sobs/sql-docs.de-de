---
title: Festlegen der Leerlaufzeit und Leerlaufdauer der CPU (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a355108635799d03c2859b6c47eaaf8acc87dc7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764222"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Festlegen der Leerlaufzeit und Leerlaufdauer der CPU (SQL Server Management Studio)
  In diesem Thema wird erläutert, wie Sie die CPU-Leerlaufbedingung für den Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]definieren. Die CPU-Leerlaufdefinition beeinflusst die Reaktion des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents auf Ereignisse. Nehmen wir beispielsweise an, dass Sie die CPU als im Leerlauf befindlich definieren, wenn die durchschnittliche CPU-Auslastung unter 10 Prozent fällt und für 10 Minuten auf dieser Stufe bleibt. Wenn Sie Aufträge definiert haben, die immer dann ausgeführt werden sollen, wenn die Server-CPU eine Leerlaufbedingung erfüllt, wird der Auftrag gestartet, wenn die CPU-Auslastung unter 10 Prozent fällt und für 10 Minuten auf dieser Stufe bleibt. Wenn es sich dabei um einen Auftrag handelt, der sich spürbar auf die Serverleistung auswirkt, ist die Art wichtig, wie Sie die CPU-Leerlaufbedingung definieren.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>So legen Sie die Leerlaufzeit und die Leerlaufdauer der CPU fest  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, klicken Sie auf **Eigenschaften**, und wählen Sie dann die Seite **Erweitert** aus.  
  
3.  Führen Sie unter **Bedingung für 'CPU im Leerlauf'** eine der folgenden Aktionen aus :  
  
    -   Aktivieren Sie **Bedingung für 'CPU im Leerlauf' definieren**.  
  
    -   Geben Sie einen Prozentsatz für das Feld **Bei durchschnittlicher CPU-Nutzung unter** (für alle CPUs) an. Damit wird die Auslastungsgrenze festgelegt, unterhalb der die CPU als im Leerlauf befindlich angesehen wird.  
  
    -   Geben Sie einen Wert für Sekunden im Feld **und Verbleiben unterhalb dieser Stufe für** an. Damit wird die Dauer der minimalen CPU-Auslastung angegeben, bevor die CPU als im Leerlauf befindlich angesehen wird.  
  
  
