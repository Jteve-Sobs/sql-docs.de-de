---
title: Aktivieren von verschlüsselten Verbindungen zum Datenbankmodul (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ffe88de8533db5cf9bbec7936d30e95d64b1726
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640771"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a>Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie verschlüsselte Verbindungen für eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] durch Angeben eines Zertifikats für die [!INCLUDE[ssDE](../../includes/ssde-md.md)] mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers aktivieren können. Für den Servercomputer muss ein Zertifikat bereitgestellt worden sein, und der Clientcomputer muss so eingerichtet sein, dass er die Stammzertifizierungsstelle des Zertifikats als vertrauenswürdig einstuft. Zertifikate werden bereitgestellt, indem sie mithilfe eines Importvorgangs in Windows installiert werden.  
  
 Das Zertifikat muss für die **Serverauthentifizierung**ausgegeben sein. Der Name des Zertifikats muss der vollqualifizierte Domänenname (FQDN) des Computers sein.  
  
 Zertifikate werden lokal für diesen Benutzer auf dem Computer gespeichert. Um ein Zertifikat zur Verwendung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren, müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager unter dem gleichen Benutzerkonto ausführen wie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst. Nur wenn der Dienst als LocalSystem, NetworkService oder LocalService ausgeführt wird, kann ein administratives Konto verwendet werden.  
  
 Der Client muss in der Lage sein, den Besitzer des vom Server verwendeten Zertifikats zu überprüfen. Wenn der Client über das Zertifikat für öffentliche Schlüssel der Zertifizierungsstelle verfügt, die das Serverzertifikat signiert hat, sind keine weiteren Konfigurationsschritte erforderlich. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows enthält die Zertifikate für öffentliche Schlüssel von vielen Zertifizierungsstellen. Wenn das Serverzertifikat von einer öffentlichen oder privaten Zertifizierungsstelle signiert wurde, für die der Client kein öffentliches Schlüsselzertifikat besitzt, müssen Sie das Zertifikat für öffentliche Schlüssel der Zertifizierungsstelle installieren, die das Serverzertifikat signiert hat.  
  
> [!NOTE]  
>  Wenn Sie die Verschlüsselung bei einem Failovercluster verwenden möchten, müssen Sie das Serverzertifikat mit dem vollqualifizierten DNS-Namen des virtuellen Servers auf allen Knoten im Failovercluster installieren. Wenn Sie z.B. über einen Cluster mit zwei Knoten verfügen, wobei die Knotennamen test1.*\<Ihr_Unternehmen>*.com und test2.*\<Ihr_Unternehmen>*.com lauten, und ein virtueller Server den Namen „virtsql“ trägt, müssen Sie ein Zertifikat für virtsql.*\<Ihr_Unternehmen>*.com auf beiden Knoten installieren. Sie können den Wert der Option **ForceEncryption**auf **Yes**.  
  
 **In diesem Thema**  
  
-   **So aktivieren Sie verschlüsselte Verbindungen**  
  
     [Bereitstellen (installieren) eines Zertifikats auf dem server](#Provision)  
  
     [Exportieren des Serverzertifikats](#Export)  
  
     [Konfigurieren Sie den Server zum Annehmen verschlüsselter Verbindungen](#ConfigureServerConnections)  
  
     [Konfigurieren Sie den Client zum Anfordern verschlüsselter Verbindungen](#ConfigureClientConnections)  
  
     [Verschlüsseln einer Verbindung in SQL Server Management Studio](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="Provision"></a> So stellen Sie ein Zertifikat auf dem Server bereit bzw. installieren Sie ein Zertifikat  
  
1.  Auf der **starten** Menü klicken Sie auf **ausführen**, und klicken Sie in der **öffnen** geben `MMC` , und klicken Sie auf **OK**.  
  
2.  Klicken Sie in der MMC-Konsole im Menü **Datei** auf **Snap-In hinzufügen/entfernen**.  
  
3.  Klicken Sie im Dialogfeld **Snap-In hinzufügen/entfernen** auf **Hinzufügen**.  
  
4.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Zertifikate**, und klicken Sie dann auf **Hinzufügen**.  
  
5.  Klicken Sie im **Dialogfeld Zertifikate-Snap-In** auf **Computerkonto**, und klicken Sie dann auf **Fertig stellen**.  
  
6.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Schließen**.  
  
7.  Klicken Sie im Dialogfeld **Snap-In hinzufügen/entfernen** auf **OK**.  
  
8.  Erweitern Sie im Dialogfeld **Zertifikate** -Snap-In die Option **Zertifikate**, erweitern Sie **Eigene Zertifikate**, und klicken Sie dann mit der rechten Maustaste auf **Zertifikate**, zeigen Sie auf **Alle Aufgaben**, und klicken Sie anschließend auf **Importieren**.  
  
9. Ergänzen Sie die Angaben im **Zertifikatimport-Assistenten**, um dem Computer ein Zertifikat hinzuzufügen, und schließen Sie dann die MMC-Konsole. Weitere Informationen zum Hinzufügen von Zertifikaten zu einem Computer finden Sie in der Windows-Dokumentation.  
  
###  <a name="Export"></a> So exportieren Sie das Serverzertifikat  
  
1.  Erweitern Sie im **Zertifikate** -Snap-In den Ordner **Zertifikate** / **Eigene Zertifikate** , klicken Sie mit der rechten Maustaste auf das **Zertifikat**, zeigen Sie auf **Alle Tasks**, und klicken Sie dann auf **Exportieren**.  
  
2.  Führen Sie den **Zertifikatexport-Assistenten**aus, und speichern Sie die Zertifikatsdatei in einem geeigneten Speicherort.  
  
###  <a name="ConfigureServerConnections"></a> So konfigurieren Sie den Server zum Annehmen verschlüsselter Verbindungen  
  
1.  Erweitern Sie im **SQL Server Configuration Manager** den Eintrag **SQL Server-Netzwerkkonfiguration**, klicken Sie mit der rechten Maustaste auf **Protokolle für** *\<Serverinstanz>*, und wählen Sie dann **Eigenschaften**.  
  
2.  In der **Protokolle für ***\<Instanzname >* **Eigenschaften** Dialogfeld auf die **Zertifikat** Registerkarte, wählen Sie das gewünschte Zertifikat aus der Dropdownliste aus für die **Zertifikat** ein, und klicken Sie dann auf **OK**.  
  
3.  Aktivieren Sie auf der Registerkarte **Flags** im Feld **ForceEncryption** die Option **Ja**, und klicken Sie dann auf **OK** , um das Dialogfeld zu schließen.  
  
4.  Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst neu.  
  
###  <a name="ConfigureClientConnections"></a> So konfigurieren Sie den Client zum Anfordern verschlüsselter Verbindungen  
  
1.  Kopieren Sie entweder das Originalzertifikat oder die exportierte Zertifikatsdatei auf den Clientcomputer.  
  
2.  Installieren Sie auf dem Clientcomputer mithilfe des **Zertifikate** -Snap-Ins entweder das Stammzertifikat oder die exportierte Zertifikatsdatei.  
  
3.  Klicken Sie im Konsolenbereich mit der rechten Maustaste auf **SQL Server Native Client-Konfiguration**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Klicken Sie auf der Seite **Flags** im Feld **Protokollverschlüsselung erzwingen** auf **Ja**.  
  
###  <a name="EncryptConnection"></a> So verschlüsseln Sie eine Verbindung in SQL Server Management Studio  
  
1.  Klicken Sie auf der Symbolleiste des Objekt-Explorers auf **Verbinden**, und klicken Sie dann auf **Datenbank-Engine**.  
  
2.  Vervollständigen Sie im Dialogfeld **Verbindung mit Server herstellen** die Verbindungseinstellungen, und klicken Sie dann auf **Optionen**.  
  
3.  Klicken Sie auf der Registerkarte **Verbindungseigenschaften** auf **Verbindung verschlüsseln**.  
  
  
