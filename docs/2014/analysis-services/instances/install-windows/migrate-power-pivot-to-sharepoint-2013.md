---
title: Migrieren von PowerPivot zu SharePoint 2013 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64f3d3474ac812f07645cd3064c270ba10ad76c3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368372"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a>Migrieren von PowerPivot zu SharePoint 2013
  
  
 SharePoint 2013 unterstützt keine direkten Upgrades. Die **Upgrademethode mit Anfügen der Datenbanken**wird jedoch unterstützt. Das Verhalten unterscheidet sich vom Upgrade auf SharePoint 2010, bei dem ein Kunde zwischen zwei grundlegenden Upgradeansätzen wählen kann: dem direkten Upgrade und dem Upgrade mit Anfügen der Datenbanken.  
  
 Wenn Sie über eine in SharePoint 2010 integrierte [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] -Installation verfügen, kann der SharePoint-Server nicht direkt aktualisiert werden. Sie haben jedoch die Möglichkeit, Inhaltsdatenbanken und Dienstanwendungsdatenbanken von der SharePoint 2010-Farm zu einer SharePoint 2013-Farm zu migrieren. Dieses Thema bietet eine Übersicht über die Schritte, die zum Ausführen eines Upgrades mit Anfügen der Datenbanken sowie für eine PowerPivot-bezogene Migration erforderlich sind.  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013  
  
### <a name="migration-overview"></a>Übersicht über die Migration  
  
|1|2|3|4|  
|-------|-------|-------|-------|  
|Vorbereiten der SharePoint 2013-Farm|Sichern, Kopieren und Wiederherstellen von Datenbanken|Einbinden von Inhaltsdatenbanken|Migrieren von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Zeitplänen|  
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|SharePoint-Zentraladministration<br /><br /> Windows PowerShell|SharePoint-Anwendungsseiten<br /><br /> Windows PowerShell|  
  
 **In diesem Thema:**  
  
