---
title: LINKEDSERVERS-Rowset (OLE DB) | Microsoft-Dokumentation
description: LINKEDSERVERS-Rowset (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 75b443df235fd99f262cf3fda0abf6a6354da413
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67993880"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Schemarowsets: LINKEDSERVERS-Rowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Das **LINKEDSERVERS**-Rowset listet Organisationsdatenquellen auf, die an verteilten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Abfragen teilnehmen können.  
  
 Das **LINKEDSERVERS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Beschreibung|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Name eines Verbindungsservers|  
|SVR_PRODUCT|DBTYPE_WSTR|Hersteller oder ein anderer Name, der den Typ des Datenspeichers identifiziert, der durch den Namen des Verbindungsservers repräsentiert wird.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Der Anzeigename des OLE DB-Anbieters, der Daten vom Server verwendet.|  
|SVR_DATASOURCE|DBTYPE_WSTR|OLE DB DBPROP_INIT_DATASOURCE-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|OLE DB DBPROP_INIT_PROVIDERSTRING-Wert, der verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_LOCATION|DBTYPE_WSTR|OLE DB DBPROP_INIT_LOCATION-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
  
 Das Rowset wird nach SRV_NAME sortiert, und eine einzelne Einschränkung wird für SRV_NAME unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
