---
title: SQLTransact-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2082a97b24284afcc879048bb08e86a7b2bb3ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070112"
---
# <a name="sqltransact-mapping"></a>SQLTransact-Zuordnung
**SQLTransact** wurde ersetzt durch **SQLEndTran**. Der Hauptunterschied zwischen den beiden Funktionen ist, **SQLEndTran** enthält ein Argument *HandleType*, der angibt, dass der Umfang der Aufgaben durchgeführt werden. Die *HandleType* -Argument kann angeben, die Umgebung oder dem Verbindungshandle. Der folgende Aufruf von **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 wird zugeordnet  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Wenn *ConnectionHandle* ist nicht gleich SQL_NULL_HDBC. Die *ConnectionHandle* Argument festgelegt ist, auf den Wert der *Hdbc*.  
  
 **SQL_Transact** zugeordnet ist  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Wenn *ConnectionHandle* SQL_NULL_HDBC entspricht. Die *EnvironmentHandle* Argument festgelegt ist, auf den Wert der *Henv*.  
  
 In beiden Fällen die *' CompletionType '* Argument festgelegt ist, auf den gleichen Wert wie *fType*.
