---
description: Datenanbieter
title: Datenanbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: rothja
ms.author: jroth
ms.openlocfilehash: cb448efeb0b78ba6cb29d9acff661308a6bf14bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453582"
---
# <a name="data-providers"></a>Datenanbieter
Datenanbieter stellen unterschiedliche Datenquellen wie SQL-Datenbanken, indizierte sequenzielle Dateien, Kalkulations Tabellen, Dokument Speicher und e-Mail-Dateien dar. Anbieter machen Daten einheitlich verfügbar, indem eine gängige Abstraktion, die als Rowset bezeichnet wird.  
  
 ADO ist leistungsstark und flexibel, da es eine Verbindung mit einem von mehreren unterschiedlichen Datenanbietern herstellen kann und immer noch dasselbe Programmiermodell verfügbar macht, unabhängig von den spezifischen Features eines beliebigen Anbieters. Da jedoch jeder Datenanbieter eindeutig ist, variiert die Interaktion der Anwendung mit ADO je nach Datenanbieter.  
  
 Beispielsweise unterscheiden sich die Funktionen und Features des OLE DB Anbieters für SQL Server, der für den Zugriff auf Microsoft SQL Server-Datenbanken verwendet wird, erheblich von denen des Microsoft OLE DB-Anbieters für die Internet Veröffentlichung, der für den Zugriff auf Dateispeicher auf einem Webserver verwendet wird.
