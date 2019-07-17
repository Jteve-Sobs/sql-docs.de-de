---
title: Vergleich von protokollierten und Nicht protokollierte Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 91e832a0f2abdfea91a63f17414bf431e7275103
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128904"
---
# <a name="logged-vs-unlogged-modifications"></a>Vergleich von protokollierten und nicht protokollierten Änderungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Kann eine Anwendung anfordern, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber nicht protokolliert **Text**, **Ntext**, und **Image** Änderungen. Diese Option sollte jedoch mit Vorsicht eingesetzt werden. Es sollte nur für diese Fälle verwendet werden, in denen die **Text**, **Ntext**, oder **Image** Daten sind nicht kritische und Besitzer der Daten bereit sind, die Möglichkeit zum Wiederherstellen von Daten für die Kompromisse höhere Leistung.  
  
 Die Protokollierung von **Text**, **Ntext**, und **Image** Änderungen wird gesteuert, durch den Aufruf [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) mit der  *Attribut* Parameter legen auf SQL_SOPT_SS_ TEXTPTR_LOGGING und *ValuePtr* legen Sie entweder auf SQL_TL_ON oder auf sql_tl_off festgelegt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text und Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
