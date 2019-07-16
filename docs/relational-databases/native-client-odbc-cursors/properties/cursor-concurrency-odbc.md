---
title: Cursorparallelität (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9b310d062ec9c9acdbfce328abc5533bfb69178
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059542"
---
# <a name="cursor-concurrency-odbc"></a>Cursorparallelität (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Cursorvorgänge werden, wie Cursortypen, von den von der Anwendung festgelegten Parallelitätsoptionen beeinflusst. Parallelitätsoptionen werden festgelegt, mit der SQL_ATTR_CONCURRENCY-Option von [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Es gibt folgende Parallelitätstypen:  
  
-   Schreibgeschützt (SQL_CONCUR_READONLY)  
  
-   Werte (SQL_CONCUR_VALUES)  
  
-   Zeilenversion (SQL_CONCUR_ROWVER)  
  
-   Sperre (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
