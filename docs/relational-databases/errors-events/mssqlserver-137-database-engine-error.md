---
title: MSSQLSERVER_137 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 617fed01d22eebba515966a0c820824d6fd39896
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62859955"
---
# <a name="mssqlserver137"></a>MSSQLSERVER_137
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|137|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P_SCALAR_VAR_NOTFOUND|  
|Meldungstext|Die "%.*ls"-Skalarvariable muss deklariert werden.|  
  
## <a name="explanation"></a>Erklärung  
Dieser Fehler tritt auf, wenn in einem SQL-Skript eine Variable verwendet wird, ohne dass die Variable zuerst deklariert wurde. Im folgenden Beispiel wird beispielsweise Fehler 137 für die SET- und die SELECT-Anweisung zurückgegeben, weil **@mycol** nicht deklariert wurde.  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
Eine der etwas komplizierteren Ursachen für diesen Fehler ist u. a. die Verwendung einer Variablen, die außerhalb der EXECUTE-Anweisung deklariert wurde. Angenommen, die in der SELECT-Anweisung angegebene Variable **@mycol** ist für die SELECT-Anweisung lokal. Das bedeutet, dass sie sich außerhalb der EXECUTE-Anweisung befindet.  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20);  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie, ob alle in einem SQL-Skript verwendeten Variablen deklariert wurden, bevor sie an anderer Stelle im Skript verwendet werden.  
  
Schreiben Sie das Skript um, sodass es nicht auf Variablen in der EXECUTE-Anweisung verweist, die außerhalb davon deklariert wurden. Beispiel:  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20) ;  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>Weitere Informationen  
[EXECUTE &#40;Transact-SQL&#41;](~/t-sql/language-elements/execute-transact-sql.md)  
[SET-Anweisungen &#40;Transact-SQL&#41;](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
