---
title: Vom Assistenten zum Generieren von Skripts unterstützte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35882207de5528147883ed3ebe408344cbd3f7fc
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643425"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Vom Assistenten zum Generieren von Skripts unterstützte Objekte
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Der Assistent zum Generieren und Veröffentlichen von Skripts unterstützt eine Teilmenge der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]unterstützten Objekte.  
  
## <a name="supported-objects"></a>Unterstützte Objekte  
 In der folgenden Tabelle finden Sie die Objekte, die vom Assistenten zum Generieren und Veröffentlichen von Skripts veröffentlicht werden können.  
  
||||||  
|-|-|-|-|-|  
|Anwendungsrolle|Datenbankrolle|Schema|Benutzerdefiniertes Aggregat|Sicht*|  
|Assembly|DEFAULT-Einschränkung|Gespeicherte Prozedur*|Benutzerdefinierter Datentyp|XML-Schemaauflistung|  
|CHECK-Einschränkung|Volltextkatalog|Synonym|Benutzerdefinierte Funktion||  
|CLR-gespeicherte Prozedur (Common Language Runtime)*|Index|Tabelle|Benutzerdefinierte Tabelle||  
|CLR-benutzerdefinierte Funktion|Regel|Benutzer**|Benutzerdefinierter Typ||  
  
 *Ohne Verschlüsselung veröffentlicht.  
  
 **Alle Nicht-Systembenutzer in der Datenbank werden als Rollen veröffentlicht.  
  
  
