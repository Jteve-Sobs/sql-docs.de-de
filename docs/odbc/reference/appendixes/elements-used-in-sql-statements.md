---
title: Elemente, die in SQL-Anweisungen verwendet werden. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: caf8f68221c1ac14649bf10be0105e1e691c7482
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129956"
---
# <a name="elements-used-in-sql-statements"></a>Elemente, die in SQL-­Anweisungen verwendet werden
Die folgenden Elemente werden in der SQL-Anweisungen, die zuvor aufgeführten verwendet.  
  
## <a name="element"></a>Element  
 *Basis-Table-Identifier* :: = *definiert-Benutzername*  
  
 *Basis-Tabellenname* :: = *Base Tabellenbezeichner*  
  
 *Boolean-Faktor-* :: [NOT] = *primären boolescher Wert*  
  
 *boolean-primary* ::= comparison *-predicate* &#124; ( *search-condition* )  
  
 *Boolean-Begriff* :: = *Boolean-Faktor-* [AND *Boolean-Begriff*]  
  
 *Zeichen-Zeichenfolgenliteral* :: = '' {*Zeichen*}... " (*Zeichen* ist ein beliebiges Zeichen im Zeichensatz der Treiber /-Datenquelle. Um ein einzelnes literale Anführungszeichen (") in ein Zeichen-Zeichenfolgenliteral einzuschließen, verwenden Sie zwei literale Anführungszeichen [" "].)  
  
 *Spalten-ID* :: = *definiert-Benutzername*  
  
 *Spaltenname* :: = [*Tabellenname*.] *-Spalten-ID*  
  
 *comparison-operator* ::= < &#124; > &#124; \<= &#124; >= &#124; = &#124; <>  
  
 *Vergleichsprädikat* :: = *Ausdruck* Vergleichsoperator Ausdruck  
  
 *Datentyp* :: = *-Zeichenfolgen-Datentyps* ( *-Zeichenfolgen-Datentyps* ist einen beliebigen Datentyp aufweisen, die für die Sie die "" DATA_TYPE""-Spalte in der von ' SQLGetTypeInfo ' zurückgegebene Resultset entweder SQL_CHAR ist oder SQL_VARCHAR.)  
  
 *digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *Dynamische Parameter* :: =?  
  
 *Ausdruck* :: = Begriff &#124; Ausdruck {+&#124;-} Begriff  
  
 *Faktor* :: = [ *+* &#124; *-* ]*primären*  
  
 *INSERT-Wert* :: =  
  
 *dynamic-parameter*  
  
 &#124; *literal*  
  
 &#124;NULL  
  
 &#124;BENUTZER  
  
 *Buchstaben* :: = *Kleinbuchstaben Fall Buchstaben &#124; Upper-Case-Buchstaben*  
  
 *Literal* :: = *Zeichen-Zeichenfolgenliteral*  
  
 *Kleinbuchstaben Fall Buchstaben* :: = eine &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; ich &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *Order by-Klausel* :: = ORDER BY *Sortierreihenfolge-Spezifikation* [, *sortierspezifikation*]...  
  
 *primäre* :: = *Spaltenname*  
  
 &#124;*Dynamic-Parameter*  
  
 &#124; *literal*  
  
 &#124;( *Ausdruck* )  
  
 *Search Condition* :: = *Boolean-Begriff* [oder *Suchbedingung*]  
  
 *SELECT-Liste* :: = \* &#124; *Select-Unterliste* [, *Select-Unterliste*]...  (*Select-Liste* darf keine Parameter enthalten.)  
  
 *select-sublist* ::= *expression*  
  
 *Sort-Spezifikation* :: = {*unsigned Integer &#124; Spaltenname*} [*ASC &#124; DESC*]  
  
 *Tabellenbezeichner* :: = *definiert-Benutzername*  
  
 *Tabellenname* :: = *Tabellenbezeichner*  
  
 *Tabellenverweis* :: = *Tabellenname*  
  
 *Tabelle der Verweisliste* :: = *Tabellenverweis* [,*Tabellenverweis*]...  
  
 *term* ::= *factor* &#124; *term* {\*&#124; */* } *factor*  
  
 *nicht signierte Ganzzahl* :: = {*Ziffer*}  
  
 *Upper-Case-Buchstaben* :: = *ein &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; ich &#124; J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; P &#124;Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *user-defined-name* ::= *letter*[*digit* &#124; *letter* &#124; *_* ]...
