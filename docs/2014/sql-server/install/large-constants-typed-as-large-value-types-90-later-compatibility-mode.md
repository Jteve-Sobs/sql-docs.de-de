---
title: Große Konstanten werden als Typen mit umfangreichen Werten im Kompatibilitätsmodus 90 oder höher eingegeben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c7aded5577e28d94f42e108e46bb8a9c3cd6020
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094089"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a>Große Konstanten werden als Typen mit großen Werten im Kompatibilitätsmodus 90 oder höher eingegeben
  Der Upgrade Advisor hat vorhandene große Konstanten erkannt. Zeichenfolgenkonstanten und binäre Konstanten, die größer als 8.000 Bytes sind, werden in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] als Datentyp für umfangreiche Objekte behandelt. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höheren Versionen werden große Zeichen-, Unicode- und binäre Konstanten als Typen mit großen Werten eingegeben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Wenn Zeichenfolgenfunktionen wie CHARINDEX und PATINDEX mit Zeichenfolgen- oder binären Konstanten verwendet werden, die 8.000 Bytes übersteigen, gibt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] den Fehler Nummer 8116 und [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höhere Versionen den Fehler Nummer 8152 zurück.  
  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] geben die Zeichenfolgenfunktionen den Fehler 8116 zurück, wenn sie mit den Datentypen `text`, `ntext` und `image` verwendet werden.  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höheren Versionen werden die großen Konstanten wie die Datentypen `varchar(max)`, `nvarchar(max)` und `varbinary(max)` behandelt. Diese Datentypen sind mit Zeichenfolgenfunktionen kompatibel.  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höheren Versionen gehen Zeichenfolgenfunktionen wie CHARINDEX und PATINDEX davon aus, dass die Zeichenfolge, die die zu findende Abfolge von Zeichen enthält, kleiner als 8.000 Bytes ist. Aus diesem Grund wird der Fehler 8152 für CHARINDEX und PATINDEX ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
