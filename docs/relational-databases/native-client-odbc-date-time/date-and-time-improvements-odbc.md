---
title: Datums- / Uhrzeitverbesserungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6669ab863896acd9633171fd4c3e7330f9edd74f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659809"
---
# <a name="date-and-time-improvements-odbc"></a>Verbesserungen bei Datum und Zeit (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wurden neue Datums- und Uhrzeitdatentypen eingeführt. In diesem Abschnitt wird beschrieben, wie diese neuen Typen als Erweiterungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verfügbar gemacht werden. Eine Übersicht über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützten neuen Datums- und Uhrzeitdatentypen finden Sie unter [Datums- / Uhrzeitverbesserungen](../../relational-databases/native-client/features/date-and-time-improvements.md). Ein Beispiel, Unterstützung für ODBC-Datum/Uhrzeit veranschaulicht, finden Sie unter [Verwenden von Datums- und Uhrzeittypen](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Weitere allgemeine Informationen zu Datum und Uhrzeit-Datentypen finden Sie unter ["DateTime" &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datentypunterstützung für ODBC-Verbesserungen bei Datum und Uhrzeit](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Liefert Informationen über ODBC-Typen, die Datums- und Uhrzeitdatentypen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen.  
  
 [Metadaten &#40;ODBC&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 Enthält Informationen, die in den IPD (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) und Implementierung Zeile deskriptorfelder (IRD), als auch zurückgegebene Spaltenmetadaten zurückgegebenen **SQLColumns** und **SQLProcedureColumns**. Beschreibt außerdem durch zurückgegebene datentypmetadaten **SQLGetTypeInfo**.  
  
 [DateTime-Datentypkonvertierungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 Beschreibt die Konvertierung zwischen datetime- und datetimeoffset-Werten.  
  
 [sql_variant-Unterstützung für Datum- und Uhrzeit-Typen](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 Beschreibt die Unterstützung der SQL_VARIANT-Funktion für die verbesserte Datums- und Uhrzeitfunktionalität.  
  
 [Massenimport der Kopie Änderungen für verbesserte Datums- und Uhrzeittypen &#40;OLE DB- und ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Beschreibt Datums-/Uhrzeitverbesserungen zur Unterstützung von Massenkopiervorgängen.  
  
 [Verbesserte Datums- und die Uhrzeit geben Verhalten bei früheren Versionen von SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Beschreibt das erwartete Verhalten, wenn eine Clientanwendung mithilfe der verbesserte Datums- und Uhrzeitfunktionen mit einer älteren Version von kommuniziert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und wenn ein Client mit einer älteren Version von kompiliert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sendet Befehle an einen Server, die Es verbesserte Datums- und Uhrzeitfunktionen unterstützt.  
  
 [ODBC API-Unterstützung für verbesserte Funktionen für Datum und Uhrzeit](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 Listet die ODBC-Funktionen auf, die die verbesserte Datums- und Uhrzeitfunktionalität unterstützen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
