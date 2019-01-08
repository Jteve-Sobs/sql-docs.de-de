---
title: Fehler und Batches | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97179574407dca56026f9d5216e4978069cffc1e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527330"
---
# <a name="errors-and-batches"></a>Fehler und Batches
Tritt ein Fehler während der Ausführung eines Batches von SQL-Anweisungen, eine der folgenden vier Vorgänge sind möglich. (Jedes mögliche Ergebnis ergibt Daten datenquellenspezifische und möglicherweise sogar richten sich nach den Anweisungen in den Batch aufgenommen.)  
  
-   Es werden keine Anweisungen im Batch ausgeführt.  
  
-   Keine Anweisungen im Batch werden ausgeführt, und die Transaktion ein Rollback aus.  
  
-   Alle Anweisungen vor der Error-Anweisung ausgeführt werden.  
  
-   Alle Anweisungen mit Ausnahme der Error-Anweisung ausgeführt werden.  
  
 In den ersten beiden Fällen **SQLExecute** und **SQLExecDirect** SQL_ERROR zurück. In den letzten beiden Fällen können sie SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurück, je nach Implementierung zurückgeben. In allen Fällen weitere Fehlerinformationen kann abgerufen werden mit **SQLGetDiagField**, **SQLGetDiagRec**, oder **SQLError**. Die Art und Tiefe der diese Informationen sind jedoch Daten datenquellenspezifische. Darüber hinaus sind diese Informationen wahrscheinlich nicht genau die Anweisung in Fehler zu identifizieren.
