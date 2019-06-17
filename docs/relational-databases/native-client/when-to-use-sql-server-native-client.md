---
title: Wenn für SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 403fd25702890ef0e030ba191e1750aa685a6642
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026641"
---
# <a name="when-to-use-sql-server-native-client"></a>Einsatzbedingungen für SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ist eine Technologie, mit der Sie auf Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zugreifen können.  Eine Besprechung der unterschiedlichen Datenzugriffstechnologien finden Sie unter [Data Access Technologies Road Map (Übersicht über Datenzugriffstechnologien)](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Sie sollten bei der Entscheidung, ob Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client als Datenzugriffstechnologie in einer Anwendung verwenden sollen, verschiedene Faktoren berücksichtigen.  
  
 Wenn Sie neue Anwendungen in einer verwalteten Programmiersprache wie Microsoft Visual C# oder Visual Basic schreiben und auf die neuen Funktionen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, zugreifen müssen, sollten Sie den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, der Teil von .NET Framework ist.  
  
 Wenn Sie eine COM-basierte Anwendung entwickeln und auf die neuen Funktionen zugreifen müssen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, dann sollten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verwenden. Wenn Sie nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen, können Sie weiterhin Windows Data Access Components (WDAC) verwenden.  
  
 Bei vorhandenen OLE DB- und ODBC-Anwendungen ist ausschlaggebend, ob Sie auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen. Wenn Sie eine ausgereifte Anwendung haben, die nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen muss, können Sie weiterhin WDAC verwenden. Wenn Sie diese neuen Funktionen, wie z. B. zugreifen müssen jedoch die [Xml-Datentyp](../../t-sql/xml/xml-transact-sql.md), verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Sowohl [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client als auch MDAC unterstützen die Read Committed-Isolation mit Zeilenversionsverwaltung, aber nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützt die Momentaufnahmen-Transaktionsisolation. (Programmiertechnisch ausgedrückt ist die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion.)  
  
 Informationen zu den Unterschieden zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client und MDAC finden Sie unter [Aktualisieren einer Anwendung von MDAC auf SQL Server Native Client](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Vorgehensweisen zu ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Vorgehensweisen für OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
