---
title: sys. dm_pdw_hadoop_operations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6378ddd4b0604fabe81d669d272b59207781fdf8
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197077"
---
# <a name="sysdm_pdw_hadoop_operations-transact-sql"></a>sys. dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält eine Zeile für jeden Map-Reduce-Auftrag, der als Teil der Ausführung einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Abfrage für eine externe Hadoop-Tabelle an Hadoop übermittelt wird. Jeder Map-Reduce-Auftrag stellt einen der Prädikate in der Abfrage dar. Diese Option wird nur verwendet, wenn die Prädikat Weitergabe für Abfragen für externe Hadoop-Tabellen aktiviert ist.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID für diesen externen Hadoop-Vorgang.|Identisch mit der ID in [sys. dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Index des Abfrage Schritts, der auf diesen Hadoop-Vorgang verweist.|Identisch mit step_index in [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Beschreibt den Typ des externen Vorgangs.|"Externer Hadoop-Vorgang"|  
|operation_name|**nvarchar(4000)**|Die Auftrags-ID für einen Map-Reduce-Auftrag. Dies wird von Hadoop zurückgegeben, nachdem [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] der Auftrag übermittelt wurde.||  
|map_progress|**float**|Der Prozentsatz der Eingabedaten, die bisher vom Zuordnungs Auftrag verarbeitet wurden.|Eine Gleit Komma Zahl zwischen und einschließlich, 0 und 100.|  
|reduce_progress|**int**|Der Prozentsatz des abgeschlossenen Reduzierungs Auftrags.|Eine Gleit Komma Zahl zwischen und einschließlich, 0 und 100.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
