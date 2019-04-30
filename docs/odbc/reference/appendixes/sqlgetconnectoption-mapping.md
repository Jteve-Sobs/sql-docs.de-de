---
title: SQLGetConnectOption-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8504709cb2cedb36c62bb9be74ffc8d12a4c811d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188791"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption-Zuordnung
Wenn eine Anwendung ruft **SQLGetConnectOption** über einen ODBC 3.*.x* Treiber, den Aufruf von  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 wird wie folgt zugeordnet:  
  
-   Wenn *fOption* gibt an, eine ODBC-definierten Verbindungsoption, die eine Zeichenfolge, die Treiber-Manager ruft zurückgibt.  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Wenn *fOption* gibt an, eine ODBC-definierten Verbindungsoption, die einen 32-Bit-Ganzzahl-Wert, der Treiber-Manager ruft zurückgibt.  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Wenn *fOption* gibt an, eine treiberdefinierten-Anweisungsoption, die Treiber-Manager-Aufrufe  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 In den vorherigen drei Fällen die *ConnectionHandle* Argument festgelegt ist, mit dem Wert im *Hdbc*, *Attribut* Argument festgelegt ist, mit dem Wert im *fOption* , und die *ValuePtr* Argument festgelegt ist, auf den gleichen Wert wie *PvParam*.  
  
 Für ODBC definierte Zeichenfolge Verbindungsoptionen, des Treiber-Managers festlegt der *Pufferlänge* Argument im Aufruf von **SQLGetConnectAttr** auf die vordefinierte maximale Länge (SQL_MAX_OPTION_STRING_LENGTH); für eine Verbindungsoption keine Zeichenfolgen darstellen *Pufferlänge* auf 0 festgelegt ist.  
  
 Eine ODBC 3.*.x* -Treiber verwenden, der Treiber-Manager nicht mehr überprüft, ob *Option* zwischen SQL_CONN_OPT_MIN und SQL_CONN_OPT_MAX ist, oder ist größer als SQL_CONNECT_OPT_DRVR_START. Der Treiber muss die Gültigkeit der Werte für die Option zu überprüfen.
