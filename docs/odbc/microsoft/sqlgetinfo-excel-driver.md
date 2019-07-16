---
title: SQLGetInfo (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Excel Driver
ms.assetid: fed4aea2-6d3d-4199-a5db-3d033eb63927
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba2e23bf4b3c464c5483897c0a9dd3e6c9dea626
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003281"
---
# <a name="sqlgetinfo-excel-driver"></a>SQLGetInfo (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** unterstützt die SQL_FILE_USAGE Informationstyp. Der zurückgegebene Wert ist eine 16-Bit-Ganzzahl, die angibt, wie der Treiber die Dateien in einer Datenquelle direkt behandelt:  
  
-   SQL_FILE_NOT_SUPPORTED - ist der Treiber keinen ein-Ebenen-Treiber.  
  
-   SQL_FILE_TABLE - behandelt ein ein-Ebenen-Treiber-Dateien in einer Datenquelle als Tabellen.  
  
-   SQL_FILE_QUALIFIER - Treiber nur einer Ebene behandelt Dateien in einer Datenquelle, als Qualifizierer.  
  
 Der ODBC-Treiber gibt für die Microsoft Exceldriver SQL_FILE_TABLE zurück, da jede Datei eine Tabelle handelt.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Format der Versionsnummer|  
|----------|-------------|-------------------------------|  
|Microsoft Excel|3.0|03.00.0000|  
||4.0|04.00.0000|  
||5.0/7.0|05.00.0000|  
||97/2000|08.00.0000|  
  
## <a name="sqlfileusage"></a>SQL_FILE_USAGE  
 SQL_FILE_TABLE (Excel 3.0/4.0)  
  
 SQL_FILE_CATALOG (Excel 5.0/7.0)  
  
## <a name="sqlmaxcharliterallen"></a>SQL_MAX_CHAR_LITERAL_LEN  
 255 (Excel 3.0/4.0/5.0/7.0)  
  
 65535 (Excel 97)  
  
## <a name="sqlmaxcolumnnamelen"></a>SQL_MAX_COLUMN_NAME_LEN  
 30 (Excel 3.0/4.0)  
  
 64 (Excel 5.0/7.0/97)  
  
## <a name="sqlmaxtablenamelen"></a>SQL_MAX_TABLE_NAME_LEN  
 12 (Excel 3.0/4.0)  
  
 31 (Excel 5.0/7.0/97)  
  
## <a name="sqlcatalognameseparator"></a>SQL_CATALOG_NAME_SEPARATOR  
 "\\" (Excel-3.0/4.0)  
  
 "." (Excel-5.0/7.0/97)  
  
## <a name="sqlcatalogterm"></a>SQL_CATALOG_TERM  
 "Directory" (Excel 3.0/4.0)  
  
 "Arbeitsmappe" (Excel 5.0/7.0/97)  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
