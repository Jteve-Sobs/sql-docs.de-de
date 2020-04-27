---
title: Servereigenschaften (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93365925d412f672b9e8d3e5a9b5f67a850e508a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100000"
---
# <a name="server-properties-general-page"></a>Servereigenschaften (Seite Allgemein)
  Verwenden Sie diese Seite, um den im Berichts-Manager verwendeten Titel anzuzeigen oder zu ändern, um den Ordner Meine Berichte zu aktivieren oder zu deaktivieren, um eine Rollendefinition für die Sicherheit des Ordners Meine Berichte auszuwählen und um das Client-Drucksteuerelement zu aktivieren oder zu deaktivieren.  
  
 Um diese Seite zu öffnen, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten Sie, stellen eine Verbindung mit einer Berichts Serverinstanz her, klicken mit der rechten Maustaste auf den Namen des Berichts Servers und wählen dann **Eigenschaften**aus.  
  
 Der Servermodus bestimmt, welche Servereigenschaften Sie festlegen können. Wenn Sie einen Berichtsserver verwalten, der so konfiguriert ist, dass er im integrierten SharePoint-Modus ausgeführt wird, können Sie Meine Berichte nicht aktivieren und auch den Anwendungstitel für den Berichts-Manager nicht festlegen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Anwendungsnamen ein, der im Berichts-Manager angezeigt werden soll. Standardmäßig ist dieser Wert auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] festgelegt. Der von Ihnen angegebene Name wird nur im Berichts-Manager angezeigt.  
  
 **Version**  
 Diese Eigenschaft ist schreibgeschützt. Gibt die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] an, die Sie verwenden.  
  
 **Edition**  
 Diese Eigenschaft ist schreibgeschützt. Gibt die aktuelle Berichtsserverinstanz an. Der Berichts-Manager ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Authentifizierungsmodus**  
 Diese Eigenschaft ist schreibgeschützt. Sie identifiziert die Typen der von der Berichtsserverinstanz akzeptierten Authentifizierungsanforderungen. Möchten Sie den Authentifizierungsmodus ändern, müssen Sie die Datei RSReportServer.config ändern. Weitere Informationen finden Sie unter [Authentication with the Report Server](../security/authentication-with-the-report-server.md).  
  
 **URL**  
 Diese Eigenschaft ist schreibgeschützt. Sie gibt die URL zum Report Server-Webdienst an. Dieser Wert wird im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool angegeben. Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Für jeden Benutzer den Ordner 'Meine Berichte' aktivieren**  
 Den Ordner Meine Berichte für Benutzer verfügbar machen. Diese Option ist nur für Berichtsserver im einheitlichen Modus verfügbar.  
  
 **Wählen Sie die Rolle für jeden Ordner 'Meine Berichte' aus**  
 Geben Sie eine für die Sicherheit des Ordners Meine Berichte zu verwendende Rollendefinition an. Die Rollendefinition identifiziert die Aufgaben, die im jeweiligen Ordner Meine Berichte unterstützt werden.  
  
 **Download für das ActiveX-Client-Drucksteuerelement aktivieren**  
 Legt die `EnableClientPrinting`-Berichtsserver-Systemeigenschaft fest. Wenn Sie Clientdruck aktivieren, können Benutzer mit lokaler Administratorberechtigung ein signiertes ActiveX-Steuerelement zum Drucken von HTML-Berichten herunterladen. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#40;Management Studio Eigenschaften für Berichts Server festlegen&#41;](set-report-server-properties-management-studio.md)   
 [Herstellen einer Verbindung mit einem Berichts Server in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Aktivieren und Deaktivieren von Meine Berichte](../report-server/enable-and-disable-my-reports.md)   
 [Berichts Server in Management Studio F1-Hilfe](report-server-in-management-studio-f1-help.md)   
 [Sichern von Meine Berichte](../security/secure-my-reports.md)  
  
  
