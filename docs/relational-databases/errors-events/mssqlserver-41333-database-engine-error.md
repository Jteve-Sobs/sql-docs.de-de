---
title: MSSQLSERVER_41333 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4e5e6d6b8e7b8fb62c3e7e8948bad8ecf5b0af2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62716487"
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41333|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Meldungstext|Die folgenden Transaktionen müssen unter Verwendung der Momentaufnahmeisolation auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren zugreifen: RepeatableRead-Transaktionen, Serializable-Transaktionen und Transaktionen, die auf Tabellen zugreifen, die in der RepeatableRead-Isolation oder der Serializable-Isolation nicht speicheroptimiert sind.|  
  
## <a name="explanation"></a>Erklärung  
Es gibt Einschränkungen für den Benutzer der höheren Isolationsstufen zwischen datenträgerbasierten Transaktionen und XTP-Transaktionen.  
  
## <a name="user-action"></a>Benutzeraktion  
Versuchen Sie nicht, Isolationsvorgänge auf hoher Ebene in speicheroptimierten Tabellen (und systemintern kompilierten Prozeduren) und datenträgerbasierten Tabellen durchzuführen.  
  
Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