-   [1) Vorbereiten der SharePoint 2013-Farm](#bkmk_prepare_sharepoint2013)  
  
-   [2) Sichern, Kopieren und Wiederherstellen der Datenbanken](#bkmk_backup_restore)  
  
-   [3) Vorbereiten von Webanwendungen und Einbinden von Inhaltsdatenbanken](#bkmk_prepare_mount_databases)  
  
-   [(4) aktualisieren von PowerPivot-Zeitplänen](#bkmk_upgrade_powerpivot_schedules)  
  
-   [Zusätzliche Ressourcen](#bkmk_additional_resources)  
  
##  <a name="bkmk_prepare_sharepoint2013"></a> 1) Vorbereiten der SharePoint 2013-Farm  
  
1.  > [!TIP]  
    >  Überprüfen Sie die Authentifizierungsmethode, die in vorhandenen Webanwendungen konfiguriert wurde. SharePoint 2013-Webanwendungen verwenden standardmäßig die anspruchsbasierte Authentifizierung. Für den klassischen Authentifizierungsmodus konfigurierte SharePoint 2010-Webanwendungen erfordern zusätzliche Schritte, um Datenbanken von SharePoint 2010 zu SharePoint 2013 zu migrieren. Wenn die Webanwendungen für den klassischen Authentifizierungsmodus konfiguriert sind, lesen Sie die SharePoint 2013-Dokumentation.  
  
2.  Installieren Sie eine neue SharePoint Server 2013-Farm.  
  
3.  Installieren Sie eine Instanz eines [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Modus. Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2013 Installation](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
4.  Führen Sie das [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013-Installationspaket **spPowerPivot.msi** auf jedem Server in der SharePoint-Farm aus. Weitere Informationen finden Sie unter [installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
5.  Konfigurieren Sie in der SharePoint 2013-Zentraladministration die Excel Services-Dienstanwendung in der Weise, dass sie den im vorangehenden Schritt erstellten [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus verwendet. Weitere Informationen finden Sie im Abschnitt "Konfigurieren einer grundlegenden Analysis Services SharePoint Integration" [PowerPivot für SharePoint 2013 Installation](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
##  <a name="bkmk_backup_restore"></a> 2) Sichern, Kopieren und Wiederherstellen der Datenbanken  
 Der Prozess "SharePoint-Datenbank-Upgrade mit anfügen" ist eine Abfolge von Schritten zu sichern, kopieren und Wiederherstellung PowerPivot verwandte Inhalte und dienstanwendungsdatenbanken auf der SharePoint 2013-Farm.  
  
1.  **Datenbank wird auf schreibgeschützt festgelegt:** In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf den Datenbanknamen, und klicken Sie auf **Eigenschaften**. Legen Sie auf der Seite **Optionen** die Eigenschaft **Datenbank schreibgeschützt** auf **True**fest.  
  
2.  **Sichern Sie:** Sichern Sie jede Inhaltsdatenbank und jede dienstanwendungsdatenbank, die Sie zur SharePoint 2013-Farm migrieren möchten. Klicken Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf den Datenbanknamen, und klicken Sie auf **Tasks**und dann auf **Sichern**.  
  
3.  Kopieren Sie die Datenbank-Sicherungsdateien (.bak) auf den gewünschten Zielserver.  
  
4.  **Wiederherstellung:** Stellen Sie die Datenbanken auf dem Ziel- [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]. Dieser Schritt kann mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]ausgeführt werden.  
  
5.  **Legen Sie die Datenbank mit Lese-/ Schreibzugriff:** Legen Sie die **Datenbank schreibgeschützt** zu **"false"**.  
  
##  <a name="bkmk_prepare_mount_databases"></a> 3) Vorbereiten von Webanwendungen und Einbinden von Inhaltsdatenbanken  
 Eine ausführlichere Erläuterung der folgenden Verfahren werden soll, finden Sie unter [Aktualisieren von Datenbanken von SharePoint 2010 auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
1.  **Datenbank offline schalten:**  
  
     Schalten Sie jede SharePoint 2013-Inhaltsdatenbank mithilfe der SharePoint-Zentraladministration offline. Die Inhaltsdatenbanken werden durch die Datenbanken ersetzt, die Sie kopiert haben. Überlegen Sie, welches die beste Abfolge für Ihre Umgebung ist. Sie können die Datenbanken einzeln offline schalten und die zugehörige Ersatzdatenbank einbinden, bevor Sie die nächste Inhaltsdatenbank offline schalten. Oder Sie haben die Möglichkeit, alle Inhaltsdatenbanken als Gruppe offline zu schalten.  
  
    1.  Klicken Sie in der SharePoint-Zentraladministration auf **Anwendungsverwaltung**.  
  
    2.  Klicken Sie auf **Inhaltsdatenbanken verwalten**.  
  
    3.  Klicken Sie auf den Namen der Datenbank.  
  
    4.  Legen Sie unter **Inhaltsdatenbankeigenschaften verwalten**die Option **Datenbankstatus** auf **Offline**fest.  
  
    5.  Wählen Sie **Inhaltsdatenbank entfernen**aus. Beachten Sie die Warnung, dass auf Websites, die in der Inhaltsdatenbank gespeichert sind, nicht mehr zugegriffen werden kann.  
  
-   **Inhaltsdatenbanken einbinden:**  
  
     Verwenden Sie PowerShell-Cmdlets in der SharePoint 2013-Verwaltungsshell, um die migrierte Inhaltsdatenbank einzubinden. Die Dienstanwendungsdatenbank muss nicht eingebunden werden, sondern nur die Inhaltsdatenbanken: ![PowerShell-Inhalt](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")  
  
    ```  
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]  
    ```  
  
     Weitere Informationen finden Sie unter [anfügen oder Trennen von Inhaltsdatenbanken (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx).  
  
     **Status, wenn der Schritt abgeschlossen ist:**  Wenn der Bereitstellungsvorgang abgeschlossen ist, sehen Benutzer die Dateien, die in der alten Inhaltsdatenbank enthalten waren. Folglich können Benutzer die Arbeitsmappen in der Dokumentbibliothek anzeigen und öffnen.  
  
    > [!TIP]  
    >  An dieser Stelle im Migrationsvorgang besteht die Möglichkeit, neue Zeitpläne für die migrierten Arbeitsmappen zu erstellen. Die Zeitpläne werden jedoch in der neuen Datenbank der [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Dienstanwendung erstellt und nicht in der Datenbank, die Sie aus der alten SharePoint-Farm kopiert haben. Daher enthält die Datenbank keinen der alten Zeitpläne. Nachdem Sie die folgenden Schritte ausgeführt haben, um die alte Datenbank zu verwenden und die alten Zeitpläne zu migrieren, sind die neuen Zeitpläne nicht verfügbar.  
  
### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a>Beheben von Problemen beim Einbinden von Datenbanken  
 In diesem Abschnitt sind mögliche Probleme zusammengefasst, die beim Einbinden der Datenbank auftreten können.  
  
1.  **Authentifizierungsfehler:** Wenn Authentifizierungsfehler auftreten, überprüfen Sie den Authentifizierungsmodus, der von den Quellwebanwendungen verwendet wird. Der Fehler könnte durch einen Authentifizierungskonflikt zwischen der SharePoint 2013-Webanwendung und der SharePoint 2010-Webanwendung verursacht werden. Weitere Informationen finden Sie unter [1) Vorbereiten der SharePoint 2013-Farm](#bkmk_prepare_sharepoint2013) .  
  
2.  **Fehlende PowerPivot-Dateien:** Wenn Fehler bezüglich fehlender PowerPivot-DLLs angezeigt werden die **spPowerPivot.msi** wurde nicht installiert oder [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Konfigurationstool zur Konfiguration von PowerPivot nicht verwendet wurde.  
  
##  <a name="bkmk_upgrade_powerpivot_schedules"></a> (4) aktualisieren von PowerPivot-Zeitplänen  
 In diesem Abschnitt werden die Details und Optionen zum Migrieren von PowerPivot-Zeitplänen beschrieben. Die Migration von Zeitplänen erfolgt in zwei Schritten. Zunächst konfigurieren Sie die PowerPivot-Dienstanwendung für die Verwendung der migrierten Dienstanwendungsdatenbank. Als Nächstes wählen Sie eine der beiden Optionen zur Migration von Zeitplänen aus.  
  
 **Konfigurieren Sie die Dienstanwendung für die Verwendung der migrierten Dienstanwendungsdatenbank.**  
  
 Konfigurieren Sie die PowerPivot-Dienstanwendung in der SharePoint-Zentraladministration für die Verwendung der alten Dienstanwendungsdatenbank, die Sie kopiert haben. Der PowerPivot-Dienst aktualisiert die Dienstanwendungsdatenbank auf das neue Schema.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration auf **Dienstanwendungen verwalten**.  
  
2.  Suchen Sie die PowerPivot-Anwendung, z. B. "PowerPivot-Standarddienstanwendung", klicken Sie auf den Namen der dienstanwendung, und klicken Sie auf **Eigenschaften** im SharePoint-Menüband.  
  
3.  Aktualisieren Sie die Datenbankservernamensinstanz und den Datenbanknamen. Verwenden Sie die Namen der Datenbank, die Sie gesichert, kopiert und wiederhergestellt haben. Nachdem Sie auf **OK**geklickt haben, wird die Dienstanwendungsdatenbank aktualisiert. Etwaige Fehler können Sie dem ULS-Protokoll entnehmen.  
  
 **Aktualisieren von PowerPivot-Zeitplänen**  
  
 Konfigurieren Sie die PowerPivot-Dienstanwendung für die Migration von Aktualisierungszeitplänen.  
  
-   **Migrieren von Zeitplänen option1: SharePoint-Farmadministrator**  
  
    1.  In der SharePoint 2013-Management-Ausführung der `Set-PowerPivotServiceApplication` Cmdlet mit der `-StartMigratingRefreshSchedules` Switch So aktivieren Sie automatische bedarfsorientierte Migration von Zeitplänen ![PowerShell related Content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related Content"). Im folgenden Windows PowerShell-Skript wird davon ausgegangen, dass nur eine PowerPivot-Dienstanwendung vorhanden ist.  
  
        ```  
        $app=Get-PowerPivotServiceApplication  
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules  
        ```  
  
         Nachdem das Windows PowerShell-Skript ausgeführt wurde, sind die Zeitpläne aktiv und werden zum nächstmöglichen Zeitpunkt ausgeführt. Der Status auf der Seite für die Zeitplanaktualisierung lautet jedoch nicht Aktiviert. Wenn der Zeitplan das erste Mal ausgeführt wird, wird er migriert, und auf der Seite zur Zeitplanaktualisierung ist **Aktiviert**  auf "True" festgelegt.  
  
    2.  Wenn Sie den aktuellen Wert der StartMigratingRefreshSchedules-Eigenschaft überprüfen möchten, führen Sie das folgende PowerShell-Skript aus. Das Skript durchläuft alle PowerPivot-Dienstanwendungsobjekte und zeigt den Namen und die Eigenschaftswerte an:  
  
        ```  
        $apps = Get-PowerPivotServiceApplication  
        foreach ($app in $apps){}  
        Get-PowerPivotServiceApplication $appp | format-table -property displayname,id,StartMigratingRefreshSchedules  
        ```  
  
     **Migrieren von Zeitplänen option2: Benutzer Aktualisierung jeder Arbeitsmappe**  
  
    1.  Eine andere Möglichkeit zum Migrieren von Zeitplänen besteht darin, die Zeitplanaktualisierung für jede Arbeitsmappe zu aktivieren. Navigieren Sie zu der Dokumentbibliothek, in der die Arbeitsmappen enthalten sind.  
  
    2.  Öffnen Sie das Kontextmenü, und klicken auf **PowerPivot-Datenaktualisierung verwalten**.  
  
    3.  Klicken Sie im Abschnitt zur **Zeitplanaktualisierung** auf **Aktivieren**.  
  
    4.  Sie können **Außerdem sobald wie möglich aktualisieren**auswählen. Durch diese Option wird der Warteschlange eine Instanz der Aktualisierung hinzugefügt, sobald Sie auf OK klicken. Der reguläre Aktualisierungszeitplan wird weiterhin zum entsprechenden Zeitpunkt ausgelöst.  
  
    5.  Klicken Sie auf **OK**. Der Aktualisierungsverlauf wird jetzt auf der Aktualisierungsseite angezeigt, und der Zeitplan wird zum normalen Zeitpunkt ausgelöst.  
  
 **SQL Server 2008 R2 PowerPivot-Arbeitsmappen**  
  
-   SQL Server 2008 R2 PowerPivot-Arbeitsmappen werden nicht automatisch aktualisiert, wenn sie in SQL Server 2012 SP1 PowerPivot für SharePoint 2013 verwendet werden. Nach der Migration einer Inhaltsdatenbank, die 2008 R2-Arbeitsmappen enthält, können Sie die Arbeitsmappen zwar verwenden, die Zeitpläne werden jedoch nicht aktualisiert.  
  
-   Weitere Informationen finden Sie unter [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_additional_resources"></a> Zusätzliche Ressourcen  
  
> [!NOTE]  
>  Weitere Informationen zum [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] - und SharePoint-Upgrade mit Anfügen der Datenbanken finden Sie unter:  
  
-   [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
-   [Übersicht über den Upgradeprozess für SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Vorbereitende Bereinigung vor einem Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Aktualisieren von Datenbanken von SharePoint 2010 auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
  
