---
title: Erstellen einer SQL­Anweisung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3e4b2665920541ac2b59a706e0088adc83c35ad2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937316"
---
# <a name="constructing-an-sql-statement-odbc"></a>Erstellen einer SQL-Anweisung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In ODBC-Anwendungen werden fast alle Datenbankzugriffe mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen ausgeführt. Die Form dieser Anweisungen richtet sich nach den Anforderungen der Anwendung. SQL-Anweisungen können auf folgende Weise gebildet werden:  
  
-   Hartcodiert  
  
     Statische Anweisungen, die von einer Anwendung als feste Aufgabe ausgeführt werden.  
  
-   Zur Laufzeit  
  
     SQL-Anweisungen, die zur Laufzeit gebildet werden und es den Benutzern ermöglichen, die Anweisung mit gängigen Klauseln wie SELECT, WHERE und ORDER BY anzupassen. Hierzu gehören auch von den Benutzern eingegebene Ad-hoc-Abfragen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client-ODBC-Treiber analysiert SQL-Anweisungen nur nach ODBC- und ISO-Syntax, die nicht direkt unterstützt werden, indem die [!INCLUDE[ssDE](../../includes/ssde-md.md)], die der Treiber wandelt [!INCLUDE[tsql](../../includes/tsql-md.md)]. Jede andere SQL-Syntax wird wie vorliegend an das [!INCLUDE[ssDE](../../includes/ssde-md.md)] weitergeleitet, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, ob sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zulässig ist. Dieser Ansatz hat zwei Vorteile:  
  
-   Geringerer Arbeitsaufwand  
  
     Der Arbeitsaufwand des Treibers wird minimiert, weil er nur eine kleine Anzahl von ODBC- und ISO-Klauseln überprüfen muss.  
  
-   Flexibilität  
  
     Programmierer können die Portabilität ihrer Anwendungen anpassen. Um die Portabilität für mehrere Datenbanken zu verbessern, verwenden Sie primär die ODBC- und ISO-Syntax. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen Erweiterungen zu verwenden, verwenden Sie die entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Syntax. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt die vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, sodass auf ODBC basierende Anwendungen alle Features nutzen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Die Spaltenliste der SELECT-Anweisung sollte nur die Spalten enthalten, die zur Ausführung der aktuellen Aufgabe erforderlich sind. Dadurch werden nicht nur weniger Daten über das Netzwerk gesendet, sondern Datenbankänderungen wirken sich in geringerem Umfang auf die Anwendung aus. Wenn eine Anwendung nicht auf eine Spalte einer Tabelle verweist, dann ist die Anwendung von keinerlei Änderungen betroffen, die an dieser Spalte vorgenommen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
