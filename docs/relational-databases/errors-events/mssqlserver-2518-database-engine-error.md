---
title: MSSQLSERVER_2518 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca6a654894304197357cbe244be60f9b9a58f789
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138514"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2518|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Meldungstext|Objekt-ID O_ID (Objekt "O_NAME"): Berechnete Spalten und benutzerdefinierte Typen können für dieses Objekt nicht überprüft werden, da die Common Language Runtime (CLR) deaktiviert ist.|  
  
## <a name="explanation"></a>Erklärung  
Diese Informationsmeldung gibt an, dass der Abfrageprozessor DBCC kein internes Objekt bereitstellen konnte, um die Auswertung berechneter Spalten und CLR-benutzerdefinierter Typen (Common Language Runtime) zu ermöglichen. Dieses Problem ist aufgetreten, weil eine der Spalten CLR beinhaltet, aber CLR nicht aktiviert ist. Das interne Objekt deckt alle Spalten ab. Daher verhindert das Unvermögen, eine einzelne Spalte auszuwerten, das Erstellen des internen Objekts. Das bedeutet, dass berechnete Spalten nicht auf Richtigkeit überprüft werden oder verwendet werden, wenn DBCC die Konsistenz zwischen Indizes und Basistabellen überprüft.  
  
## <a name="user-action"></a>Benutzeraktion  
Aktivieren Sie CLR, und führen Sie die DBCC-Anweisung erneut aus.  
  
## <a name="see-also"></a>Weitere Informationen  
[Aktivieren der CLR-Integration](~/relational-databases/clr-integration/clr-integration-enabling.md)  
  
