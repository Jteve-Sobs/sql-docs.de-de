---
title: MSSQLSERVER_7987 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7987 (Database Engine error)
ms.assetid: 314aebf1-6cdf-488d-a274-ce967fadb57b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0541f066c653a233508a48d7b8f02504d36f25b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913277"
---
# <a name="mssqlserver7987"></a>MSSQLSERVER_7987
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7987|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_PRE_CHECKS_CHAIN_LINKAGE_MISMATCH|  
|Meldungstext|Vorabüberprüfungen für Systemtabelle: Objekt-ID O_ID besitzt eine nicht übereinstimmende kettenverknüpfung. P_ID1->next = P_ID2, aber P_ID2->prev = P_ID3. Die CHECK-Anweisung wurde aufgrund eines irreparablen Fehlers beendet.|  
  
## <a name="explanation"></a>Erklärung  
 Die erste Phase eines DBCC CHECKDB beinhaltet einfache Überprüfungen der Datenseiten kritischer Systemtabellen. Gefundene Fehler können nicht repariert werden. Daher wird DBCC CHECKDB sofort beendet.  
  
 Der Zeiger für die nächste Seite der Seite *P_ID1* zeigt auf die Seite *P_ID2*. Der Zeiger für die vorherige Seite von Seite *P_ID2* zeigt jedoch auf die Seite *P_ID3*, aber nicht zurück auf die Seite *P_ID1*, wie er es sollte.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht verfügbar. Dieser Fehler kann nicht automatisch repariert werden. Wenn Sie die Datenbank nicht von einer Sicherung wiederherstellen können, wenden Sie sich an den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support Services (CSS).  
  
  
