---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7dc6cfb5388634e9e2f4281250dd7eb619102515
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106755"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen generieren keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters erlauben oder die Anzahl der betroffenen Zeilen zurück, wenn ausgeführt:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei einer erfolgreichen Ausführung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück, und die Nachrichten stehen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück, und verfügt über eine oder mehrere informationsmeldungen nach der Ausführung von vielen [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen oder Ausführung der Consumer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Element -Funktion.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Consumer ermöglicht die dynamische Angabe von Abfragetext sollte fehlerschnittstellen überprüfen Sie nach jeder Ausführung der Elementfunktion unabhängig vom Wert von den Rückgabecode, das Vorhandensein oder fehlen einer zurückgegebenen **IRowset** oder **IMultipleResults** -Schnittstellenverweises oder die Anzahl der betroffenen Zeilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
