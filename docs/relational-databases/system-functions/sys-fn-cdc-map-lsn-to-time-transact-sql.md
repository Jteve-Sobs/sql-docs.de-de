---
title: fn_cdc_map_lsn_to_time (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_lsn_to_time_TSQL
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time_TSQL
- fn_cdc_map_lsn_to_time
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time
ms.assetid: 405aa29c-8bd8-42d3-9f39-7494b643fc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c3573b876a10b4400969bf63200682e91bfc45fb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046346"
---
# <a name="sysfncdcmaplsntotime-transact-sql"></a>sys.fn_cdc_map_lsn_to_time (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt für die angegebene Protokollfolgenummer (Log Sequence Number, LSN) den Datums- und Uhrzeitwert aus der **tran_end_time** -Spalte in der [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) -Systemtabelle zurück. Sie können diese Funktion verwenden, um die LSN-Bereiche den Datumsbereichen in der Änderungstabelle systematisch zuzuordnen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_cdc_map_lsn_to_time ( lsn_value )  
```  
  
## <a name="arguments"></a>Argumente  
 *lsn_value*  
 Der LSN-Wert, mit dem verglichen werden soll. *lsn_value* ist **binary(10)**  
  
## <a name="return-type"></a>Rückgabetyp  
 **datetime**  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann verwendet werden, um auf Basis des in der Änderungsdatenzeile zurückgegebenen **__$start_lsn** -Werts den Zeitpunkt zu bestimmen, zu dem für die Änderung ein Commit erfolgte.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe der `sys.fn_cdc_map_lsn_to_time` -Funktion die Commitzeit bestimmt, die mit der letzten Änderung verknüpft ist, die im angegebenen LSN-Intervall für die `HumanResources_Employee` -Aufzeichnungsinstanz verarbeitet wurde.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @max_lsn binary(10);  
SELECT @max_lsn = MAX(__$start_lsn)  
FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
SELECT sys.fn_cdc_map_lsn_to_time(@max_lsn);  
GO   
```  
  
## <a name="see-also"></a>Siehe auch  
 [cdc.lsn_time_mapping &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
