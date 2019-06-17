---
title: Nur Benutzer mit Systemadministratorberechtigungen Protokolldateien für Auftragsschritte in das Dateisystem schreiben können | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84d04729e2f4c00c5d127a706727567c44855cd6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093683"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Nur Benutzer mit Systemadministratorberechtigungen können Protokolldateien für Auftragsschritte in das Dateisystem schreiben
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellt optional ein Protokoll für jeden Auftragsschritt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent kann die Protokolle schreiben, in das Dateisystem für Aufträge, die von einem Mitglied gehören die **Sysadmin** -Serverrolle sein. Ist der Besitzer des Auftrags kein Mitglied der **Sysadmin** Rolle und das Proxykonto aktiviert ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent kann Protokolle in das Dateisystem schreiben, mit den Anmeldeinformationen des Proxykontos.  
  
 Nach dem upgrade können Aufträge, die Benutzern gehören, die nicht Mitglied von der **Sysadmin** -Serverrolle kann nicht mehr Protokolle im Dateisystem schreiben. Stattdessen diese Benutzer können auswählen, die Möglichkeit, Schreiben ihre Protokolle in eine Tabelle in der **Msdb** Datenbank. Mitglieder der **Sysadmin** Rolle kann immer noch Protokolldateien in das Dateisystem schreiben.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Nach dem upgrade können Aufträge, die Benutzern gehören, die nicht Mitglied von der **Sysadmin** Rolle wird weiterhin ausgeführt, aber die Protokolle werden nicht erstellt werden. Auftragsschritte in eine Tabelle, die Benutzer anmelden, die nicht Mitglied von der **Sysadmin** Rolle muss ihre Aufträge manuell aktualisieren.  
  
 Weitere Informationen finden Sie in den Themen "Erstellen von Aufträgen", "Erstellen von Auftragsschritten" und "Handhaben mehrerer Auftragsschritte" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Probleme beim Upgrade des SQL Server-Agents](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
