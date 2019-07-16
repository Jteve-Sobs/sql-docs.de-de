---
title: Überprüfen der Unterstützung von Funktionen und Variabilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 21495e538a554a477336d1a92926c11fe762c5af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062665"
---
# <a name="checking-feature-support-and-variability"></a>Überprüfung der Funktionsunterstützung und Variabilität
Um Unterstützung von Funktionen und Variabilität zu überprüfen, rufen Anwendungen im allgemeinen **SQLGetInfo**, **SQLGetFunctions**, und **SQLGetTypeInfo**. Ein guter Ausgangspunkt ist die vom Treiber-API und SQL-Grammatik-Konformitätsgrad. Diese werden umfassende Maß an Unterstützung von Funktionen beschrieben. Die Anwendung kann dann aufrufen **SQLGetInfo** mit anderen Optionen, um zu bestimmen, die Unterstützung oder die Variabilität der Funktionen, die es benötigt, **SQLGetFunctions** bestimmen muss, ob die Funktionen über die zurückgegebene Konformitätsgrad werden unterstützt, und **SQLGetTypeInfo** zu bestimmen, welche SQL-Datentypen unterstützt werden.  
  
 Eine Anwendung kann bestimmen, ob ein Attribut-Anweisung oder die Verbindung durch den Aufruf unterstützt wird **SQLSetStmtAttr** oder **SQLSetConnectAttr** mit diesem Attribut. Wenn die Funktion SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, wird das Attribut unterstützt. Wenn SQL_ERROR zurück, und SQLSTATE HYC00 zurückgegeben (optionales Feature nicht implementiert), das Attribut wird nicht unterstützt.  
  
 Anwendungen können auch eine begrenzte Menge an Informationen, bevor Sie eine Verbindung mit der Treiber aufrufen bestimmen **SQLDrivers**.
