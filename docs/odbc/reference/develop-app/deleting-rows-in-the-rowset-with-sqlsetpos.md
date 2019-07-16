---
title: Löschen von Zeilen im Rowset mit SQLSetPos | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39b70f92f7b239b011cdd4fdd6abd36c27561c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076801"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Löschen von Zeilen im Rowset mit SQLSetPos
Beim Löschvorgang von **SQLSetPos** macht die Datenquelle, die eine oder mehrere ausgewählte Zeilen einer Tabelle zu löschen. Zum Löschen von Zeilen mit **SQLSetPos**, die Anwendung ruft **SQLSetPos** mit *Vorgang* auf SQL_DELETE festgelegt und *RowNumber* legen Sie auf der Anzahl der zu löschenden Zeile. Wenn *RowNumber* gleich 0 ist, werden alle Zeilen im Rowset gelöscht.  
  
 Nach dem **SQLSetPos** zurückgegeben wird, die gelöschte Zeile wird die aktuelle Zeile und des Status SQL_ROW_DELETED. Die Zeile kann nicht verwendet werden, in allen weiteren positionierten Operationen, wie z. B. Aufrufe von **SQLGetData** oder **SQLSetPos**.  
  
 Beim Löschen aller Zeilen im Rowset ( *' RowNumber '* gleich 0 ist), die Anwendung kann verhindern, dass den Treiber bestimmte Zeilen löscht, mit der Zeile Operation-Array, auf die gleiche Weise wie für den Updatevorgang **SQLSetPos** . (Finden Sie unter [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Jede Zeile, die gelöscht wird, sollte eine Zeile sein, die im Resultset vorhanden ist. Wenn die Anwendungspuffer durch Abrufen gefüllt wurden und ein zeilenstatusarray gewahrt wurde, sollte die Werte an jeder Zeilenposition nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.
