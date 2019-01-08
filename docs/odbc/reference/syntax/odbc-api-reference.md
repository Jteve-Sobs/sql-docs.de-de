---
title: ODBC-API-Referenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: dllExport
ms.assetid: b7a49774-f458-44ce-9a04-a0457501405b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56d6068b842256bd450844c7b163727e5d35f3d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525060"
---
# <a name="odbc-api-reference"></a>ODBC-API-Referenz
In die Themen in diesem Abschnitt beschreiben die einzelnen ODBC-Funktion in alphabetischer Reihenfolge. Jede Funktion wird als eine C-Funktion "Language" Programmierschnittstelle definiert. Die folgenden: Beschreibungen  
  
-   Zweck  
  
-   ODBC-version  
  
-   Standard CLI-Konformitätsgrad  
  
-   Syntax  
  
-   Argumente  
  
-   Rückgabewerte  
  
-   Diagnose  
  
-   Kommentare zur Verwendung und Implementierung  
  
-   Codebeispiel  
  
-   Verweise auf verwandte Funktionen  
  
 Der standard CLI-Konformitätsgrad kann einen der folgenden sein: ISO-92, ODBC-Gruppe zu öffnen oder als veraltet markiert. Eine Funktion, die wie ISO-92-konformen auch in Version 1, öffnen Sie die angezeigt wird markiert, da die Open Group eine reine der ISO-92 ist. Eine Funktion, die als "Open Group-kompatibel" gekennzeichnet, die auch in ODBC 3. angezeigt werden. *x*, da ODBC 3. *X* ist eine reine Obermenge der öffnen Sie die Version 1. Eine Funktion, die gekennzeichnet werden, wie in keiner der beiden standardmäßigen ODBC-konformen angezeigt wird. Eine Funktion, die markiert, als veraltet, wurde in ODBC 3. als veraltet markiert. *x*.  
  
 Behandlung von Diagnoseinformationen finden Sie auf die [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) funktionsbeschreibung. Der SQLSTATE-Werten zugeordnete Text enthalten eine Beschreibung der Bedingung ist jedoch dient nicht zum Schreiben von bestimmtem Text vor.  
  
> [!NOTE]  
>  Treiber-spezifische Informationen zu ODBC-Funktionen finden Sie im Abschnitt für den Treiber.  
  
 Dieser Abschnitt enthält Themen, die für die folgenden Funktionen:  
  
-   [SQLAllocConnect-Funktion](../../../odbc/reference/syntax/sqlallocconnect-function.md)  
  
-   [SQLAllocEnv-Funktion](../../../odbc/reference/syntax/sqlallocenv-function.md)  
  
-   [SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLAllocStmt-Funktion](../../../odbc/reference/syntax/sqlallocstmt-function.md)  
  
-   [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)  
  
-   [SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
-   [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)  
  
-   [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)  
  
-   [SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)  
  
-   [SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)  
  
-   [SQLColAttribute-Funktion](../../../odbc/reference/syntax/sqlcolattribute-function.md)  
  
-   [SQLColAttributes-Funktion](../../../odbc/reference/syntax/sqlcolattributes-function.md)  
  
-   [SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)  
  
-   [SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)  
  
-   [SQLCompleteAsync-Funktion](../../../odbc/reference/syntax/sqlcompleteasync-function.md)  
  
-   [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
-   [SQLCopyDesc-Funktion](../../../odbc/reference/syntax/sqlcopydesc-function.md)  
  
-   [SQLDataSources-Funktion](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)  
  
-   [SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)  
  
-   [SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)  
  
-   [SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
-   [SQLDrivers-Funktion](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)  
  
-   [SQLError-Funktion](../../../odbc/reference/syntax/sqlerror-function.md)  
  
-   [SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)  
  
-   [SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)  
  
-   [SQLExtendedFetch-Funktion](../../../odbc/reference/syntax/sqlextendedfetch-function.md)  
  
-   [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
-   [SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
-   [SQLForeignKeys-Funktion](../../../odbc/reference/syntax/sqlforeignkeys-function.md)  
  
-   [SQLFreeConnect-Funktion](../../../odbc/reference/syntax/sqlfreeconnect-function.md)  
  
-   [SQLFreeEnv-Funktion](../../../odbc/reference/syntax/sqlfreeenv-function.md)  
  
-   [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
-   [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)  
  
-   [SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLGetConnectOption-Funktion](../../../odbc/reference/syntax/sqlgetconnectoption-function.md)  
  
-   [SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)  
  
-   [SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)  
  
-   [SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)  
  
-   [SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)  
  
-   [SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLGetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
-   [SQLGetStmtOption-Funktion](../../../odbc/reference/syntax/sqlgetstmtoption-function.md)  
  
-   [SQLGetTypeInfo-Funktion](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
-   [SQLMoreResults-Funktion](../../../odbc/reference/syntax/sqlmoreresults-function.md)  
  
-   [SQLNativeSql-Funktion](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
-   [SQLNumParams-Funktion](../../../odbc/reference/syntax/sqlnumparams-function.md)  
  
-   [SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)  
  
-   [SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)  
  
-   [SQLParamOptions-Funktion](../../../odbc/reference/syntax/sqlparamoptions-function.md)  
  
-   [SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)  
  
-   [SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)  
  
-   [SQLProcedureColumns-Funktion](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)  
  
-   [SQLProcedures-Funktion](../../../odbc/reference/syntax/sqlprocedures-function.md)  
  
-   [SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)  
  
-   [SQLRowCount-Funktion](../../../odbc/reference/syntax/sqlrowcount-function.md)  
  
-   [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   [SQLSetConnectOption-Funktion](../../../odbc/reference/syntax/sqlsetconnectoption-function.md)  
  
-   [SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)  
  
-   [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
-   [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)  
  
-   [SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)  
  
-   [SQLSetParam-Funktion](../../../odbc/reference/syntax/sqlsetparam-function.md)  
  
-   [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)  
  
-   [SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)  
  
-   [SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
-   [SQLSetStmtOption-Funktion](../../../odbc/reference/syntax/sqlsetstmtoption-function.md)  
  
-   [SQLSpecialColumns-Funktion](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)  
  
-   [SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)  
  
-   [SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)  
  
-   [SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)  
  
-   [SQLTransact-Funktion](../../../odbc/reference/syntax/sqltransact-function.md)
