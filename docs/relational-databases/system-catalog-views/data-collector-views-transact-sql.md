---
title: Sichten des Datensammlers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- data collector [SQL Server], views
ms.assetid: a005e885-7813-4c7e-b332-b01d9e9d4054
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9e412f796a5b04f980557b5a3131763811aa78da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033169"
---
# <a name="data-collector-views-transact-sql"></a>Sichten des Datensammlers (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Der Datensammler bietet die folgenden Sichten, in denen Informationen zur Konfiguration des Datensammlers, beispielsweise Eigenschaften des Sammlertyps, Sammlungssätze und Elemente in Sammlungssätzen, sowie Ausführungsstatistiken, die bei der Ausführung eines Sammlungssatzes abgerufen werden, angezeigt werden können. Diese Ansichten, mit denen in der **Msdb** Datenbank befinden, stellen auch eine Abstraktionsebene für die zugrunde liegenden Tabellen. Diese Abstraktion erhöht die Sicherheit durch direkten Zugriff auf die Tabellen, zugleich Änderungen an den Tabellen ohne Auswirkungen auf die zugeordneten Anwendungen zu verhindern.  
  
|||  
|-|-|  
|[syscollector_collection_items &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)|[syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)|  
|[syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)|[syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)|  
|[syscollector_execution_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)|[syscollector_execution_log_full &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)|  
|[syscollector_execution_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)||  
  
## <a name="see-also"></a>Siehe auch  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
