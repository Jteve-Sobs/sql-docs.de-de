---
title: Installieren von PowerPivot über die Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e84b6e148774fc9b48b6174fa8be87579290fec4
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52393413"
---
# <a name="install-powerpivot-from-the-command-prompt"></a>Installieren von PowerPivot über die Eingabeaufforderung
  Sie können Setup in der Befehlszeile ausführen, um SQL Server PowerPivot für SharePoint zu installieren. Sie müssen den `/ROLE`-Parameter in den Befehl einschließen und den `/FEATURES`-Parameter ausschließen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 SharePoint Server 2010 Enterprise Edition mit Service Pack 1 (SP1) muss installiert sein.  
  
 Sie müssen über Domänenbenutzerkonten verfügen, um Analysis Services bereitzustellen.  
  
 Der Computer muss der gleichen Domäne wie die SharePoint-Farm hinzugefügt werden.  
  
##  <a name="Commands"></a> / ROLE-basierte Installationsoptionen  
 Für PowerPivot für SharePoint-Bereitstellungen wird der `/ROLE`-Parameter anstelle des `/FEATURES`-Parameters verwendet. Gültige Werte sind:  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 Beide Rollen installieren Anwendungs-, Konfigurations- und Bereitstellungsdateien, die die Ausführung von PowerPivot für SharePoint in einer SharePoint-Farm ermöglichen. Die Angabe von beiden Rolle bewirkt, dass Setup Hardware- und Softwareanforderungen für die SharePoint-Integration überprüft.  
  
 Die vorhandene Farmoption geht davon aus, dass eine SharePoint-Farm bereits vorhanden ist. Die neue farmoption geht davon aus, dass Sie eine neue Farm erstellen; Es unterstützt das Hinzufügen einer Datenbank-Engine-Instanz in die Befehlszeilensyntax, damit Sie die Datenbank-Engine-Instanz als Datenbankserver der Farm verwenden können.  
  
 Im Gegensatz zu den vorherigen Versionen werden alle Serverkonfigurationstasks nach der Installation ausgeführt. Wenn Sie Installations- und Konfigurationsschritte automatisieren, können Sie den Server mithilfe von PowerShell konfigurieren. Weitere Informationen finden Sie unter [PowerPivot-Konfiguration, die mithilfe von Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  
  
## <a name="example-commands"></a>Beispielbefehle  
 Die folgenden Beispiele veranschaulichen die Verwendung jeder Option. Beispiel 1 `SPI_AS_ExistingFarm`.  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 Beispiel 2 zeigt `SPI_AS_NewFarm`. Beachten Sie, dass es Parameter zum Bereitstellen der Datenbank-Engine einschließt.  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="Join"></a> Ändern der Befehlssyntax  
 Ändern Sie die Beispielbefehlssyntax mithilfe der folgenden Schritte.  
  
1.  Kopieren Sie den folgenden Befehl in Editor:  
  
    ```  
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     Der `/q`-Parameter führt Setup im stillen Modus aus, beim dem die Benutzeroberfläche unterdrückt wird.  
  
     `/IAcceptSQLServerLicenseTerms` wird benötigt, wenn der `/q`-Parameter oder der `/qs`-Parameter für nicht beaufsichtigte Installationen angegeben wird.  
  
     Der `/action`-Parameter weist Setup an, eine Installation auszuführen.  
  
     Der `/role`-Parameter weist Setup an, das Analysis Services-Programm und die für PowerPivot für SharePoint erforderlichen Konfigurationsdateien zu installieren. Diese Rolle erkennt auch die vorhandenen Farmkonnektivitätsinformationen und verwendet sie, um auf die SharePoint-Konfigurationsdatenbank zuzugreifen. Dieser Parameter ist erforderlich. Verwenden Sie ihn statt des `/features`-Parameters, um die zu installierenden Komponenten anzugeben.  
  
     Der `/instancename`-Parameter gibt 'PowerPivot' als benannte Instanz an. Dieser Wert ist hartcodiert und kann nicht geändert werden. Er wird im Befehl zu pädagogischen Zwecken angegeben, damit Sie wissen, wie der Dienst installiert wird.  
  
     Mit dem `/indicateprogress`-Parameter können Sie den Status im Eingabeaufforderungsfenster überwachen.  
  
2.  Der `PID`-Parameter wird im Befehl weggelassen, was bewirkt, dass die Evaluation Edition installiert ist. Wenn Sie die Enterprise Edition installieren möchten, fügen Sie dem Setup-Befehl die PID hinzu und geben Sie einen gültigen Product Key ein.  
  
    ```  
  
    /PID=<product key for an Enterprise installation>  
  
    ```  
  
3.  Ersetzen Sie die Platzhalter für \<Domain\username > und \<StrongPassword > durch gültige Benutzerkonten und Kennwörter.  
  
     Die `/assvaccount` und **/assvcpassword** Parameter dienen zum Konfigurieren der [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] Instanz auf dem Anwendungsserver. Ersetzen Sie diese Platzhalter durch gültige Kontoinformationen.  
  
     Die **/assysadminaccounts** -Parameter muss festgelegt werden, um die Identität des Benutzers, der SQL Server-Setup ausgeführt wird. Sie müssen wenigstens einen Systemadministrator angeben. Beachten Sie, dass SQL Server-Setup keine automatischen sysadmin-Berechtigungen für Mitglieder der integrierten Gruppe "Administratoren" gewährt.  
  
4.  Entfernen Sie Zeilenumbrüche.  
  
5.  Wählen Sie den gesamten Befehl aus, und klicken Sie dann auf **Kopie** auf das Menü "Bearbeiten".  
  
6.  Öffnen Sie eine Administrator-Eingabeaufforderung. Zu diesem Zweck klicken Sie auf **starten**mit der rechten Maustaste auf die Eingabeaufforderung, und wählen Sie **als Administrator ausführen**.  
  
7.  Navigieren Sie zum Laufwerk oder dem freigegebenem Ordner, der die SQL Server-Installationsmedien enthält.  
  
8.  Fügen Sie den überarbeiteten Befehl in die Befehlszeile ein. Zu diesem Zweck klicken Sie auf das Symbol in der oberen linken Ecke des Eingabeaufforderungsfenster den Befehl aus, zeigen Sie auf **bearbeiten**, und klicken Sie dann auf **einfügen**.  
  
9. Drücken Sie **EINGABETASTE** zum Ausführen des Befehls. Warten Sie, bis Setup abgeschlossen ist. Sie können den Status von Setup im Eingabeaufforderungsfenster überwachen.  
  
10. Um die Installation zu überprüfen, öffnen Sie die Datei summary.txt unter \Programme\SQL Server\120\Setup Bootstrap\Log. Das Endergebnis sollte "Erfolgreich" lauten, wenn der Server ohne Fehler installiert hat.  
  
11. Konfigurieren Sie den Server. Sie müssen Lösungen bereitstellen, eine Dienstanwendung erstellen und die Funktion für jede Websitesammlung aktivieren. Weitere Informationen finden Sie unter [konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 &#40;PowerPivot-Konfigurationstool&#41; ](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) oder [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration ](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von PowerPivot-Dienstkonten](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
