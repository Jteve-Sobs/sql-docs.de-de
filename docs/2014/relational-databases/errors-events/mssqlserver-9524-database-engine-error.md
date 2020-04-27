---
title: MSSQLSERVER_9524 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16f5876211a987dff593721310ee31667d428b81
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62761665"
---
# <a name="mssqlserver_9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9254|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XMLERR_INVALID_COLUMNSET_XML|  
|Meldungstext|Der angegebene XML-Inhalt entspricht nicht dem erforderlichen XML-Format für Sparsespaltensätze.|  
  
## <a name="explanation"></a>Erklärung  
 Es wurde versucht, einen Spaltensatz zu ändern. Der XML-Inhalt eines Spaltensatzes muss die Formateinschränkungen für Spaltensätze erfüllen. Das allgemeine Format eines Spaltensatzes sieht folgendermaßen aus:  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 Weitere Informationen zu Spaltensätzen finden Sie im Thema "Verwenden von Spaltensätzen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="user-action"></a>Benutzeraktion  
 Korrigieren Sie das XML-Format für den Spaltensatz in der Anweisung.  
  
  
