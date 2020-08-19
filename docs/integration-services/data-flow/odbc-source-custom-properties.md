---
description: ODBC Source Custom Properties
title: Benutzerdefinierte Eigenschaften der ODBC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c0c01d66062747788bd9bf05ca8cf06e8e5088a6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430762"
---
# <a name="odbc-source-custom-properties"></a>ODBC Source Custom Properties

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der ODBC-Quelle beschrieben. Alle Eigenschaften können über SSIS-Eigenschaftsausdrücke festgelegt werden.  
  
|Eigenschaftenname|Datentyp|BESCHREIBUNG|  
|-------------------|---------------|-----------------|  
|Verbindung|ODBC-Verbindung|Eine ODBC-Verbindung für den Zugriff auf die Quelldatenbank.|  
|AccessMode|Ganze Zahl (Enumeration)|Der zum Zugreifen auf die Datenbank verwendete Modus. Die möglichen Werte sind der Tabellenname (0) und der SQL-Befehl (1).<br /><br /> Die Standardeinstellung ist der Tabellenname (0).|  
|BatchSize|Integer|Die Größe des Batches für die Massenextrahierung. Dies ist die Anzahl der als Array extrahierten Datensätze. Wenn der ausgewählte ODBC-Anbieter keine Arrays unterstützt, beträgt die Batchgröße 1.|  
|BindCharColumnAs|Ganze Zahl (Enumeration)|Diese Eigenschaft bestimmt, wie die ODBC-Quelle Spalten an Zeichenfolgentypen mit mehreren Byte bindet, z. B. SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR.<br /><br /> Die möglichen Werte sind Unicode (0), wobei die Spalten als SQL_C_WCHAR gebunden werden, und ANSI (1), wobei die Spalten als SQL_C_CHAR gebunden werden. Der Standardwert ist Unicode (0).<br /><br /> **Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|BindNumericAs|Ganze Zahl (Enumeration)|Diese Eigenschaft bestimmt, wie die ODBC-Quelle Spalten mit numerischen Daten an die Datentypen SQL_TYPE_NUMERIC und SQL_TYPE_DECIMAL bindet.<br /><br /> Die möglichen Optionen sind Char (0), wobei die Spalten als SQL_C_CHAR gebunden werden, und Numeric (1), wobei die Spalten als SQL_C_NUMERIC gebunden werden. Der Standardwert ist Char (0).<br /><br /> **Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|DefaultCodePage|Integer|Die Codepage, die für Zeichenfolgen-Ausgabespalten verwendet werden soll.<br /><br /> **Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|ExposeCharColumnsAsUnicode|Boolean|Diese Eigenschaft bestimmt, wie die Komponente CHAR-Spalten verfügbar macht. Der Standardwert ist False. Dieser Wert gibt an, dass CHAR-Spalten als Multibyte-Zeichenfolgen (DT_STR) verfügbar gemacht werden. Wenn True gilt, werden CHAR-Spalten als breite Zeichenfolgen (DT_WSTR) verfügbar gemacht.<br /><br /> **Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|FetchMethod|Ganze Zahl (Enumeration)|Die Methode, die zum Abrufen der Daten verwendet wird. Die möglichen Optionen sind Zeile für Zeile (0) und Batch (1). Der Standardwert ist Batch (1).<br /><br /> Weitere Informationen zu diesen Optionen finden Sie unter [ODBC Source](../../integration-services/data-flow/odbc-source.md).<br /><br /> **Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.|  
|SqlCommand|String|Der SQL-Befehl, der ausgeführt werden soll, wenn AccessMode auf SQL-Befehl festgelegt wird.|  
|StatementTimeout|Integer|Die Anzahl der Sekunden, wie lange auf die Ausführung einer SQL-Anweisung gewartet wird, bevor – mit einem Fehler – zur Anwendung zurückgekehrt wird. Der Standardwert ist 0. Der Wert 0 gibt an, dass für das System kein Timeout verwendet wird.|  
|TableName|String|Der Name der Tabelle mit den Daten, die verwendet werden, wenn AccessMode auf Tabellenname festgelegt wird.|  
|LobChunckSize|Integer|Die Segmentgrößenzuordnung für LOB-Spalten.|  
||||  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC Source](../../integration-services/data-flow/odbc-source.md)   
 [Quellen-Editor für ODBC &#40;Seite „Verbindungs-Manager“&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)  
  
  
