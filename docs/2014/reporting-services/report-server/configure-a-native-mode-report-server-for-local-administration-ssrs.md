---
title: Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f9dc5d0ae36feb5801f026f0fca77683004e23b3
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52400543"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a>Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung (SSRS)
  Für die Bereitstellung eines [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsservers unter einem der folgenden Betriebssysteme sind weitere Konfigurationsschritte erforderlich, wenn die Berichtsserverinstanz lokal verwaltet werden soll. In diesem Thema wird beschrieben, wie der Berichtsserver für die lokale Verwaltung konfiguriert wird. Wenn Sie noch nicht installiert oder den Berichtsserver konfiguriert, finden Sie unter [Installieren von SQL Server 2014 vom Installations-Assistenten &#40;Setup&#41; ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) und [Verwalten einer Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 Da Berechtigungen durch die angegebenen Betriebssysteme beschränkt werden, führen Mitglieder der lokalen Gruppe Administratoren die meisten Anwendungen auf die gleiche Weise wie bei der Verwendung des Standardbenutzerkontos aus.  
  
 Dieses Verfahren verbessert zwar die allgemeine Sicherheit des Systems, verhindert jedoch, dass Sie die vordefinierten integrierten Rollenzuweisungen verwenden, die von Reporting Services für lokale Administratoren erstellt werden.  
  
-   [Übersicht der Konfigurationsänderungen](#bkmk_configuraiton_overview)  
  
-   [So konfigurieren Sie den Berichtsserver und den Berichts-Manager für die lokale Verwaltung](#bkmk_configure_local_server)  
  
-   [So konfigurieren Sie SQL Server Management Studio (SSMS) für die lokale Verwaltung des Berichtsservers](#bkmk_configure_ssms)  
  
-   [So konfigurieren Sie SQL Server Datatools BI (SSDT) zum Veröffentlichen in einem lokalen Berichtsserver](#bkmk_configure_ssdt)  
  
-   [Zusätzliche Informationen](#bkmk_addiitonal_informaiton)  
  
##  <a name="bkmk_configuraiton_overview"></a> Übersicht der Konfigurationsänderungen  
 Durch die folgenden Konfigurationsänderungen wird der Server so konfiguriert, dass Berichtsserverinhalte und -vorgänge mit Standardbenutzerberechtigungen verwaltet werden können:  
  
-   Fügen Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URLs zu vertrauenswürdigen Websites hinzu. Internet Explorer wird unter den aufgelisteten Betriebssystemen standardmäßig im **geschützten Modus**ausgeführt. Diese Funktion verhindert, dass Browseranforderungen Prozesse auf hoher Ebene erreichen, die auf demselben Computer ausgeführt werden. Sie können den geschützten Modus für die Berichtsserveranwendungen deaktivieren, indem Sie sie als vertrauenswürdige Sites hinzufügen.  
  
-   Erstellen Sie Rollenzuweisungen, die Ihnen als Berichtsserveradministrator die Berechtigung zur Verwaltung von Inhalt und Vorgängen verleihen, ohne die Funktion **Als Administrator ausführen** in Internet Explorer verwenden zu müssen. Durch das Erstellen von Rollenzuweisungen für Ihr Windows-Benutzerkonto erhalten Sie Zugriff auf einen Berichtsserver mit Inhalts-Manager- und Systemadministratorberechtigungen durch explizite Rollenzuweisungen, die die vordefinierten, integrierten Rollenzuweisungen ersetzen, die von Reporting Services erstellt werden.  
  
##  <a name="bkmk_configure_local_server"></a> So konfigurieren Sie den Berichtsserver und den Berichts-Manager für die lokale Verwaltung  
 Führen Sie die Konfigurationsschritte in diesem Abschnitt aus, wenn beim Navigieren zu einem lokalen Berichtsserver eine mit der folgenden vergleichbare Fehlermeldung angezeigt wird:  
  
-   Der Benutzer `'Domain\[user name]`' verfügt nicht über die erforderlichen Berechtigungen. Stellen Sie sicher, dass ausreichende Berechtigungen erteilt und die Einschränkungen der Windows-Benutzerkontensteuerung (UAC) behandelt wurden.  
  
###  <a name="bkmk_site_settings"></a> Browsereinstellungen für vertrauenswürdige Sites  
  
1.  Öffnen Sie ein Browserfenster mit "Als Administrator ausführen"-Berechtigungen. Klicken Sie im Menü **Start** auf **Alle Programme**, klicken Sie mit der rechten Maustaste auf **Internet Explorer**, und wählen Sie **Als Administrator ausführen**aus.  
  
2.  Klicken Sie auf **Zulassen** , um den Vorgang fortzusetzen.  
  
3.  Geben Sie in der URL-Adresse die Berichts-Manager-URL ein. Anweisungen finden Sie unter [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
4.  Klicken Sie auf **Extras**.  
  
5.  Klicken Sie auf **Internetoptionen**.  
  
6.  Klicken Sie auf **Sicherheit**.  
  
7.  Klicken Sie auf **Vertrauenswürdige Sites**.  
  
8.  Klicken Sie auf **Websites**.  
  
9. Fügen Sie `http://<your-server-name>`hinzu.  
  
10. Deaktivieren Sie das Kontrollkästchen **Für Sites dieser Zone ist eine Serverüberprüfung (https:) erforderlich** , falls Sie HTTPS nicht für die Standardwebsite verwenden.  
  
11. Klicken Sie auf **Hinzufügen**.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="bkmk_configure_folder_settings"></a> Ordnereinstellungen im Berichts-Manager  
  
1.  Klicken Sie im Berichts-Manager auf der Startseite auf **Ordnereinstellungen**.  
  
2.  Klicken Sie auf der Seite Ordnereinstellungen auf **Sicherheit**.  
  
3.  Klicken Sie auf **Neue Rollenzuweisung**.  
  
4.  Geben Sie im Feld **Gruppen- oder Benutzername** Ihr Windows-Benutzerkonto im folgenden Format ein: `<domain>\<user>`.  
  
5.  Wählen Sie **Inhalts-Manager**aus.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="bkmk_configure_site_settings"></a> Siteeinstellungen im Berichts-Manager  
  
1.  Öffnen Sie den Browser mit Administratorprivilegien, und navigieren Sie zum Berichts-Manager unter `http://<server name>/reports`.  
  
2.  Klicken Sie in der oberen Ecke der Startseite auf **Siteeinstellungen** .  
  
    > [!TIP]  
    >  **Hinweis**: Wenn Sie nicht sehen die **Standorteinstellungen** option, schließen und öffnen Sie Ihren Browser und navigieren Sie zum Berichtmanager mit Administratorrechten ausführen.  
  
3.  Klicken Sie auf **Sicherheit**.  
  
4.  Klicken Sie auf **Neue Rollenzuweisung**.  
  
5.  Geben Sie im Feld **Gruppen- oder Benutzername** Ihr Windows-Benutzerkonto im folgenden Format ein: `<domain>\<user>`.  
  
6.  Wählen Sie **Systemadministrator**aus.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  Schließen Sie den Berichts-Manager.  
  
9. Öffnen Sie den Berichts-Manager in Internet Explorer erneut, ohne **Als Administrator ausführen**zu verwenden.  
  
##  <a name="bkmk_configure_ssms"></a> So konfigurieren Sie SQL Server Management Studio (SSMS) für die lokale Verwaltung des Berichtsservers  
 Standardmäßig ist es nur möglich, auf alle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbaren Berichtsservereigenschaften zuzugreifen, wenn Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorprivilegien starten.  
  
 **So konfigurieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** , sodass [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nicht jedes Mal mit erweiterten Berechtigungen gestartet werden muss:  
  
-   Klicken Sie im Menü **Start** auf **Alle Programme**und anschließend auf **SQL Server 2014**. Klicken Sie mit der rechten Maustaste auf **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, und klicken Sie anschließend auf **Als Administrator ausführen**.  
  
-   Stellen Sie eine Verbindung mit dem lokalen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Server her.  
  
-   Klicken Sie im Knoten **Sicherheit** auf **Systemrollen**.  
  
-   Klicken Sie mit der rechten Maustaste auf **Systemadministrator** , und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Wählen Sie auf der Seite **Systemrolleneigenschaften** die Option **Berichtsservereigenschaften anzeigen**aus. Wählen Sie weitere Eigenschaften aus, die Sie Mitgliedern der Systemadministratorrolle zuordnen möchten.  
  
-   Klicken Sie auf **OK**.  
  
-   Schließen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Informationen zum Hinzufügen eines Benutzers zur Systemrolle "Systemadministrator" finden Sie im Abschnitt [Siteeinstellungen im Berichts-Manager](#bkmk_configure_site_settings) weiter oben in diesem Thema.  
  
 Wenn Sie jetzt [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] öffnen und nicht explizit **Als Administrator ausführen** auswählen, haben Sie Zugriff auf die Berichtsservereigenschaften.  
  
##  <a name="bkmk_configure_ssdt"></a> So konfigurieren Sie SQL Server Datatools BI (SSDT) zum Veröffentlichen in einem lokalen Berichtsserver  
 Wenn Sie [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] unter einem der im ersten Abschnitt dieses Themas aufgeführten Betriebssysteme installiert haben und SSDT mit einem lokalen Berichtsserver im einheitlichen Modus interagieren soll, treten Berechtigungsfehler auf, sofern Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht mit erweiterten Berechtigungen öffnen oder Reporting Services-Rollen konfigurieren. Wenn Sie nicht über ausreichende Berechtigungen verfügen, können z. B. folgende Probleme auftreten:  
  
-   Beim Versuch, Berichtselemente auf dem lokalen Berichtsserver bereitzustellen, wird im Fenster **Fehlerliste** eine Fehlermeldung wie die folgende angezeigt:  
  
    -   Die dem Benutzer „Domain\\<Benutzername\>“ erteilten Berechtigungen reichen zum Ausführen des Vorgangs nicht aus.  
  
 **So verwenden Sie bei jedem Öffnen von SSDT erweiterte Berechtigungen**  
  
1.  Geben Sie im Startbildschirm `sql server` , und klicken Sie dann mit der rechten Maustaste **SQL Server Data Tools für Visual Studio**. Klicken Sie auf **Als Administrator ausführen**.  
  
     **Oder**verfahren Sie bei älteren Betriebssystemen wie folgt:  
  
     Klicken Sie im Menü **Start** auf **Alle Programme**und dann auf **SQL Server 2014**. Klicken Sie mit der rechten Maustaste auf **SQL Server Data Tools**und dann auf **Als Administrator ausführen**.  
  
2.  Klicken Sie auf **Weiter**.  
  
3.  Klicken Sie auf **Programm ausführen**.  
  
 Sie können jetzt Berichte und andere Elemente auf einem lokalen Berichtsserver bereitstellen.  
  
 **So konfigurieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Rollenzuweisungen, damit SSDT nicht jedes Mal mit erweiterten Berechtigungen gestartet werden muss**  
  
-   Siehe die Abschnitte [Ordnereinstellungen im Berichts-Manager](#bkmk_configure_folder_settings) und [Siteeinstellungen im Berichts-Manager](#bkmk_configure_site_settings) weiter oben in diesem Thema.  
  
##  <a name="bkmk_addiitonal_informaiton"></a> Zusätzliche Informationen  
 Ein weiterer häufiger Konfigurationsschritt in Verbindung mit der Verwaltung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] besteht darin, Port 80 in der Windows-Firewall zu öffnen, um den Zugriff auf den Berichtsservercomputer zu ermöglichen. Anweisungen finden Sie unter [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus](manage-a-reporting-services-native-mode-report-server.md)  
  
  
