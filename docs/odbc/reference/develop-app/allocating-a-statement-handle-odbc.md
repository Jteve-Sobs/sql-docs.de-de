---
title: Zuordnen eines ODBC-Anweisungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d50b0a31aed4935c805ca30620575ccff70d4a0b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077202"
---
# <a name="allocating-a-statement-handle-odbc"></a>Zuordnen eines ODBC-Anweisungshandles
Bevor die Anwendung eine Anweisung ausführen kann, müssen sie wie folgt ein Anweisungshandle zuzuweisen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ Befehls beschäftigt. Es ruft dann **SQLAllocHandle** und übergibt die Adresse dieser Variablen wird das Handle für die Verbindung in der die Anweisung, und die Option SQL_HANDLE_STMT auf zuordnen. Zum Beispiel:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zum Speichern von Informationen über die Anweisung und Aufrufe **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_STMT auf.  
  
3.  Der Treiber ordnet ihre eigene Struktur zum Speichern von Informationen über die Anweisung und gibt das Anweisungshandle Treiber an den Treiber-Manager.  
  
4.  Der Treiber-Manager gibt das Anweisungshandle-Treiber-Manager für die Anwendung in der Anwendungsvariablen zurück.  
  
 Das Anweisungshandle identifiziert, welche Anweisung beim Aufrufen von ODBC-Funktionen verwenden. Weitere Informationen zu Anweisungshandles, finden Sie unter [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md).
