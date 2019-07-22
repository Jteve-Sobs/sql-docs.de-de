---
title: Common Criteria-Konformität aktiviert (Konfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: craigg-msft
ms.author: craigg
ms.openlocfilehash: f072ed3e73b7dacd10254c04aaa34e5466b582b8
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262222"
---
# <a name="common-criteria-compliance-enabled-server-configuration"></a>Common Criteria-Kompatibilität aktiviert (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit der Option „“Common Criteria-Kompatibilität aktiviert“ werden die folgenden Elemente aktiviert, die für die [Common Criteria for Information Technology Security Evaluation](https://www.commoncriteriaportal.org/) erforderlich sind.  
  
|Kriterien|und Beschreibung|  
|--------------|-----------------|  
|RIP (Residual Information Protection)|Bei RIP muss eine Speicherbelegung mit einem bekannten Muster von Bits überschrieben werden, bevor der Arbeitsspeicher wieder einer neuen Quelle zugewiesen wird. Durch Einhalten des RIP-Standards kann die Sicherheit erhöht werden. Beim Überschreiben der Speicherbelegung kann jedoch die Leistung beeinträchtigt werden. Das Überschreiben wird erst ausgeführt, nachdem die Option Common Criteria-Kompatibilität aktiviert aktiviert wurde.|  
|Die Möglichkeit zum Anzeigen von Anmeldestatistiken|Die Anmeldungsüberwachung wird erst aktiviert, nachdem die Option Common Criteria-Kompatibilität aktiviert aktiviert wurde. Immer wenn sich ein Benutzer erfolgreich bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anmeldet, werden Informationen zum Zeitpunkt der letzten erfolgreichen Anmeldung, zum Zeitpunkt der letzten erfolglosen Anmeldung sowie zur Anzahl der Versuche zwischen dem Zeitpunkt der letzten erfolgreichen Anmeldung und dem der aktuellen Anmeldung bereitgestellt. Diese Anmeldestatistiken können angezeigt werden, indem die dynamische Verwaltungssicht [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md) abgefragt wird.|  
|`DENY` auf Tabellenebene sollte nicht durch `GRANT` auf Spaltenebene außer Kraft gesetzt werden|Nachdem die Option Common Criteria-Kompatibilität aktiviert wurde, hat `DENY` auf Tabellenebene Vorrang vor `GRANT` auf Spaltenebene. Wenn die Option nicht aktiviert ist, hat `GRANT` auf Spaltenebene Vorrang vor `DENY` auf Tabellenebene.|  
  
 Die Option „Common Criteria-Kompatibilität aktiviert“ ist eine erweiterte Option. Allgemeine Kriterien werden nur für die Enterprise Edition und die Datacenter Edition ausgewertet und zertifiziert. Informationen zum aktuellen Status der Common Criteria-Zertifizierung finden Sie auf der Website [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) (in Englisch).  
  
> [!IMPORTANT]  
>  Zusätzlich zur Aktivierung der Option Common Criteria-Kompatibilität aktiviert müssen Sie ein Skript herunterladen und ausführen, mit dem die Konfiguration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Kompatibilität mit der Common Criteria-Auswertungssicherungsstufe 4+ (EAL4+) ausgeführt wird. Sie können dieses Skript von der Website [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) (in Englisch) herunterladen.  
  
 Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur `sp_configure` ändern, können Sie die Option Common Criteria-Kompatibilität aktiviert nur ändern, wenn für Erweiterte Optionen anzeigen der Wert 1 festgelegt ist. Diese Einstellung wird wirksam, nachdem der Server neu gestartet wurde. Die möglichen Werte lauten 0 und 1:  
  
-   Mit 0 wird angegeben, dass die Common Criteria-Kompatibilität nicht aktiviert ist. Dies ist die Standardeinstellung.  
  
-   Mit 1 wird angegeben, dass die Common Criteria-Kompatibilität aktiviert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Common Criteria-Kompatibilität aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE WITH OVERRIDE; 
GO  
```  

Starten Sie [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] neu.
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)
