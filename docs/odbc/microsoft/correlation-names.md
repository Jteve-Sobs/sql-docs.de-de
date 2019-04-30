---
title: Abhängige Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b8a253f9d252beb42080d2085adb962206ebd94
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232310"
---
# <a name="correlation-names"></a>Korrelationsnamen
Abhängige Namen werden vollständig unterstützt, einschließlich der in der Tabellenliste. In der folgenden Zeichenfolge, für den E1 beispielsweise der abhängige Name für die Tabelle Emp ist:  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
