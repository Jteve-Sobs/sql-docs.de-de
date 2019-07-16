---
title: Tabelle der Einschränkungen von | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 152a0aa1e8d92424b2f60c49f44888de7d3e528c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939774"
---
# <a name="table-name-limitations"></a>Einschränkungen für Tabellennamen
Tabellennamen können keine gültigen Zeichen (z. B. Leerzeichen) enthalten. Wenn Tabellennamen alle Zeichen mit Ausnahme von Buchstaben, Zahlen und Unterstriche enthalten, muss der Namen getrennt werden, indem Sie es in Back Anführungszeichen (') einschließen.  
  
 Wenn Microsoft Excel-Treibers verwendet wird, und ein Tabellenname wird durch eine datenbankverbindung ein Datenbankverweis nicht qualifiziert, wird die Standarddatenbank impliziert. Wenn Sie ein Namen in Microsoft Excel enthält das "!" Zeichen ist, wird es automatisch eine Übersetzung in das Zeichen "$" stattdessen.  
  
 Der Name der Microsoft Excel-Tabelle, die verweist \<Filename > wird für Microsoft Excel, 3.0 und 4.0-Dateien unterstützt. Der Name der Microsoft Excel-Tabelle, die verweist \<Arbeitsmappe-Name > wird für Microsoft Excel 5.0, 7.0 oder 97-Dateien unterstützt.  
  
 Wenn die dBASE-Treiber verwendet wird, werden Zeichen mit ASCII-Wert größer als 127 zu unterstrichen konvertiert.  
  
 Wenn die Microsoft Access-Treiber verwendet wird, ist der Tabellenname maximal 64 Zeichen umfassen.  
  
 Wenn dBASE, Microsoft Excel 3.0 oder 4.0, Text oder Paradox-Treiber verwendet wird, sollte speziellen MS-DOS-Schlüsselwörter CON "," AUX "," LPT1 "und" LPT2 nicht als Tabellennamen verwendet werden.
