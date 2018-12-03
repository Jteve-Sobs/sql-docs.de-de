---
title: Installieren von nicht englischsprachigen Versionen von SQL Server Management Studio (SSMS) | Microsoft-Dokumentation
description: Installieren von nicht englischsprachigen Versionen von SQL Server Management Studio (SSMS)
ms.custom: ''
ms.date: 12/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7baf327182cec41ffbd20e75517cc9b944226140
ms.sourcegitcommit: 9e722cc8d10ecbdb93efc2fc1886fe7b20dbc13c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "52282042"
---
# <a name="install-non-english-language-versions-of-sql-server-management-studio-ssms"></a>Installieren von nicht englischsprachigen Versionen von SQL Server Management Studio (SSMS) 

[SSMS ist in einer Reihe von Sprachen erhältlich](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791), jedoch blockiert das SSMS-Installationsprogramm die Installation auf Computern, wenn deren Systemgebietsschema nicht mit der Sprache von SSMS übereinstimmt. 

Die folgenden Anweisungen unterscheiden sich je nach der verwendeten Windows-Version. Die hier folgenden beziehen sich auf Windows 10.

## <a name="install-non-english-ssms-on-a-computer-running-an-english-operating-system-os"></a>Installieren von SSMS in einer anderen Sprache auf einem Computer, der ein englischsprachiges Betriebssystem (OS) ausführt

1. Installieren Sie das Windows-Sprachpaket für die Sprache, die SSMS verwenden soll: 
   - **Einstellungen** > **Zeit und Sprache** > **Region und Sprache** > **Sprache hinzufügen** 
2. Legen Sie jetzt das Gebietsschema des Systems so fest, dass das im vorhergehenden Schritt installierte Sprachpaket verwendet wird, indem Sie auf die soeben installierte Sprache klicken, und wählen Sie dann **Als Standard festlegen** aus. (Nach dem Installieren von SSMS können Sie das Gebietsschema des Systems wieder auf Englisch zurücksetzen.)
3. Sobald das Betriebssystem in der gewünschten Sprache ausgeführt wird, [ist SSMS in verschiedenen Sprachen verfügbar](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791). Verwenden Sie bei der erstmaligen Installation einer neuen SSMS-Sprache das vollständige Paket. Das Upgradepaket können Sie für nachfolgende Installationsvorgänge verwenden.
4. Führen Sie SSMS aus; es sollte in der Sprache angezeigt werden, die Sie im vorhergehenden Schritt installiert haben.
5. Legen Sie das Systemgebietsschema Ihres Computers wieder auf Englisch fest.

## <a name="install-ssms-in-a-language-other-than-the-language-of-the-installed-os"></a>Installieren von SSMS in einer anderen Sprache als der des installierten Betriebssystems

1. Installieren Sie das Windows-Sprachpaket für die Sprache, die SSMS verwenden soll: 
   - **Einstellungen** > **Zeit und Sprache** > **Region und Sprache** > **Sprache hinzufügen** 
2. Legen Sie jetzt das Gebietsschema des Systems so fest, dass das im vorhergehenden Schritt installierte Sprachpaket verwendet wird, indem Sie auf die soeben installierte Sprache klicken, und wählen Sie dann **Als Standard festlegen** aus. 
3. Sobald das Betriebssystem in der gewünschten Sprache ausgeführt wird, [ist SSMS in verschiedenen Sprachen verfügbar](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791). Verwenden Sie bei der erstmaligen Installation einer neuen SSMS-Sprache das vollständige Paket. Das Upgradepaket können Sie für nachfolgende Installationsvorgänge verwenden.
4. Für jede Sprache, die Sie installieren möchten, die nicht mit der Sprache der installierten ersten Version von SSMS übereinstimmt, installieren Sie das entsprechende Sprachpaket für Visual Studio 2015 Shell (Isoliert):
   - Navigieren Sie zu [https://connect.microsoft.com/VisualStudio/ExtendVS](https://connect.microsoft.com/VisualStudio/ExtendVS). Sie müssen sich möglicherweise anmelden und den Prozess zur *Connect-Registrierung* abschließen.
   - Laden Sie das gewünschte Sprachpaket für Visual Studio 2015 Shell (Isoliert) herunter, und installieren Sie es.

   > [!IMPORTANT]
   > Befolgen Sie die vorstehenden Schritte, um das Sprachpaket für Visual Studio 2015 Shell (Isoliert) zu installieren, verwenden Sie nicht den Link **Zusätzliche Sprachen abrufen** unter **Extras** | **Optionen** | **Internationale Einstellungen**. 

5. Führen Sie SSMS aus, und wählen Sie hier die Sprache aus, die Sie verwenden möchten:
   - **Extras** | **Optionen** | **Internationale Einstellungen**
1. Schließen Sie SSMS, und starten Sie es erneut.

## <a name="next-steps"></a>Nächste Schritte

- [Tutorial: SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/tutorials/tutorial-sql-server-management-studio)
