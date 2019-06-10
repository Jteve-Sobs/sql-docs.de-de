---
title: Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 92c0943b17f22c63481f1dbfb0f76977a4b71381
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66500230"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver
  Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in einem Netzwerk bereitstellen, in dem das Kerberos-Protokoll zur gegenseitigen Authentifizierung verwendet wird, müssen Sie einen Dienstprinzipalnamen (SPN) für den Berichtsserverdienst erstellen, wenn Sie diesen als Domänenbenutzerkonto konfigurieren.  
  
## <a name="about-spns"></a>Informationen zu SPNs  
 Ein SPN ist ein eindeutiger Bezeichner für einen Dienst in einem Netzwerk mit Kerberos-Authentifizierung. SPNs bestehen aus einer Dienstklasse, einem Hostnamen und (manchmal) einem Port. HTTP-SPNs erfordern keinen Port. In einem Netzwerk mit Kerberos-Authentifizierung muss ein SPN für den Server unter einem integrierten Computerkonto wie NetworkService oder LocalSystem oder unter einem Benutzerkonto registriert sein. SPNs werden automatisch für integrierte Konten registriert. Wenn Sie einen Dienst unter einem Domänenbenutzerkonto ausführen, müssen Sie den SPN manuell für das Konto registrieren, das Sie verwenden möchten.  
  
 Um einen SPN zu erstellen, können Sie das Befehlszeilen-Hilfsprogramm **SetSPN** verwenden. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [SetSPN](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx)  
  
-   [SetSPN-Syntax (Setspn.exe) für Dienstprinzipalnamen (SPN)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Sie müssen Domänenadministrator sein, um das Hilfsprogramm auf dem Domänencontroller auszuführen.  
  
## <a name="syntax"></a>Syntax  
 Die Befehlssyntax für die Verwendung des Hilfsprogramms SetSPN zum Erstellen eines SPN für den Berichtsserver kann z. B. wie folgt lauten:  
  
```  
Setspn -s http/<computername>.<domainname> <domain-user-account>  
```  
  
 **SetSPN** ist in Windows Server verfügbar. Mit dem Argument **-s** wird ein SPN hinzugefügt, nachdem überprüft wurde, dass kein doppelter Name vorhanden ist. **HINWEIS:** „-s“ ist in Windows Server ab Windows Server 2008 verfügbar.  
  
 **HTTP** ist die Dienstklasse. Der Report Server-Webdienst wird in HTTP.SYS ausgeführt. Wenn Sie einen SPN für HTTP erstellen, werden allen Webanwendungen auf dem gleichen Computer, die in HTTP.SYS ausgeführt werden (einschließlich der Anwendungen, die in IIS gehostet werden), Tickets auf der Basis des Domänenbenutzerkontos zugewiesen. Wenn diese Dienste unter einem anderen Konto ausgeführt werden, können Authentifizierungsanforderungen nicht ordnungsgemäß verarbeitet werden. Konfigurieren Sie deshalb alle HTTP-Anwendungen zur Ausführung unter dem gleichen Konto, oder erstellen Sie Hostheader für jede Anwendung und anschließend je einen SPN pro Hostheader. Wenn Sie Hostheader konfigurieren, sind DNS-Änderungen unabhängig von der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfiguration erforderlich.  
  
 Die Werte für \<*computername*> und \<*domainname*> bezeichnen die eindeutige Netzwerkadresse des Computers, der den Berichtsserver hostet. Dies kann ein lokaler Hostname oder ein vollqualifizierter Domänenname (FQDN) sein. Wenn Sie nur über eine Domäne verfügen, ist \<*domainname*> in der Befehlszeile nicht erforderlich. \<*domäne-benutzer-konto*> ist das Benutzerkonto, unter dem der Berichtsserverdienst ausgeführt wird und für das der SPN registriert werden muss.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Registrieren eines SPNs für ein Domänenbenutzerkonto  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>So registrieren Sie einen SPN für einen Berichtsserverdienst, der als Domänenbenutzer ausgeführt wird  
  
1.  Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , und konfigurieren Sie den Berichtsserverdienst zur Ausführung als Domänenbenutzerkonto. Erst wenn Sie die folgenden Schritte ausgeführt haben, können Benutzer eine Verbindung mit dem Berichtsserver herstellen.  
  
2.  Melden Sie sich als Domänenadministrator beim Domänencontroller an.  
  
3.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
4.  Kopieren Sie den folgenden Befehl, um Platzhalterwerte durch gültige Werte für das Netzwerk zu ersetzen:  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name> <domain-user-account>  
    ```  
  
     Beispiel: `Setspn -s http/MyReportServer.MyDomain.com MyDomainUser`  
  
5.  Führen Sie den Befehl aus.  
  
6.  Öffnen Sie die Datei **RsReportServer.config** , und suchen Sie den Abschnitt `<AuthenticationTypes>` .  
  
7.  Fügen Sie `<RSWindowsNegotiate/>` als ersten Eintrag in diesem Abschnitt hinzu, um Kerberos zu aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
