---
title: SQLPutData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f5b813a2e411d1b8b4dcf1069f656ed844f4e77
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68131222"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die folgenden Einschränkungen gelten beim Senden von mehr als 65.535 Byte Daten mit SQLPutData (für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 4. 21a) oder 400 KB Daten (für SQL Server, Version 6.0 und höher) für eine SQL_LONGVARCHAR (**Text**), SQL_WLONGVARCHAR (**Ntext**) oder SQL_LONGVARBINARY (**Image**) Spalte:  
  
-   Der referenzierte Parameter sein kann die *Insert_value* in einer INSERT-Anweisung.  
  
-   Der referenzierte Parameter sein kann eine *Ausdruck* in der SET-Klausel einer UPDATE-Anweisung.  
  
 Abbrechen einer Sequenz von SQLPutData-Aufrufe, die Daten in Blöcken mit einem Server bereitstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bewirkt, dass eine teilaktualisierung für den Wert der Spalte bei Verwendung von Version 6.5 oder früher. Die **Text**, **Ntext**, oder **Image** Spalte, auf die verwiesen wurde, als SQLCancel aufgerufen wurde, ein platzhalterzwischenwert festgelegt ist.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Treiber unterstützt das Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version 6.5 und niedriger nicht.  
  
## <a name="diagnostics"></a>Diagnose  
 Es gibt ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-spezifischen SQLSTATE für SQLPutData:  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Wenn die Länge der Daten in der zu sendenden Bytes von einer Anwendung, beispielsweise mit SQL_LEN_DATA_AT_EXEC angegeben wurde (*n*), in denen *n* ist größer als 0 (null) die Gesamtanzahl von Bytes, von der Anwendung über SQLPutData muss mit die angegebene Länge übereinstimmen.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData und Tabellenwertparameter  
 SQLPutData wird von einer Anwendung verwendet, wenn Variablen zeilenbindung mit Tabellenwertparametern verwenden. Die *StrLen_Or_Ind* Parameter gibt an, dass sie bereit für den Treiber zum Sammeln von Daten für die nächste Zeile bzw. Zeilen von Tabellenwertparameter-Daten ist oder keine weiteren Zeilen verfügbar sind:  
  
-   Ein Wert größer als 0 gibt an, dass der nächste Satz von Zeilenwerten verfügbar ist.  
  
-   Der Wert 0 gibt an, dass es keine Zeilen mehr gibt, die gesendet werden sollen.  
  
-   Ein Wert unter 0 zeigt einen Fehler an und führt dazu, dass ein Diagnosedatensatz mit SQLState HY090 aufgezeichnet und die Meldung „Ungültige Zeichenfolge oder Pufferlänge“ ausgegeben wird.  
  
 Die *DataPtr* Parameter wird ignoriert, jedoch muss auf einen Wert ungleich NULL festgelegt werden. Weitere Informationen finden Sie im Abschnitt für Variablen zeilenbindung in [Bindung und Data Transfer of Table-Valued-Parameter und Spaltenwerte](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Wenn *StrLen_Or_Ind* verfügt über einen anderen Wert als SQL_DEFAULT_PARAM oder eine Zahl zwischen 0 und SQL_PARAMSET_SIZE (d. h. die *ColumnSize* -Parameter von SQLBindParameter), ist ein Fehler auf. Dieser Fehler bewirkt, dass SQLPutData SQL_ERROR zurück: SQLSTATE = HY090, "Ungültige Zeichenfolgen- oder Pufferlänge".  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Parameterwerte von Datum-/Uhrzeit-Typen werden konvertiert, wie in beschrieben [Konvertierungen von C-zu SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData-Unterstützung für große CLR-UDTs  
 **SQLPutData** unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPutData-Funktion](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
