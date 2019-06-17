---
title: Katalog- und Schemaverwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9476f4f928890514354f97ce604f871bd8a06d11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007888"
---
# <a name="catalog-and-schema-usage"></a>Katalog- und Schemaverwendung
Datenquellen unterstützen nicht unbedingt Katalog-und Schemanamen als Name der Objektbezeichner in allen SQL-Anweisungen. Datenquellen können Katalog-und Schemanamen in einer oder mehreren der folgenden Klassen von SQL-Anweisungen unterstützen: Data Manipulation Language (DML)-Anweisungen, Prozeduraufrufe, datendefinitionsanweisungen für die Tabelle, Index-datendefinitionsanweisungen und datendefinitionsanweisungen Berechtigungen. Um die Klassen der SQL-Anweisungen zu ermitteln, in der Katalog und Schema Namen verwendet werden können, eine Anwendung ruft **SQLGetInfo** mit den Optionen SQL_CATALOG_USAGE und SQL_SCHEMA_USAGE.
