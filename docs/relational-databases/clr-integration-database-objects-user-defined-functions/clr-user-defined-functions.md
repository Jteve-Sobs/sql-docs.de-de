---
title: Benutzerdefinierte CLR-Funktionen | Microsoft Docs
description: Mit der SQL Server CLR-Integration können Sie benutzerdefinierte Skalar-, Tabellen- und Aggregatfunktionen in jeder Programmiersprache von .NET Framework erstellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: 0da524de3a21a97daf6e3b2d2e0277631a4467c0
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488270"
---
# <a name="clr-user-defined-functions"></a>CLR-benutzerdefinierte Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Benutzerdefinierte Funktionen sind Routinen, die Parameter annehmen, Berechnungen oder andere Aktionen ausführen und Ergebnisse zurückgeben können. Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] können Sie benutzerdefinierte Funktionen in jeder beliebigen [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Programmiersprache schreiben, beispielsweise in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Es sind zwei Arten von Funktionen verfügbar: Skalarfunktionen, die einen einzigen Wert zurückgeben, und Tabellenwertfunktionen, die einen Satz Zeilen zurückgeben.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [CLR-Skalarwertfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-scalar-valued-functions.md)  
 Beschreibt Implementierungsanforderungen und führt Beispiele für Skalarwertfunktionen an.  
  
 [CLR-Tabellenwertfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
 Erörtert, wie Tabellenwertfunktionen (Table-Valued Functions, TVFs) implementiert und verwendet werden, und beschreibt die Unterschiede zwischen [!INCLUDE[tsql](../../includes/tsql-md.md)]- und CLR-TVFs.  
  
 [Benutzerdefinierte CLR-Aggregate](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)  
 Beschreibt die Implementierung und Verwendung von benutzerdefinierten Aggregaten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Funktionen](../../relational-databases/user-defined-functions/user-defined-functions.md)  
  
  
