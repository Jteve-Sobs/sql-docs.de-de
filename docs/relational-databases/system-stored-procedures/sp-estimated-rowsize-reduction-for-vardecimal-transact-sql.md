---
title: Sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0d7f088d85a5a56a6440266bd9851cbd90c9c0f9
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590454"
---
# <a name="spestimatedrowsizereductionforvardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Schätzt die Verringerung der durchschnittlichen Zeilengröße ab, wenn Sie das vardecimal-Speicherformat für eine Tabelle aktivieren. Verwenden Sie diese Zahl, um die Gesamtverringerung der Tabellengröße abzuschätzen. Da zur Berechnung der durchschnittlichen Verringerung der Zeilengröße die Stichprobenuntersuchung verwendet wird, betrachten Sie dies nur als Schätzung. In seltenen Fällen kann sich die Zeilengröße erhöhen, nachdem Sie das vardecimal-Speicherformat aktiviert haben.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die ROW-Komprimierung und die PAGE-Komprimierung. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md). Auswirkung einer Komprimierung auf die Größe von Tabellen und Indizes, finden Sie unter [Sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@table=** ] **"**_Tabelle_**"**  
 Der dreiteilige Name der Tabelle, für die das Speicherformat geändert wird. *Tabelle* ist **nvarchar(776)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Das folgende Resultset wird zurückgegeben, damit Informationen zur aktuellen und geschätzten Tabellengröße bereitgestellt werden.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**Decimal ("12", "2")**|Stellt die Länge der Zeile im festen Dezimalspeicherformat dar.|  
|**avg_rowlen_vardecimal_format**|**Decimal ("12", "2")**|Stellt die durchschnittliche Zeilengröße dar, wenn das vardecimal-Speicherformat verwendet wird.|  
|**row_count**|**int**|Anzahl der Zeilen in der Tabelle|  
  
## <a name="remarks"></a>Hinweise  
 Verwendung **Sp_estimated_rowsize_reduction_for_vardecimal** können Sie die einsparungen abschätzen, die sich ergeben, wenn Sie eine Tabelle das Vardecimal-Speicherformat aktivieren. Wenn beispielsweise die durchschnittliche Größe der Zeile um 40 % verringert werden kann, können Sie die Größe der Tabelle potenziell um 40 % verringern. Möglicherweise erhalten Sie keine Platzeinsparung; dies hängt vom Füllfaktor und von der Zeilengröße ab. Wenn es sich beispielsweise um eine Zeile handelt, die 8000 Bytes lang ist, und Sie die Größe um 40 % verringern, passt weiterhin nur eine Zeile auf eine Datenseite, was zu keiner Einsparung führt.  
  
 Wenn die Ergebnisse der **Sp_estimated_rowsize_reduction_for_vardecimal** anzugeben, dass die Tabelle vergrößert, dies bedeutet, dass viele Zeilen in der Tabelle fast die gesamte Genauigkeit der dezimaldatentypen verwendet und die Addition des kleinen verwenden. zusätzliche Verarbeitungsaufwand für das Vardecimal-Speicherformat ist größer als die einsparungen durch die vardecimal-Speicherformat. Aktivieren Sie in diesem seltenen Fall das vardecimal-Speicherformat nicht.  
  
 Wenn eine Tabelle das Vardecimal-Speicherformat aktiviert ist, verwenden Sie **Sp_estimated_rowsize_reduction_for_vardecimal** um die durchschnittliche Größe der Zeile zu schätzen, wenn das Vardecimal-Speicherformat deaktiviert ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Tabelle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Verringerung der Zeilengröße abgeschätzt, wenn die `Production.WorkOrderRouting`-Tabelle in der `AdventureWorks2012`-Datenbank komprimiert wird.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
