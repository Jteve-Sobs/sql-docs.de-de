---
title: Reporting Services-Anmeldung (Dialogfeld) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3d60450f0f4c7feb7d6a00f66fcedeb89c764bf5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77082174"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Reporting Services-Anmeldung (Dialogfeld) (SSRS)
  Verwenden Sie das Dialogfeld **Reporting Services-Anmeldung** , um die Anmeldeinformationen zum Veröffentlichen von Berichten auf dem Berichtsserver bereitzustellen.  
  
-   **Hinweis** : Wenn dies das erste Mal seit Festlegen der Bereitstellungseigenschaft **TargetServerURL** für ein Projekt ist, dass Sie einen Bericht auf einem Berichtsserver veröffentlichen, vergewissern Sie sich, dass der angegebene Servername **Server** anstatt **Berichte**enthält. Beispiel: `https://localhost/reportserver`und nicht das Format `https://localhost/reports`. Durch Angeben des `reports` -Verzeichnisses auf dem lokalen Server anstelle des `reportserver` -Verzeichnisses wird indirekt bewirkt, dass dieses Dialogfeld geöffnet wird. Weitere Informationen zum Festlegen von **TargetServerURL** finden Sie unter [Festlegen von Bereitstellungseigenschaften (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Tastatur  
 **Server**  
 Zeigt den Namen des Berichtsservers an. Beispiel: `https://localhost/reportserver`. Für Berichtsserver, die einen anderen Port verwenden als Standardport 80, schließen Sie die Portnummer ein. Beispiel: `https://localhost:81/reportserver`.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, der beim Anmelden am Webdienst verwendet werden soll.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, das beim Anmelden am Webdienst verwendet werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Report Designer F1 Help (Berichts-Designer (F1-Hilfe))](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
