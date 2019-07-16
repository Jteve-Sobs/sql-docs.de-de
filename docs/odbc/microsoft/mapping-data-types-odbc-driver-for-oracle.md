---
title: Zuordnen von Datentypen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 47646fd6fdf1e8fd16165af1bcfc5e741c6e610f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080740"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Zuordnen von Datentypen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Der Oracle-Server unterstützt einen Satz von Datentypen. Der ODBC-Treiber für Oracle werden diese Datentypen in ihre entsprechenden ODBC SQL-Datentypen zugeordnet. Die folgende Tabelle enthält die Oracle 7.3-Server-Datentypen und die entsprechenden ODBC SQL-Datentypen.  
  
 Der ODBC-Treiber für Oracle unterstützt Oracle 7.3 und einige 8-Datentypen. Weitere Informationen zu unterstützten 8-Datentypen finden Sie unter [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Oracle-Server-Datentyp|ODBC-SQL-Datentyp|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|GLEITKOMMAZAHL|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Weitere Informationen zu die zulässige Größe der Spalte VARCHAR, finden Sie unter [VARCHAR-Spaltengröße](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) in diesem Handbuch.
