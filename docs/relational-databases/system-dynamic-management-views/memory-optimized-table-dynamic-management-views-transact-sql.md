---
title: Dynamische Verwaltungs Sichten für Speicher optimierte Tabellen (Transact-SQL)
description: Erfahren Sie mehr über die SQL Server dynamischen Verwaltungs Sichten und Objektkatalog Sichten, die mit in-Memory-OLTP in SQL Server verwendet werden.
ms.custom: seo-dt-2019
ms.date: 02/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ccd82fed-1a3f-47de-85c4-1c9bdd80b027
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2cbcc1bfb022f213295f5c3c37d78be4935fbf48
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442519"
---
# <a name="memory-optimized-table-dynamic-management-views-transact-sql"></a>Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)
[!INCLUDE[sql-asdb-asdbmi](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  Die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dynamischen Verwaltungs Sichten (Dynamic Management Views, DMVs) werden mit in-Memory-OLTP verwendet:  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  

:::row:::
    :::column:::
        [sys. dm_db_xtp_checkpoint_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md)

        [sys. dm_db_xtp_gc_cycle_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md)

        [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)

        [sys.dm_db_xtp_merge_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-merge-requests-transact-sql.md)

        [sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)

        [sys. dm_db_xtp_transactions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-transactions-transact-sql.md)

        [sys. dm_xtp_gc_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md)

        [sys. dm_xtp_transaction_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-transaction-stats-transact-sql.md)
    :::column-end:::
    :::column:::
        [sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md)

        [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)

        [sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)

        [sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)

        [sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)

        [sys. dm_xtp_gc_queue_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)

        [sys. dm_xtp_system_memory_consumers &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-system-memory-consumers-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="object-catalog-views"></a>Katalogsichten für Objekte

Die folgenden Objektkatalog Sichten werden speziell mit in-Memory OLTP verwendet.

:::row:::
    :::column:::
        [sys.hash_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md)
    :::column-end:::
    :::column:::
        [sys.memory_optimized_tables_internal_attributes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-memory-optimized-tables-internal-attributes-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="internal-dmvs"></a>Interne DMVs

Es gibt zusätzliche DMVs, die nur für die interne Verwendung vorgesehen sind und für die wir keine direkte Dokumentation bereitstellen. Im Bereich Speicher optimierter Tabellen umfassen nicht dokumentierte DMVs Folgendes:

- sys. dm_xtp_threads
- sys. dm_xtp_transaction_recent_rows

