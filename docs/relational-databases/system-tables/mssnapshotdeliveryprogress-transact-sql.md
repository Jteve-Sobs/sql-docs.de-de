---
description: MSsnapshotdeliveryprogress (Transact-SQL)
title: MSsnapshotdeliveryprogress (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dd50e23578c8da3ca9d0e96a5ad7480f9af6acb4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454600"
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSsnapshotdeliveryprogress** -Tabelle dient zum Nachverfolgen von Dateien, die erfolgreich an den Abonnenten übermittelt wurden, wenn eine Momentaufnahme angewendet wird. Die Daten werden zum Fortsetzen der Dateiübermittlung verwendet, falls es dem Merge-Agent nicht gelingt, alle Dateien während einer Sitzung zu übermitteln. Dadurch wird erreicht, dass beim nächsten Ausführen des Merge-Agents nicht dieselben Dateien noch einmal übermittelt werden. Diese Tabelle wird auf dem Abonnenten in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|Identifiziert den Pfad zum Momentaufnahmeordner, von dem aus die Datei erfolgreich übermittelt wurde. Bei Veröffentlichungen, die parametrisierte Filter verwenden, wird die Zeichenfolge **dynsnap** an den Wert angehängt.|  
|**progress_token_hash**|**int**|Ein Hashwert, der auf Grundlage des Werts von *progress_token* generiert wird, der verwendet wird, um die Such Effizienz für einen bestimmten *progress_token* Wert zu verbessern.|  
|**progress_token**|**nvarchar (500)**|Identifiziert eine Datei, die erfolgreich übermittelt wurde, wobei der Wert sich aus einer Kombination des Dateinamens und des Pfads ergibt.|  
|**progress_timestamp**|**datetime**|Der **DateTime** -Wert, der angibt, wann eine Momentaufnahme Datei erfolgreich übermittelt wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
