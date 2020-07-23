---
title: Zeilen Lesezeichen (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 149f40d2bc6ddb9313c7e20b76fb6ec7738cd5ce
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942152"
---
# <a name="bookmarks"></a>Lesezeichen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Lesezeichen ermöglichen es Consumern, schnell zu einer Zeile zurückzukehren. Mit Lesezeichen können Consumer auf der Grundlage des Lesezeichenwerts beliebig auf Zeilen zugreifen. Die Lesezeichenspalte ist die Spalte 0 (null) im Rowset. Der Consumer legt den Wert des Felds dwFlag der Bindungsstruktur auf DBCOLUMNSINFO_ISBOOKMARK fest, um anzugeben, dass die Spalte als Lesezeichen verwendet wird. Der Consumer legt zudem die Rowseteigenschaft DBPROP_BOOKMARKS auf VARIANT_TRUE fest. Dadurch kann die Spalte 0 im Rowset vorhanden sein. Mit der **IRowsetLocate::GetRowsAt**-Methode werden dann Zeilen abgerufen. Dabei wird mit der Zeile begonnen, die in einem Lesezeichen als Offset angegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
