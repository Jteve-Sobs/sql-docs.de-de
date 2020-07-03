---
title: sys. fn_cdc_get_max_lsn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn_TSQL
- sys.fn_cdc_get_max_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_max_lsn
- sys.fn_cdc_get_max_lsn
ms.assetid: 93f3a4c8-b91f-4ebb-8e96-9397bb3a1c43
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c1c1efe2659ff0e127a1347e911c3f3da18908c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898425"
---
# <a name="sysfn_cdc_get_max_lsn-transact-sql"></a>sys.fn_cdc_get_max_lsn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die maximale Protokoll Folge Nummer (Log Sequence Number, LSN) aus der start_lsn Spalte in der [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) -Systemtabelle zurück. Mithilfe dieser Funktion können Sie den oberen Endpunkt der Change Data Capture-Zeitachse für jede Aufzeichnungsinstanz zurückgeben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_cdc_get_max_lsn ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **binary(10)**  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt die maximale LSN in der start_lsn-Spalte der [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) -Tabelle zurück. Es handelt sich entsprechend um die letzte LSN, die vom Aufzeichnungsprozess verarbeitet wurde, als Änderungen an die Datenbank-Änderungstabellen weitergegeben wurden. Sie wird auch als oberer Endpunkt für alle Zeitachsen verwendet, die den für die Datenbank definierten Aufzeichnungsinstanzen zugeordnet sind.  
  
 Die Funktion wird meist verwendet, um einen geeigneten oberen Endpunkt für ein Abfrageintervall zu erhalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-maximum-lsn-value"></a>A. Zurückgeben des höchsten LSN-Werts  
 Im folgenden Beispiel wird die höchste LSN für alle Aufzeichnungsinstanzen in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Datenbank zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT sys.fn_cdc_get_max_lsn()AS max_lsn;  
```  
  
### <a name="b-setting-the-high-endpoint-of-a-query-range"></a>B. Festlegen des oberen Endpunkts eines Abfragebereichs  
 Im folgenden Beispiel wird die höchste von `sys.fn_cdc_get_max_lsn` zurückgegebene LSN verwendet, um den oberen Endpunkt für einen Abfragebereich für die `HumanResources_Employee`-Aufzeichnungsinstanz festzulegen.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn(N'HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fn_cdc_get_min_lsn &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
