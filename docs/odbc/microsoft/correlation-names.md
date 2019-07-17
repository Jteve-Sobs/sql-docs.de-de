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
ms.openlocfilehash: 535c169123923cdb36c355e098f6e0c55ebb9d56
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127306"
---
# <a name="correlation-names"></a>Korrelationsnamen
Abhängige Namen werden vollständig unterstützt, einschließlich der in der Tabellenliste. In der folgenden Zeichenfolge, für den E1 beispielsweise der abhängige Name für die Tabelle Emp ist:  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
