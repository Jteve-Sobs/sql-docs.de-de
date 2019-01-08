---
title: Verbindung mit einer Master Data Services-Datenbank herstellen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c5214722aea9ea3fb1d04519d414b4c86ebb33de
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52810112"
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Verbindung mit einer Master Data Services-Datenbank herstellen (Dialogfeld)
  Verwenden Sie das Dialogfeld **Verbindung mit einer Master Data Services-Datenbank herstellen** , um eine [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auszuwählen.  
  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ist dieses Dialogfeld auf den folgenden Seiten verfügbar:  
  
-   Klicken Sie auf der Seite **Datenbankkonfiguration** auf **Datenbank auswählen.** Wählen Sie über dieses Dialogfeld eine Datenbank aus, für die Sie Systemeinstellungen konfigurieren möchten.  
  
-   Klicken Sie auf der Seite **Webkonfiguration** unter **///Anwendung einer Datenbank zuordnen**auf **Auswählen** , um die Datenbank auszuwählen, die der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Website oder -Anwendung zugewiesen werden soll.  
  
## <a name="select-database"></a>Datenbank auswählen  
 Geben Sie Informationen für die Verbindung mit einer lokalen oder Remoteinstanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] an, auf der die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank gehostet werden soll. Um eine Verbindung mit einer Remoteinstanz herzustellen, müssen Sie diese für Remoteverbindungen einrichten.  
  
|Steuerelementname|Description|  
|------------------|-----------------|  
|**SQL Server-Instanz**|Geben Sie den Namen der [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] -Instanz an, auf der die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank gehostet werden soll. Dies kann eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder Remotecomputer sein. Geben Sie die Informationen wie folgt an:<br /><br /> Einen Punkt (.) für die Verbindung mit der Standardinstanz auf dem lokalen Computer.<br /><br /> Den Servernamen oder die IP-Adresse für die Verbindung mit der Standardinstanz auf dem angegebenen lokalen oder Remotecomputer.<br /><br /> Der Servername oder die IP-Adresse und der Instanzname für die Verbindung mit der benannten Instanz auf dem angegebenen lokalen oder Remotecomputer. Geben Sie diese Informationen im Format *Servername*\\*Instanzname*an.|  
|**Authentifizierungstyp**|Wählen Sie den Authentifizierungstyp aus, der für die Verbindung mit der angegebenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz verwendet werden soll. Welche Datenbanken in der Dropdownliste **Master Data Services-Datenbank** angezeigt werden, hängt von den Anmeldeinformationen ab, mit denen Sie die Verbindung herstellen. Mögliche Authentifizierungstypen:<br /><br /> **Aktueller Benutzer – integrierte Sicherheit von**: Verwendet integrierte Windows-Authentifizierung mithilfe der Anmeldeinformationen des aktuellen Windows-Benutzerkontos eine Verbindung herstellen. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] verwendet die Windows-Anmeldeinformationen des Benutzers, der am Computer angemeldet ist und die Anwendung geöffnet hat. Sie können keine anderen Windows-Anmeldeinformationen in der Anwendung angeben. Wenn Sie die Verbindung mit anderen Windows-Anmeldeinformationen herstellen möchten, müssen Sie sich als der betreffende Benutzer am Computer anmelden und [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]öffnen.<br /><br /> **SQL Server-Dienstkonto**: Verbindung wird eine SQL Server-Dienstkonto verwendet werden. Wenn Sie diese Option auswählen, sind die Felder **Benutzername** und **Kennwort** aktiviert, und Sie müssen Anmeldeinformationen für ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konto auf der betreffenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz angeben.|  
|**Benutzername**|Geben Sie den Namen des Benutzerkontos an, unter dem eine Verbindung mit der angegebenen SQL Server-Instanz hergestellt wird. Das Konto muss der Rolle **sysadmin** auf der angegebenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz angehören:<br /><br /> Wenn der **Authentifizierungstyp** auf **Aktueller Benutzer – Integrierte Sicherheit**festgelegt wurde, ist das Feld **Benutzername** schreibgeschützt und zeigt den Namen des Windows-Benutzerkontos an, das auf dem Computer angemeldet ist.<br /><br /> Wenn der **Authentifizierungstyp** auf **SQL Server-Konto**festgelegt wurde, ist das Feld **Benutzername** aktiviert, und Sie müssen Anmeldeinformationen für ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konto auf der betreffenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz angeben.|  
|**Kennwort**|Geben Sie das Kennwort ein, das dem Benutzerkonto zugeordnet ist:<br /><br /> Wenn der **Authentifizierungstyp** auf **Aktueller Benutzer – Integrierte Sicherheit** festgelegt wurde, ist das Feld **Kennwort** schreibgeschützt, und die Verbindung wird mit Anmeldeinformationen des angegebenen Windows-Benutzerkontos hergestellt.<br /><br /> Wenn der **Authentifizierungstyp** auf **SQL Server-Konto**festgelegt wurde, ist das Feld **Kennwort** aktiviert, und Sie müssen das Kennwort angeben, das dem betreffenden Benutzerkonto zugeordnet ist.|  
|**Verbinden**|Stellen Sie mit den angegebenen Anmeldeinformationen eine Verbindung mit der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz her.|  
|**Master Data Services-Datenbank**|Zeigt die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbanken in der angegebenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz auf Grundlage der folgenden Kriterien an:<br /><br /> Wenn der Benutzer Mitglied der Serverrolle **sysadmin** für diese Instanz ist, werden alle [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbanken in dieser Instanz angezeigt.<br /><br /> Wenn der Benutzer ein Mitglied der Datenbankrolle **db_owner** für beliebige [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbanken auf dieser Instanz ist, werden diese [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbanken angezeigt.<br /><br /> <br /><br /> Weitere Informationen zu SQL Server finden Sie unter [Rollen auf Serverebene](../relational-databases/security/authentication-access/server-level-roles.md) und [Rollen auf Datenbankebene](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankkonfiguration &#40;Seite im Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Einrichten von Datenbank und Website für Master Data Services](set-up-the-database-and-website-for-master-data-services.md)  
  
  
