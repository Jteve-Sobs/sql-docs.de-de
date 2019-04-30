---
title: SQLGetConfigMode-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54c8dbed5599952778ca7651acbdb55a21b8f876
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259289"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLGetConfigMode** den Konfigurationsmodus zu wechseln, der angibt, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Argumente  
 *pwConfigMode*  
 [Ausgabe] Zeiger auf den Puffer mit den Konfigurationsmodus zu wechseln. (Siehe "Kommentare".) Der Wert in  *\*PwConfigMode* sind möglich:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetConfigMode** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird verwendet, um zu bestimmen, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen ist. Wenn  *\*PwConfigMode* ODBC_USER_DSN, der DSN ist eine Benutzer-DSN ist, und die Funktion liest aus dem Eintrag der Odbc.ini in HKEY_CURRENT_USER. Wenn es sich um ODBC_SYSTEM_DSN handelt, der DSN ist eine System-DSN, und die Funktion liest aus dem Eintrag der Odbc.ini in HKEY_LOCAL_MACHINE. HKEY_CURRENT_USER wird versucht, wenn es sich um ODBC_BOTH_DSN ist, und schlägt fehl, HKEY_LOCAL_MACHINE verwendet wird.  
  
 In der Standardeinstellung **SQLGetConfigMode** ODBC_BOTH_DSN zurückgibt. Wenn ein Benutzer-DSN oder einen System-DSN durch einen Aufruf erstellt wird **SQLConfigDataSource**, die Funktion setzt den Konfigurationsmodus auf ODBC_USER_DSN "oder" ODBC_SYSTEM_DSN ", um Benutzer und System-DSNs, die beim Ändern eines DSN zu unterscheiden. Vor der Rückgabe, **SQLConfigDataSource** den Konfigurationsmodus auf ODBC_BOTH_DSN zurückgesetzt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Festlegen des Konfigurationsmodus|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
