---
title: Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 26175cfea8af6686f8c15840c7e44a5bde191df5
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175635"
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a>Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bestimmt mithilfe der rollenbasierten Autorisierung und eines Authentifizierungssubsystems, wer Vorgänge ausführen und auf Elemente auf einem Berichtsserver zugreifen kann. Die rollenbasierte Autorisierung teilt die Aktionen, die ein Benutzer oder eine Gruppe ausführen kann, in Rollen ein. Die Authentifizierung basiert auf der integrierten Windows-Authentifizierung oder auf einem von Ihnen bereitgestellten benutzerdefinierten Authentifizierungsmodul. Bei beiden Authentifizierungstypen können vordefinierte oder benutzerdefinierte Rollen verwendet werden.  
  
## <a name="using-roles-to-grant-report-server-access"></a>Verwenden von Rollen zum Gewähren des Zugriffs auf einen Berichtsserver  
 Alle Benutzer interagieren mit einem Berichtsserver im Rahme ihrer Rolle, die eine bestimmte Ebene des Zugriffs definiert. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält vordefinierte Rollen, die Sie Benutzern und Gruppen zuweisen können, um unmittelbaren Zugriff auf einen Berichtsserver bereitzustellen. Vordefinierte Rollen sind z.B.**Inhalts-Manager**, **Verleger**und **Browser** . Jede Rolle definiert eine Auflistung verwandter Aufgaben. Zum Beispiel ist ein **Verleger** berechtigt, Berichte hinzuzufügen und Ordner zum Speichern dieser Berichte zu erstellen.  
  
 Rollenzuweisungen werden i. d. R. von einem übergeordneten Knoten geerbt, allerdings können Sie die Vererbung von Berechtigungen unterbrechen, indem Sie für ein bestimmtes Element eine neue Rollenzuweisung erstellen. Ein Benutzer, der für einen Bericht Mitglied der **Inhalts-Manager** -Rolle ist, kann für einen anderen Bericht Mitglied der **Browser** -Rolle sein.  
  
 Beachten Sie die folgenden Richtlinien, um den Zugriff auf Berichtsserverelemente und -vorgänge zu gewähren:  
  
1.  Überprüfen Sie die vordefinierten Rollen, um zu ermitteln, ob Sie sie unverändert verwenden können. Wenn Sie die Aufgaben anpassen oder zusätzliche Rollen definieren müssen, sollte dies erfolgen, bevor Sie den einzelnen Rollen Benutzer zuweisen. Weitere Informationen zu den einzelnen Rollen finden Sie unter [Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md).  
  
2.  Identifizieren Sie, für welche Benutzer und Gruppen der Zugriff auf den Berichtsserver erforderlich ist und auf welcher Ebene. Die meisten Benutzer sollten der **Browser** -Rolle oder der **Berichts-Generator** -Rolle zugewiesen werden. Eine kleinere Anzahl von Benutzern sollte der **Verleger** -Rolle zugewiesen werden. **Inhalts-Manager**sollten nur sehr wenige Benutzer zugewiesen werden.  
  
3.  Verwenden Sie das Webportal, um im Stammordner (dem Ordner auf der obersten Ebene der Ordnerhierarchie des Berichtsservers) Rollen für jeden Benutzer oder jede Gruppe zuzuweisen, der bzw. die Zugriff benötigt.  
  
4.  Erstellen Sie im Webportal auf der Seite „Websiteeinstellungen“ mithilfe der vordefinierten Rollen **Systembenutzer** und **Systemadministrator** eine Rollenzuweisung auf Systemebene für jeden Benutzer und jede Gruppe.  
  
5.  Erstellen Sie nach Bedarf zusätzliche Rollenzuweisungen für bestimmte Ordner, Berichte und andere Elemente. Erstellen Sie keine große Anzahl von Rollenzuweisungen. Wenn Sie zu viele Rollenzuweisungen erstellen, ist es schwierig, den Überblick über die verschiedenen Berechtigungsebenen der einzelnen Benutzer zu behalten.  
  
> [!NOTE]  
>  Wenn Sie einen Berichtsserver für die Ausführung im integrierten SharePoint-Modus konfiguriert haben, müssen Sie die Berechtigungen auf der SharePoint-Website festlegen, um den Zugriff auf Berichtsserverelemente zu gewähren. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
## <a name="who-sets-permissions"></a>Wer Berechtigungen festgelegt  
 Anfänglich können nur Benutzer, die Mitglieder der lokalen Administratorgruppe sind, auf einen Berichtsserver zugreifen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird mit zwei Standardrollenzuweisungen installiert, die Zugriff auf Element- und auf Systemebene für Mitglieder der lokalen Administratorgruppe gewähren. Mithilfe dieser integrierten Rollenzuweisungen können lokale Administratoren anderen Benutzern Zugriff auf den Berichtsserver gewähren und Berichtsserverelemente verwalten. Die integrierten Rollenzuweisungen können nicht gelöscht werden. Ein lokaler Administrator verfügt immer über die Berechtigung zur vollständigen Verwaltung einer Berichtsserverinstanz.  
  
 Da Vollberechtigungen für einen Berichtsserver Berechtigungen auf Element- und Systemebene umfassen, wird ein lokaler Administrator folgenden Rollen zugewiesen:  
  
 Bevor eine Berichtsserverinstanz auf einem lokalen Computer, auf dem Windows Vista oder Windows Server 2008 ausgeführt wird, verwaltet werden kann, sind zusätzliche Konfigurationsschritte erforderlich. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="how-permissions-are-stored"></a>Wie Berechtigungen gespeichert werden  
 Rollenzuweisungen und -definitionen werden in der Berichtsserver-Datenbank gespeichert. Wenn Sie mit verschiedenen Clienttools oder programmgesteuerten Schnittstellen arbeiten, hängt jeder Zugriff von den Berechtigungen ab, die für die Berichtsserverinstanz insgesamt definiert sind. Wenn Sie mehrere Berichtsserver in einer Bereitstellung für horizontales Skalieren konfigurieren, werden die von Ihnen in einer Instanz definierten Rollenzuweisungen in einer freigegebenen Datenbank gespeichert und von allen anderen Instanzen in derselben Bereitstellung für horizontales Skalieren verwendet. Da Rollenzuweisungen zusammen mit den durch sie gesicherten Elementen gespeichert werden, können Sie die Datenbank zu einer anderen Berichtsserverinstanz verschieben, ohne dass die definierten Berechtigungen verloren gehen.  
  
## <a name="tasks-and-tools-for-managing-permissions"></a>Aufgaben und Tools zum Verwalten von Berechtigungen  
 Verwenden Sie die folgenden Tools, um Rollendefinitionen und -zuweisungen zu verwalten.  
  
|Tool|Aufgaben|  
|----------|-----------|  
|Management Studio - zum Anzeigen, Ändern, Erstellen und Löschen von Rollendefinitionen|[Erstellen, Löschen oder Ändern einer Rolle &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)|  
|Das Webportal – zum Zuweisen von Benutzern und Gruppen zu Rollen|[Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md)<br /><br /> [Ändern oder Löschen einer Rollenzuweisung](../../reporting-services/security/role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md)   
 [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Authentifizierung mit dem Berichtsserver](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Erstellen und Verwalten von Rollenzuweisungen](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Sicherheit und Schutz für Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
