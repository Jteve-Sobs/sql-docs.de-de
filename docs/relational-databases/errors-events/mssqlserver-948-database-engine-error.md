---
title: MSSQLSERVER_948 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74dd7dda8c743a9914f800b9cf7844de63b3dae2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636310"
---
# <a name="mssqlserver_948"></a>MSSQLSERVER_948
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|948|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|Nicht verfügbar|  
|Meldungstext|Die '%.*ls'-Datenbank kann nicht geöffnet werden, weil sie die Version %d aufweist. Dieser Server unterstützt Version %d und früher. Ein Herabstufungspfad wird nicht unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
Bestimmte funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirken sich auf die Struktur der Datenbankdateien aus. Wenn Sie eine Datenbank an eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anfügen, ist das Dateiformat möglicherweise mit einer anderen Version von [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht kompatibel.  
  
Dieser Fehler kann beispielsweise verursacht werden, wenn das vardecimal-Speicherformat in einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird und dann versucht wird, die Datenbankdateien in einer niedrigeren Version als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 anzufügen.  
  
## <a name="user-action"></a>Benutzeraktion  
Ermitteln Sie die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf dem ursprünglichen Server ausgeführt wird. Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit der rechten Maustaste auf den Server und dann auf **Eigenschaften**, oder geben Sie in einem Abfragefenster **SELECT @@VERSION** ein. Öffnen Sie die Datenbank mithilfe der ursprünglichen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ermitteln Sie die funktionen, die für die ursprüngliche Datenbank in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktiviert sind. Ändern Sie diese Einstellungen, um mit der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu arbeiten, in der die Datenbank angefügt wird.  
  
