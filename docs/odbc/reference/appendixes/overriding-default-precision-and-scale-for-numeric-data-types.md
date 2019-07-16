---
title: Überschreiben der Standardgenauigkeit und Dezimalstellenanzahl für numerische Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66fc728440808314dbdaa30065c68232f4a89fba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100614"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Dezimalstellenanzahl für numerische Datentypen
Wenn das SQL_DESC_TYPE-Feld in einer ARD durch Aufrufen von entweder auf SQL_C_NUMERIC, festgelegt ist **SQLBindCol** oder **SQLSetDescField**SQL_DESC_SCALE Felds in die ARD auf 0 festgelegt ist, und das Feld "SQL_DESC_PRECISION" festgelegt ist um den treiberdefinierten standardgenauigkeit. Dies gilt auch, wenn das SQL_DESC_TYPE-Feld in einer APD auf SQL_C_NUMERIC, festgelegt ist, durch Aufrufen von entweder **SQLBindParameter** oder **SQLSetDescField**. Dies gilt für Eingabe-, Eingabe/Ausgabe oder Output-Parameter.  
  
 Wenn entweder die Standardwerte beschrieben nicht zuvor für eine Anwendung akzeptabel sind, sollte die Anwendung durch Aufrufen von Feld SQL_DESC_SCALE oder SQL_DESC_PRECISION festgelegt **SQLSetDescField** oder **SQLSetDescRec**.  
  
 Wenn die Anwendung ruft **SQLGetData** zum Zurückgeben von Daten in einer Struktur SQL_C_NUMERIC Standardfelder SQL_DESC_SCALE und SQL_DESC_PRECISION verwendet werden. Wenn die Standardwerte nicht akzeptabel sind, muss die Anwendung aufrufen **SQLSetDescRec** oder **SQLSetDescField** legen Sie die Felder aus, und rufen Sie anschließend **SQLGetData** mit einem *TargetType* von SQL_ARD_TYPE, um die Werte in die deskriptorfelder verwenden.  
  
 Wenn **SQLPutData** wird aufgerufen, der Aufruf verwendet die Felder SQL_DESC_SCALE und SQL_DESC_PRECISION der anwendungsparameterdeskriptor-Datensatz, der die Data-at-Execution-Parameter oder eine Spalte entspricht die APD Felder für Aufrufe sind  **SQLExecute** oder **SQLExecDirect**, oder ARD Felder für Aufrufe von **SQLBulkOperations** oder **SQLSetPos**.
