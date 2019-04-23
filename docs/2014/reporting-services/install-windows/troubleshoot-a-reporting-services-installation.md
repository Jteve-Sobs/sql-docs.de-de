---
title: Problembehandlung bei einer Installation von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c923a239ad0eeb677b476665a4c99b45d430b421
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59954206"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Problembehandlung für eine Reporting Services-Installation
  Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aufgrund von Fehlern während der Ausführung von Setup nicht installieren können, können Sie mithilfe der Anweisungen in diesem Thema die häufigsten Ursachen von Installationsfehlern behandeln.  
  
 Die neuesten Informationen zu Problemen mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]finden Sie unter [Reporting Services SQL Server 2012 - Tipps, Tricks und Problembehandlung](https://go.microsoft.com/fwlink/?LinkId=221297)  
  
 Informationen zu anderen Fehlern und Problemen, die sich auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] beziehen, finden Sie unter [Beheben von SSRS-Problemen und Fehlern](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)  
  
 Lesen Sie die [Onlinehinweise zu dieser Version](https://go.microsoft.com/fwlink/?linkid=236893) , wenn das aufgetretene Problem in den Versionshinweisen beschrieben wird.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Überprüfen von Setupprotokollen](#bkmk_setuplogs)  
  
-   [Überprüfen der Voraussetzungen](#bkmk_prereq)  
  
-   [Behandeln von Problemen mit Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
-   [Behandeln von Problemen mit Installationen im einheitlichen Modus](#bkmk_tshoot_native)  
  
-   [Zusätzliche Ressourcen](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a> Überprüfen von Setupprotokollen  
 Setupfehler werden in Protokolldateien im Ordner **Programme\Microsoft SQL Server\110\Setup Bootstrap\Log** aufgezeichnet. Wenn Sie Setup ausführen, wird ein Unterordner erstellt. Der Name des Unterordners entspricht dem Datum und der Uhrzeit der Ausführung von Setup. Informationen zum Anzeigen der Setupprotokolldateien finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Die Protokolldateien enthalten eine Auflistung von Dateien.  
  
-   Öffnen Sie die Datei * _summary.txt, um Informationen über Produkt, Komponente und Instanz anzuzeigen.  
  
-   Öffnen Sie die Datei * _errorlog.txt, um Informationen zu Fehlern während der Ausführung von Setup anzuzeigen.  
  
-   Öffnen Sie *_RS\_\*_ComponentUpdateSetup.log, um Setupinformationen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] anzuzeigen.  
  
##  <a name="bkmk_prereq"></a> Überprüfen von Voraussetzungen  
 Die Voraussetzungen werden von Setup automatisch überprüft. Wenn Sie Setupprobleme behandeln möchten, ist es jedoch hilfreich, zu wissen, welche Voraussetzungen von Setup überprüft werden.  
  
-   Zu den Kontoanforderungen für die Ausführung von Setup gehört die Mitgliedschaft in der lokalen Gruppe Administratoren. Setup muss über die Berechtigung zum Hinzufügen von Dateien und Registrierungseinstellungen sowie zum Erstellen von lokalen Sicherheitsgruppen und zum Festlegen von Berechtigungen verfügen. Beim Installieren einer Standardkonfiguration muss das Setup die Berechtigung zum Erstellen einer Berichtsserver-Datenbank auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, auf der die Installation durchgeführt wird, aufweisen.  
  
-   HTTP.SYS 1.1 muss vom Betriebssystem unterstützt werden.  
  
-   Der HTTP-Dienst muss aktiviert sein und ausgeführt werden.  
  
-   Wenn Sie auch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst installieren, ist eine Ausführung von Distributed Transaction Coordinator (DTC) erforderlich.  
  
-   Der Ordner System32 muss die Datei Authz.dll enthalten.  
  
 Setup führt keine Überprüfung für Internet Information Services (IIS) oder [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]mehr durch. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert MDAC 2.0 und [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , Version 2.0; diese werden ggf. von Setup installiert.  
  
##  <a name="bkmk_tshoot_sharepoint"></a> Problembehandlung von Installationen im SharePoint-Modus  
  
-   [Reporting Services-Konfigurations-Manager startet nicht.](#bkmk_configmanager_notstart)  
  
-   [Sie werden in der SharePoint-Zentraladministration den SQL Server Reporting Services-Dienst nicht angezeigt, nach der Installation von SQL Server 2012 SSRS im SharePoint-Modus](#bkmk_no_ssrs_service)  
  
-   [PowerShell-Cmdlets für Reporting Services sind nicht verfügbar, und Befehle werden nicht erkannt.](#bkmk_cmdlets_not_recognized)  
  
-   [Sie sehen eine Fehlermeldung, die angibt, dass die URL nicht konfiguriert ist](#bkmk_URL_not_configured)  
  
-   [Setup erzeugt einen Fehler, wenn SharePoint auf einem Computer zwar installiert, aber nicht konfiguriert ist.](#bkmk_sharepoint_not_confiugred)  
  
-   [Die Seite der SharePoint-Zentraladministration ist leer.](#bkmk_central_admin_blank)  
  
-   [Eine Fehlermeldung wird angezeigt, wenn Sie versuchen, einen neuen Bericht mit dem Berichts-Generator zu erstellen.](#bkmk_reportbuilder_newreport_error)  
  
-   [Eine Fehlermeldung wird angezeigt, die besagt, dass RS_SHP nicht mit PREPAREIMAGE unterstützt wird.](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a> Reporting Services-Konfigurations-Manager startet nicht.  
 **Beschreibung:** Dieses Problem ist mit Absicht in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist jetzt für die SharePoint-Dienstarchitektur ausgelegt. Zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird der Konfigurations-Manager nicht mehr benötigt.  
  
 **Problemumgehung:** Verwenden Sie zum Konfigurieren eines Berichtsservers im SharePoint-Modus die SharePoint-Zentraladministration. Weitere Informationen finden Sie unter [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
###  <a name="bkmk_no_ssrs_service"></a> Sie werden in der SharePoint-Zentraladministration den SQL Server Reporting Services-Dienst nicht angezeigt, nach der Installation von SQL Server 2012 SSRS im SharePoint-Modus  
 **Beschreibung:** Wenn Sie nach einer erfolgreichen Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus und die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-in für SharePoint 2010, werden Sie nicht "SQL Server Reporting Services" in den folgenden zwei Menüs angezeigt und dann die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Dienst nicht registriert wurde:  
  
-   SharePoint 2010-Zentraladministration -> "Anwendungsverwaltung" -> "Dienste auf dem Server verwalten"-Seite  
  
-   SharePoint 2010-Zentraladministration -> "Anwendungsverwaltung" -> "Dienstanwendungen verwalten" -> Menü "Neu"  
  
 **Problemumgehung:** Registrieren und Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services, führen Sie die folgenden:  
  
1.  Auf dem Computer, auf dem SharePoint 2010-Zentraladministration ausgeführt wird  
  
    1.  Öffnen Sie die SharePoint 2010-Verwaltungsshell mit Administratorberechtigungen. Klicken Sie mit der rechten Maustaste auf das Symbol, und wählen Sie "Als Administrator ausführen". Führen Sie die folgenden drei Cmdlets von der Shell aus:  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Überprüfen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service zeigt den Status als "**gestartet**" auf der Seite: SharePoint 2010-Zentraladministration-> "**Anwendungsverwaltung**"->"**Dienste auf dem Server verwalten**"  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> PowerShell-Cmdlets für Reporting Services sind nicht verfügbar, und Befehle werden nicht erkannt.  
 **Beschreibung:** Wenn Sie versuchen, Sie führen eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell-Cmdlet wird eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
-   Der Begriff „Install-SPRSServiceInstall-SPRSService“ wurde **nicht** als Name eines Cmdlets, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt. Überprüfen Sie die Schreibweise des Namens, oder wenn ein Pfad enthalten ist, stellen Sie sicher, dass der Pfad richtig ist, und versuchen Sie es erneut. Bei Zeile: 1 Char: 39 + Install-SPRSServiceInstall-SPRSService <<<< + CategoryInfo: ObjectNotFound: (Installieren-SPRSServiceInstall-sofern) [], CommandNotFoundExcep  
  
 **Problemumgehung:** Führen Sie eine der folgenden:  
  
-   Führen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte aus. **rssharepoint.msi**.  
  
-   Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus von den SQL Server-Installationsmedien.  
  
 **Hinweis**: Wenn die **SharePoint 2013-Verwaltungsshell** beim, schließen und öffnen die-Verwaltungsshell einer dieser problemumgehungen ausführen geöffnet ist.  
  
 Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [Installieren von SharePoint-Modus von Reporting Services für SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a> Sie sehen eine Fehlermeldung, die angibt, dass die URL nicht konfiguriert ist  
 **Beschreibung:** Fehlermeldung Meldung ähnlich der folgenden:  
  
 Diese SQL Server Reporting Services (SSRS)-Funktionalität wird nicht unterstützt. Verwenden Sie Zentraladministration, um ein oder mehrere folgenden Probleme zu überprüfen und zu korrigieren: •Eine Berichtsserver-URL ist nicht konfiguriert. Verwenden Sie die SSRS-Integrationsseite, um sie festzulegen. •Der Proxy der SSRS-Dienstanwendung ist nicht konfiguriert. Verwenden Sie, die SSRS-Dienstanwendungsseiten, um den Proxy zu konfigurieren. •Die SSRS-Dienstanwendung ist nicht dieser Webanwendung zugeordnet. Verwenden Sie, die SSRS-Dienstanwendungsseiten, um den Proxy der SSRS-Dienstanwendung der Anwendungsproxygruppe dieser Webanwendung zuzuordnen.  
  
 **Problemumgehung:** Die Fehlermeldung enthält drei vorgeschlagene Schritte, um dieses Problem zu beheben. Der erste Vorschlag in der Meldung "Keine Berichtsserver-URL nicht konfiguriert ist"... spielt bei der Integration der früheren Version des Berichtsservers in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eine wichtige Rolle. Die SharePoint-Konfiguration für die vorherigen Berichtsserverversionen wird auf der Seite **Allgemeine Anwendungseinstellungen** abgeschlossen und verwendet **SQL Server Reporting Services (2008 und 2008 R2)**.  
  
 **Weitere Informationen** Wird Ihnen diese Fehlermeldung beim Versuch, Sie verwenden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Funktionen, die eine Verbindung mit erfordert die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service. Dies schließt Folgendes ein:  
  
-   Öffnen von SQL Server-Berichts-Generator von einer SharePoint-Dokumentbibliothek.  
  
-   Verwalten von Abonnements.  
  
-   Verwalten einer Dienstanwendung.  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> Setup erzeugt einen Fehler, wenn SharePoint auf einem Computer zwar installiert, aber nicht konfiguriert ist.  
 **Beschreibung:** Bei Auswahl von SharePoint-Modus von Reporting Services auf einem Computer installieren, die SharePoint installiert, aber es werden nicht konfiguriert, Sie sehen, dass eine Meldung ähnlich der folgenden, und Setup beendet wird:  
  
 SQL Server-Setup wird nicht mehr ausgeführt.  
  
 **Problemumgehung:** Konfigurieren von SharePoint, und führen Sie SQL Server-Installation.  
  
 **Weitere Informationen** Bei der Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in vorhandene SharePoint-Installation, versucht Setup zum Installieren und Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Dienst. Wenn SharePoint nicht konfiguriert ist, schlägt die Dienstinstallation fehl, sodass Setup fehlschlägt.  
  
###  <a name="bkmk_central_admin_blank"></a> Die Seite der SharePoint-Zentraladministration ist leer.  
 **Beschreibung:** Sie konnten SharePoint 2010 ohne Installationsfehler erfolgreich installieren. Wenn Sie jedoch zur Zentraladministration wechseln, sehen Sie nur eine leere Seite:  
  
 **Problemumgehung:** Dieses Problem ist nicht spezifisch für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] jedoch mit der Konfiguration von Berechtigungen in der gesamten SharePoint-Installation verknüpft ist. Im Folgenden finden Sie eine Liste mit Vorschlägen:  
  
-   Sehen Sie sich das SharePoint-Thema zu Entwicklungsumgebungen an. [Einrichten der Entwicklungsumgebung für SharePoint 2010 unter Windows Vista, Windows 7 und WindowsServer 2008](https://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   Lesen Sie den Forumsbeitrag: [Gibt leere Seite nach der Installation unter Windows 7-Zentraladministration zurück](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   Das Dienstkonto, das Sie für SharePoint-Dienste verwenden, z. B. der SharePoint 2010-Zentraladministrationsdienst, sollte im lokalen Betriebssystem Administratorprivilegien haben.  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> Eine Fehlermeldung wird angezeigt, wenn Sie versuchen, einen neuen Bericht mit dem Berichts-Generator zu erstellen.  
 **Beschreibung:** Sie sehen eine Fehlermeldung ähnlich der folgenden, wenn Sie versuchen, einen Berichts-Generator-Bericht in einer Dokumentbibliothek zu erstellen:  
  
 Diese Funktionalität wird nicht unterstützt, da eine SQL Server Reporting Services-Dienstanwendung nicht vorhanden ist, oder eine Berichtsserver-URL wurde nicht in der Zentraladministration konfiguriert.  
  
 **Problemumgehung:** Überprüfen, ob ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -dienstanwendung und ordnungsgemäß konfiguriert. Weitere Informationen finden Sie im Abschnitt "Erstellen einer Reporting Services-Dienstanwendung" [installieren Sie Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> Eine Fehlermeldung wird angezeigt, die besagt, dass RS_SHP nicht mit PREPAREIMAGE unterstützt wird.  
 **Beschreibung:** Wenn Sie versuchen, PREPAREIMAGE für ausführen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
 „Beim Ausführen der PREPAREIMAGE-Aktion wird die angegebene Funktion „RS_SHP“ nicht unterstützt, da sie SysPrep nicht unterstützt. Entfernen Sie die Funktionen, die nicht mit SysPrep kompatibel sind, und führen Sie das Setup erneut aus.“  
  
 **Problemumgehung:** Es gibt keine problemumgehung. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt SYSPREP (PREPAREIMAGE) nicht. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt SYSPREP.  
  
##  <a name="bkmk_tshoot_native"></a> Behandeln von Problemen mit Installationen im einheitlichen Modus  
  
###  <a name="PerfCounters"></a> Nach dem Upgrade auf Windows Vista oder Windows Server 2008 werden keine Leistungsindikatoren angezeigt.  
 Wenn Sie auf einem Computer mit [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ein Upgrade des Betriebssystems auf [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]vornehmen, werden die Leistungsindikatoren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nach dem Upgrade nicht festgelegt.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>So stellen Sie die Leistungsindikatoren von Reporting Services wieder her  
  
1.  Löschen Sie die folgenden Registrierungsschlüssel:  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie den folgenden Befehl ein:  
  
    -   **Führen Sie \<**  *.NET 2.0 Framework-Verzeichnis* **> \InstallUtil.exe \<**  *Berichtsserver-Bin-Verzeichnis* **> \ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  Ersetzen Sie dies \< *.NET 2.0 Framework-Verzeichnis*> durch den physischen Pfad der .NET Framework 2.0-Dateien und \< *Berichtsserver-Bin-Verzeichnis*> durch den physischen Pfad von der Berichtsserver-Binärdateien.  
  
3.  Starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst neu.  
  
 Überprüfen Sie, ob die Schritte erfolgreich ausgeführt wurden, indem Sie einen Webbrowser aufrufen und zur Berichts-Manager-URL oder zur Berichtsserver-URL navigieren. Öffnen Sie anschließend den Systemmonitor, um sicherzustellen, dass die Indikatoren funktionieren.  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>So fügen Sie die Leistungsregistrierungsschlüssel mit dem Registrierungs-Editor erneut hinzu  
  
1.  Öffnen Sie den Registrierungs-Editor:  
  
    1.  Klicken Sie auf **Start**und dann auf **Ausführen**.  
  
    2.  In der **ausführen** Dialogfeld die **öffnen** geben `regedit`.  
  
2.  Wählen Sie im Registrierungs-Editor den folgenden Registrierungsschlüssel aus: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  Klicken Sie mit der rechten Maustaste auf den Knoten **Performance** , zeigen Sie auf **Neu**, und klicken Sie auf **Wert der mehrteiligen Zeichenfolge**.  
  
4.  Typ `Counter Names` und drücken Sie dann die EINGABETASTE.  
  
5.  Wiederholen Sie den Vorgang, um in diesem Knoten den Registrierungsschlüssel `Counter Types` hinzuzufügen.  
  
6.  Navigieren Sie zu folgendem Registrierungsschlüssel: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  Klicken Sie mit der rechten Maustaste auf den Knoten **Performance** , zeigen Sie auf **Neu**, und klicken Sie auf **Wert der mehrteiligen Zeichenfolge**.  
  
8.  Typ `Counter Names` und drücken Sie dann die EINGABETASTE.  
  
9. Wiederholen Sie den Vorgang, um in diesem Knoten den Registrierungsschlüssel `Counter Types` hinzuzufügen.  
  
 Nachdem Sie die 64-Bit-Instanz repariert oder die Registrierungsschlüssel manuell erneut hinzugefügt haben, können Sie mit dem Systemmonitor die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Leistungsobjekte konfigurieren, die Sie überwachen möchten.  
  
###  <a name="ConfigPropsMissing"></a> Nach einem Upgrade von SQL Server 2005 sind die "ReportServerExternalURL"-Konfigurationseigenschaft und die "PassThroughCookies"-Konfigurationseigenschaft nicht konfiguriert.  
 Beim Aktualisieren von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] werden die Konfigurationseigenschaften  `ReportServerExternalURL` und `PassThroughCookies` nicht durch den Aktualisierungsvorgang konfiguriert. `ReportServerExternalURL` ist eine optionale Eigenschaft, und es sollte festgelegt werden, nur, wenn Sie SharePoint 2.0 Webparts verwenden und Benutzer in der Lage, einen Bericht abrufen und öffnen Sie es in einem neuen Browserfenster angezeigt werden sollen. Weitere Informationen zu `ReportServerExternalURL`, finden Sie unter [URLs in Konfigurationsdateien &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). `PassThroughCookies` ist nur beim Verwenden der benutzerdefinierten Authentifizierungsmethode erforderlich. Weitere Informationen zu `PassThroughCookies`, finden Sie unter [Konfigurieren des Berichts-Manager zum Übergeben von benutzerdefinierten Authentifizierungscookies](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  Wenn Sie benutzerdefinierte Authentifizierung verwenden, wird empfohlen, die Installation zu migrieren, statt ein Upgrade durchzuführen. Weitere Informationen zur Migration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Migrate a Reporting Services Installation (Native Mode) (Migrieren einer Installation von Reporting Services (einheitlicher Modus))](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 Standardmäßig sind diese Eigenschaften in der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Konfiguration nicht vorhanden. Wenn Sie diese Eigenschaften in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] konfiguriert haben und die von ihnen bereitgestellte Funktionalität weiterhin benötigen, müssen Sie sie nach dem Upgrade manuell der Datei **RSReportServer.config** hinzufügen. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
###  <a name="Default2005InstallBreaks2008"></a> Installationsfehler für eine Standardinstanz von SQL Server 2005 Reporting Services auf einem Computer mit SQL Server-2012Reporting-Dienste  
 Wenn Sie eine Standardinstanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem Computer zu installieren versuchen, auf dem bereits eine Instanz von [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]ausgeführt wird, schlägt die Installation der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz fehl, und folgende Fehlermeldung wird ausgegeben:  
  
 "Eine Instanz mit dem gleichen Namen ist bereits auf diesem Computer installiert. Geben Sie einen eindeutigen Instanznamen an, um das SQL Server-Setup fortzusetzen."  
  
 Dieses Problem tritt unabhängig davon auf, ob die [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Instanz eine Standardinstanz oder eine benannte Instanz ist, und unabhängig davon, ob eine [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Instanz mit diesem Namen bereits auf dem Computer vorhanden ist.  
  
 Zur Umgehung dieses Problems steht Ihnen eine der folgenden Optionen zur Verfügung:  
  
-   Wenn Sie [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als Standardinstanz auf dem Computer ausführen müssen, müssen Sie die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz vor der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Instanz installieren.  
  
-   Wenn die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz keine Standardinstanz sein muss, können Sie die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz als benannte Instanz installieren, nachdem Sie die [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Instanz installiert haben.  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a> Fehler 401 – nicht autorisiert, bei Verwendung der Windows-Authentifizierung nach einem Upgrade von SQL Server 2005 auf SQL Server 2012  
 Wenn Sie [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]aktualisieren und für das Berichtsserver-Dienstkonto NTLM-Authentifizierung mit einem integrierten Konto verwenden, tritt möglicherweise der Fehler 401 – „Nicht autorisiert“ auf, wenn Sie nach dem Upgrade auf den Berichtsserver oder Berichts-Manager zugreifen.  
  
 Der Grund hierfür ist eine Änderung in der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Standardkonfiguration für Windows-Authentifizierung. In der Konfiguration ist Aushandeln festgelegt, wenn es sich bei dem Berichtsserver-Dienstkonto um einen Netzwerkdienst oder ein lokales System handelt. In der Konfiguration ist NTLM festgelegt, wenn es sich bei dem Berichtsserver-Dienstkonto um keines dieser integrierten Konten handelt. Um das Problem nach dem Upgrade zu beheben, können Sie die Datei RSReportServer.config`AuthenticationType` bearbeiten und `RSWindowsNTLM` als  konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver](../security/configure-windows-authentication-on-the-report-server.md).  
  
###  <a name="Uninstall32BitBreaks64Bit"></a> Deinstallieren der 32-Bit-Instanz von SQL Server 2012 Reporting Services in Seite-an-Seite-Bereitstellung mit einer Instanz der 64-Bit-Instanz beschädigt. die 64-bit  
 Wenn Sie eine 32-Bit-Instanz und eine 64-Bit-Instanz von [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] parallel auf einem Computer installieren und die 32-Bit-Instanz deinstallieren, werden vier [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Registrierungsschlüssel entfernt. Hierdurch wird die 64-Bit-Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]beschädigt. Beim Deinstallieren der 32-Bit-Instanz werden die folgenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Registrierungsschlüssel entfernt:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 Um dieses Problem zu beheben, können Sie die 64-Bit-Instanz reparieren. Zwar wird empfohlen, die Reparatur auszuführen, Sie können jedoch mithilfe des Registrierungs-Editors die Registrierungsschlüssel manuell erneut hinzufügen.  
  
> [!CAUTION]  
>  Ein fehlerhaftes Bearbeiten der Registrierung kann eine schwerwiegende Beschädigung des Systems zur Folge haben. Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie wichtige Daten auf dem Computer sichern.  
  
##  <a name="bkmk_additional"></a> Zusätzliche Ressourcen  
 Folgendes sind zusätzliche Ressourcen, die Sie überprüfen können, um Ihnen beim Behandeln von Problemen zu helfen:  
  
-   TechNet-Wiki: Problembehandlungsthemen [Problembehandlung bei SQL Server Reporting Services (SSRS) im integrierten SharePoint-Modus](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Forum: SQLServer Reporting Services](http://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
 ![SharePoint-Einstellungen](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Senden von Feedback und Kontaktinformationen Informationen über Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
  
