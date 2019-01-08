---
title: Database Mail XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e916fe3b76abfa8773a757cf2779e7d5cbf26b86
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640781"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs (Serverkonfigurationsoption)
  Verwenden Sie die Option **DatabaseMail XPs** , um Datenbank-E-Mail auf diesem Server zu aktivieren. Die folgenden Werte sind möglich:  
  
-   **0** gibt an, dass Datenbank-E-Mail nicht verfügbar ist (Standard).  
  
-   **1** gibt an, dass Datenbank-E-Mail verfügbar ist.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
 Nachdem Sie Datenbank-E-Mail aktiviert haben, müssen Sie zum Verwenden von Datenbank-E-Mail eine Hostdatenbank für Datenbank-E-Mail konfigurieren.  
  
 Durch das Konfigurieren von Datenbank-E-Mail mithilfe des **Assistenten zum Konfigurieren von Datenbank-E-Mail** werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail in der **msdb** -Datenbank aktiviert. Wenn Sie den **Assistenten zum Konfigurieren von Datenbank-E-Mail**verwenden, müssen Sie das unten angeführte **sp_configure** -Beispiel nicht verwenden.  
  
 Das festlegen der Option **Database Mail XPs** auf 0 verhindert das Starten von Datenbank-E-Mail. Wird Datenbank-E-Mail mit dem Wert 0 ausgeführt, wird die Ausführung und das Senden von E-Mails bis zur in der Option **DatabaseMailExeMinimumLifeTime** konfigurierten Leerlaufzeit fortgesetzt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
