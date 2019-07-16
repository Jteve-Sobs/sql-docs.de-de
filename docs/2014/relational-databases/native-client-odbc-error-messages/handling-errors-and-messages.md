---
title: Behandeln von Fehlern und Meldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4a4d87ccae235aee1a11e58aff60fe8e34d6205
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207095"
---
# <a name="handling-errors-and-messages"></a>Behandlung von Fehlern und Meldungen
  Wenn eine Anwendung eine ODBC-Funktion aufruft, wird der Treiber führt die Funktion aus und gibt Diagnoseinformationen zurück, gibt es zwei Möglichkeiten: Ein Rückgabecode gibt an, den Erfolg oder Fehlschlagen des ODBC-Funktion, und DiagnoseDatensätze liefern detaillierte Informationen über die Funktion. Diagnosedatensätze enthalten einen Headerdatensatz und Statusdatensätze. Auch wenn die Funktion erfolgreich ausgeführt wurde, wird zumindest ein Diagnosedatensatz, der Headerdatensatz, zurückgegeben.  
  
 Die Diagnoseinformationen dienen während der Entwicklung zur Erfassung von Programmierfehlern wie ungültigen Handles und Syntaxfehlern in hartcodierten SQL-Anweisungen. Darüber hinaus dienen sie zur Laufzeit dazu, Laufzeitfehler und Warnungen zu erfassen, beispielsweise das Abschneiden von Daten, Regelverstöße und Syntaxfehler in benutzerdefinierten SQL-Anweisungen. Die Programmlogik basiert im Allgemeinen auf Rückgabecodes.  
  
 Beispiel: Nachdem eine Anwendung ruft **SQLFetch** um die Zeilen in einem Resultset abzurufen, der Rückgabecode gibt an, ob das Ende des Resultsets (SQL_NO_DATA), erreicht wurde, wenn informationsmeldungen (SQL_SUCCESS_ zurückgegeben wurden WITH_INFO), oder bei einem Fehler (SQL_ERROR).  
  
 Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt etwas anderes als SQL_SUCCESS, zu die Anwendung rufen **SQLGetDiagRec** zum Abrufen, die Informations- oder Fehlermeldungen. Verwendung **SQLGetDiagRec** , führen Sie einen Bildlauf nach oben und unten die Nachricht festlegen, wenn mehr als eine Nachricht.  
  
 Der Rückgabecode SQL_INVALID_HANDLE gibt immer einen Programmierfehler an und sollte zur Laufzeit nie auftreten. Alle anderen Rückgabecodes stellen Laufzeitinformationen bereit, wenngleich SQL_ERROR einen Programmierfehler angeben kann.  
  
 Die ursprüngliche [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] systemeigene API, die DB-Library für C, ermöglicht einer Anwendung zum Installieren der Rückruf für die Fehlerbehandlung und meldungsverarbeitungs-Funktionen, Fehler oder Meldungen zurückgeben. Einige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, wie PRINT, RAISERROR, DBCC und SET, geben ihre Ergebnisse an die Meldungshandlerfunktion der DB-Library anstatt an ein Resultset zurück. Jedoch verfügt die ODBC-API über keine solche Rückruffähigkeit. Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber Meldungen erkennt wieder aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], er setzt Sie den ODBC-Rückgabecode auf SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück, und gibt die Nachricht als eine oder mehrere DiagnoseDatensätze zurück. Aus diesem Grund eine ODBC-Anwendung muss sorgfältig testen, für diese Codes und rufen Rückgabetypen **SQLGetDiagRec** um Meldungsdaten abzurufen.  
  
 Informationen zur Ablaufverfolgung von Fehlern finden Sie unter [Data Access Tracing (Ablaufverfolgung für den Datenzugriff)](https://go.microsoft.com/fwlink/?LinkId=125805). Informationen zu Verbesserungen hinzugefügten fehlerablaufverfolgung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], finden Sie unter [den Zugriff auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verarbeiten von Anweisungen, die Meldungen generieren](processing-statements-that-generate-messages.md)  
  
-   [Diagnosedatensätze und -felder](diagnostic-records-and-fields.md)  
  
-   [Systemeigene Fehlernummern](native-error-numbers.md)  
  
-   [SQLSTATE &#40;ODBC-Fehlercodes&#41;](sqlstate-odbc-error-codes.md)  
  
-   [Fehlermeldungen](error-messages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
