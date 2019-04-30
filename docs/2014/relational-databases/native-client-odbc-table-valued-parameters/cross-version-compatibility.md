---
title: Versionsübergreifende Kompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f23b0f43b32d737f03cb7c9b00368558e89e9288
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199996"
---
# <a name="cross-version-compatibility"></a>Versionsübergreifende Kompatibilität
  Konflikte zwischen Versionen können auftreten, wenn Client- oder Serverinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tabellenwertparameter verarbeiten sollen.  
  
 Im Allgemeinen ist die Tabellenwertparameter-Funktionalität nur für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Clients oder höher verfügbar (unter Verwendung von SQL Server Native Client 10.0), die mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Servern (oder höher) verbunden sind. Neue Spalten in Resultsets von Katalogfunktionen ist nur vorhanden sein, beim Verbinden mit einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) Server.  
  
 Wenn eine mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompilierte Clientanwendung Anweisungen ausführt, für die Tabellenwertparameter erwartet werden, wird dies vom Server als Datenkonvertierungsfehler erkannt, und ODBC gibt einen SQLSTATE 07006-Fehler und die Meldung "Attributverletzung beschränkter Datentypen" zurück.  
  
 Wenn eine Clientanwendung, die mit kompiliert wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 oder höher versucht, verwenden Sie Tabellenwertparameter beim Verbinden mit einer Server-Instanz vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client erkennt dies und SQLBindCol, SQLBindParameter SQLSetDescFields und SQLSetDescRec Aufrufe schlagen mit SQLSTATE 07006 und der Meldung fehl "Restricted Daten attributverletzung (die Version von SQLServer für diese Verbindung unterstützt keine Tabellenwertparameter)".  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
