---
title: Verwenden von 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 941c821d7622b2364ec1cd417dd9b50302540b95
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088170"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  Unterstützung für 16-Bit-Anwendungen werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Entwickeln Sie stattdessen die 32-Bit oder 64-Bit-Anwendungen.  
  
 Mit der ODBC-Komponente können Sie die 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treiber verwenden. Microsoft® Windows® 95/98 und Microsoft Windows/Windows 2000-Betriebssysteme unterstützen die folgenden Kombinationen von Anwendungen und Treiber:  
  
-   16-Bit-Anwendungen mit 32-Bit-Treibern  
  
-   32-Bit-Anwendungen mit 32-Bit-Treibern  
  
 Mit einer 32-Bit-Anwendung mit einem 16-Bit-Treiber wird nicht unterstützt.  
  
> [!NOTE]  
>  Beginnen mit der Veröffentlichung von ODBC, Version 3.0, wird Windows NT 4.0 unterstützt.  
  
 ODBC umfasst die ODBC-Komponenten erforderlich, um die oben genannten Konfigurationen von "thunking" Dynamic Link Libraries (DLLs), 16-Bit-Adressen in 32-Bit-Adressen zu konvertieren und umgekehrt zu unterstützen. Das Setup-Programm bestimmt, welches Betriebssystem Sie und installiert der ODBC-Komponenten, die von diesem System benötigt wird. Sie können auch auswählen, zum Installieren der ODBC-Komponenten, die von allen Systemen verwendet.  
  
 In den meisten Fällen zu portieren, eine Anwendung oder ein aus 16-Bit-Treiber in 32-Bit umfasst fünf Arten von Änderungen:  
  
-   Änderungen am Code der Behandlung von Nachrichten  
  
-   Wechselt, da ganze Zahlen und Handles 32-Bit sind  
  
-   Änderungen in Aufrufen von Windows für Anwendungsprogrammierschnittstellen (APIs)  
  
-   Änderungen an den Treiber threadsicher machen.  
  
-   Änderungen an ODBC-Komponenten  
  
 Aus einer Anwendung oder den Treiber programmiersicht ist der wesentliche Unterschied zwischen 16-Bit- und 32-Bit-ODBC-Komponenten an, dass sie unterschiedliche Dateinamen besitzen. Aus der Systemperspektive unterscheidet sich die Architektur von jeder Anwendung oder den Treiber-Verbindung, und die Tools zum Verwalten von Datenquellen unterscheiden sich.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
