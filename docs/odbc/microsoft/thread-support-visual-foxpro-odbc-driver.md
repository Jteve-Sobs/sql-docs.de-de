---
title: Thread-Unterstützung (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77187802bb57a832263ec2070564754e87f21345
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62632923"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Threadunterstützung (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC-Treiber ist threadsicher. Zugriff auf Umgebungshandles ( *"hen"* ), Verbindungshandles (*Hdbc*), und Anweisungshandles (*Befehls beschäftigt*) wird in der entsprechenden Semaphoren, um zu verhindern, dass andere Prozesse eingebunden Zugreifen aus, und potenziell ändern internen Datenstrukturen des Treibers.  
  
 In einer Multithreadanwendung, können Sie Abbrechen, eine Funktion, die synchron mit ausgeführt wird, wird ein *Befehls beschäftigt* durch Aufrufen von [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) in einem separaten Thread.  
  
 Der Treiber verwendet einen separaten Thread zum Abrufen von Daten bei der Verwendung von progressive abrufen. Um progressive abrufen für eine Datenquelle zu verwenden, wählen Sie die **rufen Sie Daten im Hintergrund** auf das Kontrollkästchen der [Dialogfeld ODBC-Visual FoxPro-Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) oder das Schlüsselwort BackgroundFetch in Ihrer Verbindung verwenden Zeichenfolge. Verwenden Sie abrufen im Hintergrund, wenn Sie den Treiber von Multithread-Anwendungen aufrufen. Weitere Informationen zu Schlüsselwörtern für Verbindungszeichenfolgen-Attribut, finden Sie unter [Verbindungszeichenfolgen verwenden](../../odbc/microsoft/using-connection-strings.md).  
  
 Weitere Informationen zu Threads und **SQLCancel**, finden Sie unter [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) in die *ODBC Programmer's Reference*.
