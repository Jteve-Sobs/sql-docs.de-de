---
title: SQLTables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8209bf586e5a0b288b4975869ee8903a73a27f06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188665"
---
# <a name="sqltables"></a>SQLTables
  SQLTables kann in einem statischen Servercursor ausgeführt werden. SQLTables in einem aktualisierbaren (dynamischen oder Keyset-) Cursor ausgeführt wird, wird SQL_SUCCESS_WITH_INFO, der angibt, dass der Cursortyp geändert wurde.  
  
 SQLTables meldet Tabellen aus allen Datenbanken auf, wenn die *CatalogName* -Parameter sql_all_catalogs lautet und alle anderen Parameter enthalten Standardwerte (NULL-Zeiger).  
  
 Um verfügbare Kataloge, Schemas und Tabellentypen zu melden, nutzt SQLTables spezielle leere Zeichenfolgen (mit der Länge Null Byte-Zeiger). Leere Zeichenfolgen sind keine Standardwerte (NULL-Zeiger).  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables gibt Informationen über alle Tabellen, deren Namen übereinstimmen *TableName* und den aktuellen Benutzer gehören.  
  
## <a name="sqltables-and-table-valued-parameters"></a>'SQLTables'- und Tabellenwertparameter  
 Wenn das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE statt auf den Standardwert SQL_SS_NAME_SCOPE_TABLE aufweist, werden Informationen über Tabellentypen von SQLTables zurück. Die TABLE_TYPE-Wert, der für einen Tabellentyp in Spalte 4 des SQLTables zurückgegebenes Resultset zurückgegeben wird TABELLENTYP. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Tabellen, Sichten und Synonyme nutzen einen gemeinsamen Namespace, der sich von dem Namespace unterscheidet, den Tabellentypen verwenden. Wenngleich ein und derselbe Namespace nicht eine Tabelle und eine Sicht enthalten kann, ist es hingegen möglich, dass ein Namespace im selben Katalog und Schema eine Tabelle und einen Tabellentypen enthält.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQLTables-Funktion](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
