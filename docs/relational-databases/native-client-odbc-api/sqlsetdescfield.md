---
title: SQLSetDescField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e91fd10869af91ff3ef6ab31fffdd0d9a8105d6d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677489"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLSetDescField kann verwendet werden, um deskriptorfelder für Tabellenwertparameter und Tabellenwertparameter-Spalten festzulegen. Weitere Informationen zu den verfügbaren Feldern finden Sie unter [Deskriptorfelder für Tabellenwertparameter-Parameter](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) und [Deskriptorfelder für Tabellenwertparameter-Parameter enthaltene Spalten](../../relational-databases/native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).  
  
## <a name="remarks"></a>Hinweise  
 Tabellenwertparameter-Spalten sind nur verfügbar, wenn das Deskriptorheaderfeld SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Datensatzes festgelegt ist, für den SQL_DESC_TYPE auf SQL_SS_TABLE eingestellt ist. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Wenn es versucht wird, um SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Parameters festzulegen, die nicht auf einem Tabellenwertparameter ist SQLSetStmtAttr SQL_ERROR zurück gibt und ein Diagnosedatensatz mit SQLSTATE erstellt = HY024 und der Meldung "Ungültiger Attributwert". SQL_SOPT_SS_PARAM_FOCUS wird nicht geändert, wenn SQL_ERROR zurückgegeben wird.  
  
 Durch das Festlegen von SQL_SOPT_SS_PARAM_FOCUS auf 0 (null) wird der Zugriff auf Deskriptordatensätze für Parameter wiederhergestellt.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>SQLSetDescField-Unterstützung für erweiterte Funktionen zu Datum und Uhrzeit  
 Datum/Uhrzeit-Funktionen wurden in ODBC verbessert. Informationen über das für die neuen Datum/Uhrzeittypen verfügbare Deskriptorfeld finden Sie unter [Parameter and Result Metadata](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>SQLSetDescField-Unterstützung für große CLR-UDTs  
 SQLSetDescField unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>SQLSetDescField-Unterstützung für Spalten mit geringer Dichte  
 SQLSetDecField kann verwendet werden, zum Festlegen von SQL_SOPT_SS_NAME_SCOPE im anweisungsparameterdeskriptor (APD) auf die Werte SQL_SS_NAME_SCOPE_EXTENDED und SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Weitere Informationen finden Sie unter [Sparse Columns Support &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
