---
title: MSSQLSERVER_17887 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3de0d505f99fd1f8f7da968bde13eb56fe50efc1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915207"
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17887|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Meldungstext|E/A-Abschlussüberwachung (0x%lx) Arbeitsthread 0x%p stellt im Knoten %ld kein Ergebnis bereit. Ungefähre CPU-Belegung: Kernel %I64d Millisek., Benutzer %I64d Millisek., Intervall: %I64d.|  
  
## <a name="explanation"></a>Erklärung  
Kennzeichnet ein mögliches Problem mit der E/A-Abschlussportüberwachung an dem spezifischen Knoten, wenn die E/A-Abschlussroutine für ein Netzwerk-Lese-/Schreibereignis ausgeführt wird. Dieser Fehler wird behoben, wenn die E/A-Abschlussportüberwachung nach der Ausführung der E/A-Abschlussroutine zurückgegeben wird.  
  
## <a name="user-action"></a>Benutzeraktion  
Wenden Sie sich an den Microsoft-Kundendienst (Customer Support Services, CSS).  
  
