---
title: Beispiel für die Diagnose-Treiber-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 95392367b70af3eb820f0943af5dc668783a3fe5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046959"
---
# <a name="driver-manager-diagnostic-example"></a>Beispiel für die Diagnose des Treiber-Managers
Der Treiber-Manager kann auch diagnosemeldungen generieren. Angenommen, eine Anwendung eine ungültige Richtung-Option zum übergeben **SQLDataSources**, der Treiber-Manager möglicherweise formatieren und die folgenden Rückgabewerte von **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Da der Fehler im Treiber-Manager hinzugefügt Präfixe der diagnosemeldung für deren Anbieter ([Microsoft]) und ihres Bezeichners ([ODBC-Treiber-Manager]).
