---
title: Azure Data Studio SQL Server Profiler-Erweiterung | Microsoft-Dokumentation
description: SQL Server Profiler-Erweiterung (Vorschauversion) für Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 7f5d1731cfb126b2dbaa259b89b327951d384e1a
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356011"
---
# <a name="sql-server-profiler-extension-preview"></a>SQL Server Profiler-Erweiterung (Vorschau)

Die SQL Server Profiler-Erweiterung (Vorschau) bietet eine einfache SQL Server-Ablaufverfolgung-Lösung, die für Sie ähnlich wie SQL Server Management Studio (SSMS) Profiler außer mit XEvents erstellt wurden. SQL Server Profiler ist sehr einfach zu verwenden und verfügt über gute Standardwerte für die am häufigsten verwendeten Konfigurationen für die Ablaufverfolgung. Die UX ist optimiert für Ereignisse durchsuchen und Anzeigen der zugehörigen Texts der Transact-SQL (T-SQL). Die SQL Server Profiler für Azure Data Studio wird vorausgesetzt, gute Standardwerte für das Sammeln von T-SQL-Ausführung-Aktivitäten mit eine benutzerfreundliche UX. Diese Erweiterung ist derzeit in der Vorschau.

**Allgemeine SQL Profiler Anwendungsfälle:**

- Schrittweises Untersuchen problematischer Abfragen, um die Ursache des Problems zu ermitteln.
- Suchen und Diagnostizieren von Abfragen, die sehr langsam ausgeführt werden.
- Erfassen der Transact-SQL-Anweisungen, die zu einem Problem führen.
- Überwachen die Leistung des SQL Servers, arbeitsauslastungen zu optimieren.
- Korrelieren von Leistungsindikatoren zur Diagnose von Problemen.


## <a name="install-the-sql-server-profiler-extension"></a>Installieren Sie die SQL Server Profiler-Erweiterung

1. Um Erweiterungs-Manager öffnen und den Zugriff auf die verfügbaren Erweiterungen, wählen Sie das Symbol für Erweiterungen oder **Erweiterungen** in die **Ansicht** Menü.
2. Wählen Sie eine verfügbare Erweiterung, um seine Details anzuzeigen.

   ![Profiler-Erweiterungs-manager](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Wählen Sie die gewünschte Erweiterung und **installieren** es.
2. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).

## <a name="start-profiler"></a>Starten von Profiler

1. Um den Profiler zu starten, stellen Sie zunächst eine Verbindung mit einem Server, auf der Registerkarte "Server".
2. Nachdem Sie eine Verbindung herstellen, geben Sie **Alt + P** Profiler zu starten.
3. Geben Sie zum Starten von Profiler **Alt + S.** Nun können Sie erweiterte Ereignisse angezeigt.
    ![Profiler-Erweiterungs-manager](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Um Profiler beenden möchten, geben **Alt + S.** Dieses Hotkeys ist eine Umschaltoption.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Profiler und erweiterte Ereignisse finden Sie unter [erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





