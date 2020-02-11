---
title: Einschränkungen der DELETE-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eb2587f733f5042436144f7865627fee576e3d9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096312"
---
# <a name="delete-statement-limitations"></a>Einschränkungen der DELETE-Anweisung
Die DELETE-Anweisung wird für den Microsoft Excel-oder Text-Treiber nicht unterstützt. Beachten Sie, dass die INSERT-Anweisung für den Text Treiber unterstützt wird.  
  
 Der dBase-Treiber unterstützt das Packen einer Tabelle zum Entfernen von "gelöschten" Werten nicht.  
  
 Damit der Paradox-Treiber eine Zeile aus einer Tabelle löschen kann, muss die Tabelle über einen eindeutigen Index verfügen (Paradox-Primärschlüssel).
