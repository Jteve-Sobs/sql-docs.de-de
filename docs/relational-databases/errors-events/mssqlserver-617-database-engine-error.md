---
title: MSSQLSERVER_617 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5078c98445587dbf8c8b99fa18fed4df2ca5846
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951669"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|617|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NODESHASH|  
|Meldungstext|Der Deskriptor für die Objekt-ID %ld in der Datenbank mit der ID %d wurde in der Hashtabelle beim Versuch, ihn aus dieser zu entfernen, nicht gefunden. In einer Arbeitstabelle fehlt ein Eintrag. Führen Sie die Abfrage erneut aus. Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn erneut.|  
  
## <a name="explanation"></a>Erklärung  
SQL Server kann die Arbeitstabelle für einen bestimmten Eintrag nicht finden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn dann erneut.  
  
2.  Führen Sie die Abfrage erneut aus.  
  
