---
title: Aktivieren eines Berichtsservers für einen Zugriff auf Power BI Mobile | Microsoft-Dokumentation
ms.date: 12/17/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: c1a71522-394b-46a7-b9ec-f964bdd81d82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d14c8e092a030c88dbc4d0b5d4375bb56a8eb82c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "63308180"
---
# <a name="enable-a-report-server-for-power-bi-mobile-access"></a>Aktivieren eines Berichtsservers für einen Zugang zu Power BI von Mobilgeräten
Sie können die mobile Power BI-App verwenden, um Mobile Berichte zu nutzen. Sie müssen einige Dinge konfigurieren, damit die mobile Power BI-App eine Verbindung mit Reporting Services herstellen kann.  
  
-   [Mobile Berichte erfordern Reporting Services im einheitlichen Modus](#nativemode)  
-   [Aktivieren der Standardauthentifizierung für Reporting Services](#basicauth) (für CTP 3.2)  
-   [Es wird empfohlen, HTTPS zusammen mit einem gültigen und vertrauenswürdigen Zertifikat für das Client-Gerät zu aktivieren](#https)  
-   [Überprüfen der Firewalleinstellungen](#firewall)  
  
<a name="nativemode"/>  
## <a name="reporting-services-native-mode-required"></a>Einheitlicher Modus von Reporting Services erforderlich  
Mobile Berichte sind eine Funktion des einheitlichen Modus. Im integrierten SharePoint-Modus sind Mobile Berichte nicht verfügbar. Die mobile Power BI-App funktioniert nur mit einer Instanz im einheitlichen Modus.  
  
<a name="basicauth"/>  
## <a name="enable-basic-authentication"></a>Aktivieren der Standardauthentifizierung  
Die mobile Power BI-App für iOS erfordert eine Standardauthentifizierung, um eine Verbindung zu Mobile Berichte herstellen und sie nutzen zu können. In der standardmäßigen Konfigurierung von Reporting Services ist die Standardauthentifizierung nicht aktiviert. Informationen zum Konfigurieren der Standardauthentifizierung finden Sie unter [Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).  
  
Sie müssen auch die Windows-Authentifizierung aktivieren, damit die Verleger-App Mobile Berichte veröffentlichen kann.  
  
<a name="https"/>  
## <a name="enable-https"></a>Aktivieren von HTTPS  
Es wird empfohlen, dass Sie HTTPS in Reporting Services aktivieren, wenn Sie die Standardauthentifizierung aktivieren. Wenn Sie HTTPS aktivieren, stellen Sie sicher, dass die Zertifikate auf den Clientgeräten, die die mobile Power BI-App für iOS ausführen, vertrauenswürdig sind. Das bedeutet, dass die Zertifizierungskette gültig und für das Clientgerät verfügbar sein muss.  
  
Wenn Sie für Entwicklungs-oder Testzwecke ein selbstsigniertes Zertifikat verwenden müssen, können Sie das Zertifikat vom Berichtsserver exportieren und es auf dem mobilen Gerät installieren. Informationen zur Installation dieses Zertifikats auf Ihrem Mobilgerät finden Sie in der Dokumentation des Mobilgeräts.  
  
Weitere Informationen zur Aktivierung von SSL finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
<a name="firewall"/>  
## <a name="review-firewall-settings"></a>Überprüfen der Firewalleinstellungen  
Wir empfehlen eine Überprüfung der Firewalleinstellungen, um sicherzustellen, dass sich alle Geräte mit Reporting Services verbinden können.   
  
Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Weitere Informationen  
  
[Configure Basic Authentication on the Report Server (Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver)](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
[Configure SSL Connections on a Native Mode Report Server (Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus)](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)  
[Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
  
  
  
  

