---
title: LINKEDSERVERS-Rowset (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a0889b7a7dd7dd3c8f3afc1d61ee95acfcfb9fd5
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247149"
---
# <a name="schema-rowsets---linkedservers-rowset-in-sql-server-native-client"></a>Schemarowsets-LINKEDSERVERS-Rowset in SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Das **LINKEDSERVERS**-Rowset listet Organisationsdatenquellen auf, die an verteilten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Abfragen teilnehmen können.  
  
 Das **LINKEDSERVERS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|BESCHREIBUNG|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Name eines Verbindungsservers|  
|SVR_PRODUCT|DBTYPE_WSTR|Hersteller oder ein anderer Name, der den Typ des Datenspeichers identifiziert, der durch den Namen des Verbindungsservers repräsentiert wird.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Der Anzeigename des OLE DB-Anbieters, der Daten vom Server verwendet.|  
|SVR_DATASOURCE|DBTYPE_WSTR|OLE DB DBPROP_INIT_DATASOURCE-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|OLE DB DBPROP_INIT_PROVIDERSTRING-Wert, der verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_LOCATION|DBTYPE_WSTR|OLE DB DBPROP_INIT_LOCATION-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
  
 Das Rowset wird nach SRV_NAME sortiert, und eine einzelne Einschränkung wird für SRV_NAME unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Rowset Support &#40;OLE DB&#41; (Schemarowset-Unterstützung &#40;OLE DB&#41;)](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  
