---
title: Fn_syscollector_get_execution_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_syscollector_get_execution_details_TSQL
- fn_syscollector_get_execution_details
dev_langs:
- TSQL
helpviewer_keywords:
- fn_syscollector_get_execution_details function
ms.assetid: d59ddf0c-72c0-4c57-bc83-aef260e4e105
author: rothja
ms.author: jroth
ms.openlocfilehash: b2ed385026d2bd47912a1a95d237b2adedafa26d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042820"
---
# <a name="fnsyscollectorgetexecutiondetails-transact-sql"></a>fn_syscollector_get_execution_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt einen Teil der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Protokolls (Sysssislog) Übereinstimmung mit der Package_execution_id für das angegebene Paket. Die Tabelle enthält eine Zeile für jeden Protokollierungseintrag, der zur Laufzeit von Paketen oder deren Tasks und Containern generiert wird.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_syscollector_get_execution_details ( log_id )  
```  
  
## <a name="arguments"></a>Argumente  
 *log_id*  
 Der lokale eindeutige Bezeichner für das Ausführungsprotokoll. *log_id* ist **int**  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|id|**int**|Der eindeutige Bezeichner des Protokollierungseintrags.|  
|Ereignis|**sysname**|Der Name des Ereignisses, das den Protokollierungseintrag generiert hat.|  
|computer|**nvarchar**|Der Computer, auf dem das Paket ausgeführt wurde, als der Protokollierungseintrag generiert wurde.|  
|Operator|**nvarchar**|Der Benutzername der Person oder des Agents, die bzw. der das Paket ausgeführt hat, das den Protokollierungseintrag generiert hat.|  
|Quelle|**nvarchar**|Der Name der ausführbaren Datei, die den Protokollierungseintrag generiert hat.|  
|sourceid|**uniqueidentifier**|GUID der ausführbaren Datei, die den Protokollierungseintrag generiert hat.|  
|executionid|**uniqueidentifier**|GUID der Ausführungsinstanz der ausführbaren Datei, die den Protokollierungseintrag generiert hat.|  
|starttime|**datetime**|Die Uhrzeit, zu der die Paketausführung gestartet wurde.|  
|endtime|**datetime**|Die Uhrzeit, zu der das Paket abgeschlossen wurde.|  
|datacode|**int**|Ein ganzzahliger Wert, der das dem Protokolleintrag zugeordnete Ereignis angibt. "0" gibt an, dass das Ereignis keinen Bezeichner bereitgestellt hat.|  
|databytes|**image**|Ein Bytearray, das einen Rückgabewert identifiziert.|  
|message|**nvarchar**|Eine Beschreibung des Ereignisses sowie die mit dem Ereignis verknüpften Informationen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die SELECT-Berechtigung für **dc_operator**.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren der Paketprotokollierung in SQL Server Data Tools](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
