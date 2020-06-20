---
title: Setup Rolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 555c6946a9732d478d9e7dca76b84ce17d0e90e2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036272"
---
# <a name="setup-role"></a>Setuprolle
  Geben Sie auf dieser Seite an, ob einzelne Funktionen über die Seite Funktionsauswahl ausgewählt werden sollen oder ob die Installation unter Verwendung einer Setuprolle ausgeführt werden soll.  
  
 Eine `setup role` ist eine unveränderliche Auswahl aller Funktionen und freigegebenen Komponenten, die zur Implementierung einer vordefinierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfiguration erforderlich sind.  
  
## <a name="options"></a>Optionen  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Funktions Installation**  
 Verwenden Sie diese Option, um einzelne Funktionen und freigegebene Komponenten auszuwählen. Die Instanzfunktionen beinhalten Datenbank-Engine-Dienste, Analysis Services (einheitlicher Modus) und Reporting Services.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerPivot für SharePoint**  
 Verwenden Sie diese Option, um Analysis Services-Serverkomponenten in einer SharePoint 2010-Farm zu installieren. Durch diese Option werden der PowerPivot-Systemdienst und der Analysis Services-Server in einer Farm bereitgestellt, wodurch Abfrage- und Datenverarbeitungsvorgänge für veröffentlichte Excel-Arbeitsmappen ermöglicht werden, die eingebettete [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten enthalten.  
  
 Optional können Sie der Installation eine relationale Datenbank-Engine-Instanz hinzufügen, wenn Sie diese benötigen, um Datenbanken in einer SharePoint-Farm zu hosten. Wenn die Farm bereits konfiguriert ist, können Sie diese Option überspringen.  
  
 Nach Beenden des Setups müssen Sie die Software mit einem der folgenden Ansätze konfigurieren: PowerPivot-Konfigurationstool, PowerShell-Cmdlets oder SharePoint 2010-Zentraladministration. Im Gegensatz zu vorherigen Versionen werden beim Setup keine Konfigurationsaufgaben für eine PowerPivot-Installation mehr ausgeführt.  
  
 Eine rollenbasierte Installation enthält keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot für Excel-Clientanwendung. Die Clientanwendung wird getrennt installiert.  
  
 **Alle Funktionen mit Standardwerten**  
 Wählen Sie diese Setuprolle aus, um alle für diese Version verfügbaren Funktionen zu installieren. Beachten Sie, dass PowerPivot für SharePoint von dieser Rolle ausgeschlossen wird. Sie müssen diese Funktion mithilfe der PowerPivot für SharePoint-Setuprolle installieren.  
  
 Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] wird für den Start unter Verwendung des Kontos **NT-AUTORITÄT\NETZWERKDIENST** konfiguriert. Der aktuelle Benutzer wird als Mitglied der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**-sysadmin** -Rolle bereitgestellt. Durch diese Option festgelegte Werte können durch Angabe zusätzlicher Befehlszeilenparameter überschrieben werden.  
  
 Sofern das Betriebssystem nicht als Domänencontroller fungiert, verwenden die Datenbank-Engine, Reporting Services und Integration Services standardmäßig das Konto NT-AUTORITÄT\NETZWERKDIENST, und das Startprogramm für den SQL-Volltextfilterdaemon verwendet das Konto NT-AUTORITÄT\LOKALER DIENST.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von PowerPivot für SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906)   
 [Hardware-und Software Anforderungen (PowerPivot für SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823)   
 [Funktionsauswahl](../../../2014/sql-server/install/feature-selection.md)  
  
  
