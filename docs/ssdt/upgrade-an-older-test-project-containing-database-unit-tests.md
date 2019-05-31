---
title: Durchführen eines Upgrades für ein älteres Testprojekt mit Datenbankkomponententests | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 42782ff3-e8cf-4c9d-8dac-a95b236edfc4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d1b91df1ecce9749ebdec3515a339ac31f2507b7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65101977"
---
# <a name="upgrade-an-older-test-project-containing-database-unit-tests"></a>Upgrade eines älteren Testprojekts, das Datenbankkomponententests enthält
Sie können ein Upgrade für ein älteres Testprojekt, das in Visual Studio 2010 erstellt wurde und Datenbankkomponententests enthält, für die Verwendung der neuen Laufzeit und Tools für SQL Server Data Tools-Datenbankkomponententests durchführen. Nachdem Sie ein Upgrade für ein älteres Projekt durchgeführt haben, können Sie dem Projekt SQL Server-Komponententests hinzufügen (weitere Informationen finden Sie unter [Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)).  
  
> [!TIP]  
> Bei Verwendung von Visual Studio 2010 sollten Sie keine Komponententests mithilfe der älteren Vorlage für Datenbankkomponententests hinzufügen, nachdem Sie einem Testprojekt SQL Server-Komponententests hinzugefügt haben. Andernfalls müssen Sie das Projekt erneut konvertieren, damit die Tests ordnungsgemäß ausgeführt werden.  
  
Wenn Sie über ein Testdatenbankprojekt verfügen, dass in einem Release vor Visual Studio 2010 erstellt wurde, finden Sie weitere Informationen unter [How to: Upgrade Database Unit Tests from Previous Releases of Visual Studio (Vorgehensweise: Upgraden von Datenbankkomponententests von Vorgängerversionen von Visual Studio)](https://msdn.microsoft.com/library/dd193412(VS.100).aspx), wenn Sie Ihr Datenbankprojekt auf Visual Studio 2010 upgraden möchten, bevor Sie das Projekt auf SQL Server Data Tools upgraden.  
  
### <a name="initiating-an-upgrade"></a>Initiieren eines Upgrades  
  
-   Sie können ein Projektupgrade über das Kontextmenü eines Testprojekts starten.  
  
    In einigen Fällen wird in SQL Server Data Tools ein Dialogfeld angezeigt, in dem Sie ein Upgrade für ein Testprojekt initiieren können.  
  
-   Durch das Projektupgrade wird der Assemblyverweis auf das ältere Datenbanktestframework entfernt und ein Verweis auf das neue Framework und eine Adapterassembly hinzugefügt. Die Datei app.config wird ebenfalls aktualisiert.  
  
    > [!NOTE]  
    > Wenn das Testprojekt sowohl über die Codedatei „DatabaseSetup“ als auch über die Codedatei „SQLDatabaseSetup“ verfügt, wird die Datei „DatabaseSetup“ durch die Durchführung eines Upgrades für das Projekt auf SQL Server Data Tools aus dem Build ausgeschlossen. Sie können die Datei DatabaseSetup entfernen, wenn sie aus dem Build ausgeschlossen wird.  
  
-   Nach der Konvertierung verwenden vorhandene Datenbankkomponententests, die mit der älteren Vorlage erstellt wurden, Typen in der Adapterassembly, um auf das neue Framework zuzugreifen. Die Verwendung einer Adapterassembly deutet darauf hin, dass die Testskripts und der Code durch den Upgradevorgang nicht geändert wurden. Wenn Sie dem Projekt einen SQL Server-Komponententest hinzufügen, verweist der neue Test direkt und nicht über einen Adapter auf das neue Framework. Sie können vorhandenen Code manuell für die Verwendung des neuen Frameworks aktualisieren, um Konsistenz mit neuen Tests zu gewährleisten. Dies ist jedoch nicht zwingend erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
