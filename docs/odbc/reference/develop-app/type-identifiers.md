---
title: Geben Sie Bezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79aa4de5d722208195477f7ffef53cac6c61a2de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093025"
---
# <a name="type-identifiers"></a>Typenbezeichner
Um SQL- und C-Datentypen zu beschreiben, ODBC definiert zwei Sätze von *Typenbezeichner*. Ein Typ-ID beschreibt den Typ der SQL-Spalte oder einem C-Puffer. Es ist ein **#define** Wert und in der Regel als ein Funktionsargument übergeben oder in den Metadaten zurückgegebenen.  
  
 Beispielsweise der folgende Aufruf von **SQLBindParameter** bindet eine Variable vom Typ SQL_DATE_STRUCT an eine Date-Parameter in einer SQL­Anweisung. Die C-Typ-ID SQL_C_TYPE_DATE gibt den Typ des der *Datum* Variable und die SQL-Typ-ID SQL_TYPE_DATE gibt Sie den Typ der dynamischen Parameter.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
