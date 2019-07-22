---
title: MSSQLSERVER_41359 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fd26d20fc887266c3efa341e546b30d4a171a1ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123197"
---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41359|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Meldungstext|Eine Abfrage, die auf speicheroptimierte Tabellen mit der READ COMMITTED-Isolationsstufe zugreift, kann auf datenträgerbasierte Tabellen nicht zugreifen, wenn die Datenbankoption READ_COMMITTED_SNAPSHOT auf ON gesetzt ist. Geben Sie eine unterstützte Isolationsstufe für die speicheroptimierte Tabelle mithilfe eines Tabellentipps wie WITH (SNAPSHOT) an.|  
  
## <a name="explanation"></a>Erklärung  
Die Datenbank mit READ_COMMITTED_SNAPSHOT=ON unterstützt nicht die Transaktionen, die sowohl auf speicheroptimierte Tabellen als auch auf datenträgerbasierte Tabellen zugreifen.  
  
## <a name="user-action"></a>Benutzeraktion  
Setzen Sie READ_COMMITTED_SNAPSHOT auf OFF oder stellen Sie eine unterstützte Isolationsstufe für die speicheroptimierte Tabelle mithilfe eines Tipps auf Tabellenebene wie WITH (SNAPSHOT) bereit. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
