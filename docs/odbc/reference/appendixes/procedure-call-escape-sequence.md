---
title: Procedure Call Escape Sequence | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aa936eb9f8ef3328945d4ece63fb36432a5fd618
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100591"
---
# <a name="procedure-call-escape-sequence"></a>Prozeduraufruf-Escapesequenz
ODBC verwendet Escapesequenzen für Prozeduraufrufe an. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
 **{** [? =]**Aufrufen** *Prozedurname*[ **(** [*Parameter*] [, [*Parameter*]]... **)** ] **}**  
  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-Prozedur-Escapesequenz* :: =  
  
 &#124;*Initiator der ODBC-esc* [? =] aufrufen *Prozedur ODBC-esc-Terminator*  
  
 *Prozedur* :: = *Prozedurname* &#124; *Prozedurname* (*Prozedurparameterliste*)  
  
 *Prozedur-ID* :: = *definiert-Benutzername*  
  
 *Name der Prozedur* :: = *Prozedur-ID*  
  
 &#124;*Besitzernamen*. *Prozedur-ID*  
  
 &#124;*Katalognamen Katalogtrennzeichen* *Prozedur-ID*  
  
 &#124;*Katalognamen Katalogtrennzeichen* [*Besitzernamen*]. *Prozedur-ID*  
  
 (Die dritte Syntax ist nur gültig, wenn die Datenquelle Besitzer nicht unterstützt.)  
  
 *Besitzername* :: = *definiert-Benutzername*  
  
 *Katalogname* :: = *definiert-Benutzername*  
  
 *Katalogtrennzeichen* :: = {*implementierungsdefinierte*}  
  
 (Das Katalogtrennzeichen zurückgegeben wurde **SQLGetInfo** mit der Option SQL_CATALOG_NAME_SEPARATOR Informationen.)  
  
 *Prozedur-Parameter-List* :: = *-Parameter der Prozedur*  
  
 &#124;*Prozedurparameter*, *Prozedurparameterliste*  
  
 *Prozedurparameter* :: = *dynamische Parameter* &#124; *literal* &#124; *leeren Zeichenfolge*  
  
 *leeren Zeichenfolge* :: =  
  
 *Initiator der ODBC-esc* :: = {  
  
 *ODBC-esc-Terminator* :: =}  
  
 (Wenn Parameter einer Prozedur eine leere Zeichenfolge ist, verwendet die Prozedur den Standardwert für diesen Parameter.)  
  
 Um zu bestimmen, ob die Datenquelle, Verfahren unterstützt und der Treiber die Aufrufsyntax des ODBC-Prozedur unterstützt, eine Anwendung aufrufen kann **SQLGetInfo** mit dem Typ der SQL_PROCEDURES-Informationen.
