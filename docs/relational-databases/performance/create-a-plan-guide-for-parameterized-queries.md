---
title: Erstellen einer Planhinweisliste für parametrisierte Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 45a57f45eae2a54d73e08064b9a02446871f8400
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67946954"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a>Erstellen einer Planhinweisliste für parametrisierte Abfragen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Eine TEMPLATE-Planhinweisliste zur Übereinstimmung mit eigenständigen Abfragen, die in einer angegebenen Form parametrisiert werden.  
  
 Im folgenden Beispiel wird eine Planhinweisliste erstellt, die mit einer beliebigen Abfrage übereinstimmt, die in einer bestimmten Form parametrisiert wird. Außerdem wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewiesen, die Parametrisierung der Abfrage zu erzwingen. Die folgenden beiden Abfragen sind syntaktisch gleichwertig, unterscheiden sich jedoch in ihren konstanten Literalwerten.  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 Dies ist die Planhinweisliste für die parametrisierte Form der Abfrage:  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 Im vorhergehenden Beispiel entspricht der Wert des `@stmt` -Parameters der parametrisierten Form der Abfrage. Die einzig zuverlässige Möglichkeit, diesen Wert für die Verwendung in sp_create_plan_guide abzurufen, ist die gespeicherte Systemprozedur [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) . Mithilfe des folgenden Skripts können Sie die parametrisierte Abfrage abrufen und anschließend eine Planhinweisliste für die Abfrage erstellen.  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  Der Wert der konstanten Literale in dem an `@stmt` übergebenen `sp_get_query_template` -Parameter kann sich auf den Datentyp auswirken, der für den Parameter, der das Literal ersetzt, gewählt wird. Dies wiederum beeinflusst den Planhinweislistenabgleich. Möglicherweise müssen mehrere Planhinweislisten für verschiedene Parameterwertbereiche erstellt werden.  
  
 Sie haben auch die Möglichkeit, TEMPLATE-Planhinweislisten zusammen mit SQL-Planhinweislisten zu verwenden. Beispielsweise können Sie eine TEMPLATE-Planhinweisliste erstellen, um sicherzustellen, dass eine bestimmte Abfrageklasse parametrisiert wird. Anschließend können Sie eine SQL-Planhinweisliste für die parametrisierte Form dieser Abfragen erstellen.  
  
  
