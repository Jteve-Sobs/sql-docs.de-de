---
description: dbo.sysjobservers (Transact-SQL)
title: dbo.sysjobservers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/26/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4df04c6a9564c2912f39173f71735162e7dc1cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427662"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Speichert die Zuordnung oder Beziehung eines bestimmten Auftrags zu einem oder mehreren Zielservern. Diese Tabelle wird in der msdb-Datenbank gespeichert.
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Identifikationsnummer des Auftrags.|  
|server_id|**int**|Die Server-ID.|  
|last_run_outcome|**tinyint**|Ergebnis der letzten Ausführung des Auftrags:<br /><br /> **0** = Fehler<br /><br /> **1** = erfolgreich<br /><br /> **2** = Wiederholung<br /><br /> **3** = Abbrechen<br /><br /> **4** = in Bearbeitung<br /><br /> **5** = unbekannt (siehe nachfolgenden Abschnitt "Hinweise") |  
|last_outcome_ message|**nvarchar(1024)**|Zugeordnete Meldung, falls vorhanden, zu der last_run_outcome-Spalte.|  
|last_run_date|**int**|Datum, an dem der Auftrag zuletzt ausgeführt wurde.|  
|last_run_time|**int**|Uhrzeit, zu der der Auftrag zuletzt ausgeführt wurde.|  
|last_run_duration|**int**|Dauer der Ausführung des Auftrags in Stunden, Minuten und Sekunden. Berechnet mithilfe der Formel: (*Stunden* \* 10000) + (*Minuten* \* 100) + *Sekunden*.|  


## <a name="remarks"></a>Bemerkungen

Ein Wert oberhalb von *4* bedeutet, dass der SQL-Agent den Status dieses Auftrags nicht kennt. Der *last_run_outcome* wird bei der Erstellung eines Auftrags anfänglich auf *5* festgelegt.


## <a name="see-also"></a>Weitere Informationen

[SQL Server-Agent Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
