---
title: MSSQLSERVER_12329 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ab8f54e274f92e3ff9a320c57bd91b527d474ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62915881"
---
# <a name="mssqlserver12329"></a>MSSQLSERVER_12329
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|12329|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|Meldungstext|Die Datentypen char(n) und varchar(n), die Sortierungen mit einer anderen Codepage als 1252 verwenden, werden bei *construct* nicht unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
 Verwenden Sie die Datentypen char(n) und varchar(n) nicht mit Sortierungen, die eine andere Codepage als 1252 verwenden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Die folgende unerwartete Situation kann zu diesem Fehler führen:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 Verwenden Sie stattdessen:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
