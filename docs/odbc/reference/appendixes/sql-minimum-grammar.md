---
title: Minimale SQL-Grammatik | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26cf76200010edae7f85993ec33eb3722f35e94e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270499"
---
# <a name="sql-minimum-grammar"></a>Minimale SQL-Grammatik
Dieser Abschnitt beschreibt die minimale SQL-Syntax, die ein ODBC-Treiber unterstützen muss. Die in diesem Abschnitt erläuterten Syntax ist eine Teilmenge der Syntax der Eintrag auf der SQL-92.  
  
 Eine Anwendung kann alle von der Syntax in diesem Abschnitt verwenden und sicher sein, dass keine ODBC-kompatiblen Treiber diese Syntax unterstützt. Um zu bestimmen, ob zusätzliche Funktionen der SQL-92 in diesem Abschnitt nicht unterstützt werden, sollte die Anwendung aufrufen **SQLGetInfo** mit dem Typ der SQL_SQL_CONFORMANCE-Informationen. Auch wenn der Treiber nicht auf alle SQL-92-Standards entspricht, kann eine Anwendung immer noch die in diesem Abschnitt erläuterten Syntax verwenden. Wenn ein Treiber eine SQL-92-Ebene entspricht, unterstützt andererseits, all-Syntax in dieser Ebene enthalten. Dies schließt die Syntax in diesem Abschnitt, da die minimale Grammatik, die hier beschriebenen reine Teil der untersten Ebene der SQL-92-Standards ist. Sobald die Anwendung weiß, dass die SQL-92-Ebene unterstützt, es kann zu bestimmen, ob eine Funktion auf höherer Ebene (sofern vorhanden) durch den Aufruf unterstützt wird **SQLGetInfo** mit individuellen Typs, der diese Funktion entspricht.  
  
 Treiber, die Arbeit nur mit schreibgeschützten Datenquellen unterstützen möglicherweise nicht die Teile der Grammatik, die in diesem Abschnitt enthalten, mit denen Daten geändert. Eine Anwendung kann bestimmen, wenn eine Datenquelle durch den Aufruf schreibgeschützt und ist **SQLGetInfo** mit dem Typ der SQL_DATA_SOURCE_READ_ONLY-Informationen.  
  
## <a name="statement"></a>-Anweisung.  
 *create-table-statement* ::=  
  
 CREATE TABLE *Basis-Table-Name*  
  
 (*Spaltenbezeichner Datentyp* [*, Spalten-ID Datentyp*]...)  
  
> [!IMPORTANT]  
>  Als eine *Datentyp* in einer *-Anweisung create Table*, Anwendungen müssen einen Datentyp aus der TYPE_NAME-Spalte des Resultsets vom verwenden **SQLGetTypeInfo**.  
  
 *delete-statement-searched* ::=  
  
 DELETE FROM *Tabellenname* [, in denen *Suchbedingung*]  
  
 *drop-table-statement* ::=  
  
 DROP TABLE *Basis-Table-Name*  
  
 *insert-statement* ::=  
  
 INSERT INTO *Tabellenname* [( *Spaltenbezeichner* [, *Spaltenbezeichner*]...)]      Werte (*Wert einfügen*[, *Wert einfügen*]...)  
  
 *select-statement* ::=  
  
 Wählen Sie [alle &#124; DISTINCT] *Select-Liste*  
  
 VON *Tabellenliste-Referenz*  
  
 [, In denen *Suchbedingung*]  
  
 [*order-by-clause*]  
  
 *statement* ::= *create-table-statement*  
  
 &#124; *delete-statement-searched*  
  
 &#124; *drop-table-statement*  
  
 &#124; *insert-statement*  
  
 &#124; *select-statement*  
  
 &#124; *update-statement-searched*  
  
 *update-statement-searched*  
  
 UPDATE *Tabellenname*  
  
 Legen Sie *Spaltenbezeichner* = {*Ausdruck* &#124; NULL}  
  
 [, *Spaltenbezeichner* = {*Ausdruck* &#124; NULL}]...  
  
 [, In denen *Suchbedingung*]  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Elemente, die in SQL-­Anweisungen verwendet werden](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Datentypunterstützung](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Parameterdatentypen](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md)
