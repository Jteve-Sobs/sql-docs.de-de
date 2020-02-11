---
title: 'Jet: Datums-, Uhrzeit-und Zeitstempel Literale | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bb7f0fb02049b6d2f1897c4f495035aee2858f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085493"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Datums-, Zeit- und Zeitstempelliterale
Für maximale Interoperabilität sollten Anwendungen Datums Literale im kanonischen ODBC-Format mithilfe der escapeklausel-Syntax übergeben:  
  
-   Für Datums Literale {d '*value*'}, wobei *Valu*e das Format "yyyy-mm-dd" hat.  
  
-   Für Zeit Literale {t '*value*'}, wobei *Valu*e im Format ' HH: mm: SS ' liegt.  
  
 Für Zeitstempel-Literale {TS '*value*'}, wobei *Valu*e das Format ' yyyy-mm-dd hh: mm: SS [. f...] ' aufweist.
