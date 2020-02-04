---
title: Problembehandlung beim Veröffentlichen oder Anzeigen eines Berichts auf einem Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.date: 02/28/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
ms.assetid: df7720a1-d178-45bb-8d6f-63e208cae7fe
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6e3a96e3eef90778b0e7877b88ba79cb4e0dd43e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65573860"
---
# <a name="troubleshoot-publishing-or-viewing-a-report-on-a-native-mode-report-server"></a>Problembehandlung beim Veröffentlichen oder Anzeigen eines Berichts auf einem Berichtsserver im einheitlichen Modus
  
  
  
Wenn Sie einen Bericht auf einem im einheitlichen Modus konfigurierten Berichtsserver veröffentlichen oder auf diesen hochladen, treten möglicherweise Probleme auf, die für das Anzeigen von Berichten auf dem Berichtsserver spezifisch sind. Dieses Thema soll Ihnen beim Behandeln der folgenden Probleme helfen.   
  
## <a name="why-am-i-being-prompted-for-credentials-when-i-publish-a-report"></a>Warum werde ich zur Eingabe von Anmeldeinformationen aufgefordert, wenn ich einen Bericht veröffentliche?  
Um einen Bericht auf dem Berichtsserver bereitzustellen, müssen Sie die Adresse des Servers angeben. Möglicherweise wird das Dialogfeld Reporting Services-Anmeldung angezeigt, in dem Sie zur Eingabe von Anmeldeinformationen aufgefordert werden.   
  
Der Berichtsservername ist nicht ordnungsgemäß angegeben.  
  
  
Beim Bereitstellen eines Berichts auf einem Berichtsserver im einheitlichen Modus tritt häufig der Fehler auf, dass statt des Namens des Berichtsservers der Name des Berichtsordners angegeben wird.   
  
Stellen Sie sicher, dass die Berichtsserver-URL die Adresse des Berichtsservers (z. B. `https://localhost/reportserver`) und nicht die Adresse für das virtuelle Verzeichnis des Berichts-Managers (z. B. `https://localhost/reports`) ist. Wenn Sie für den Berichtsserver eine Portnummer angegeben haben, die nicht der Standard-Portnummer 80 entspricht, müssen Sie die Portnummer in der Adresse des Berichtsservers angeben (Beispiel: `https://localhost:81/reportserver`).   
  
 ## <a name="nothing-happens-when-i-toggle-items-in-my-published-report"></a>Wenn ich Elemente in meinem veröffentlichten Bericht ein-/ausschalte, geschieht nichts.  
  Wenn Sie einen Bericht in der lokalen Vorschau anzeigen, können Sie Elemente im Bericht ein-/ausschalten und sie anzeigen oder ausblenden. Wenn Sie denselben Bericht nach seiner Veröffentlichung auf dem Berichtsserver anzeigen, funktionieren Elemente zum Ein-/Ausschalten nicht mehr.   
  
\<Berichtsservername> enthält einen Unterstrich (_).  
  
Wenn ein Bericht ohne Fehler ausgeführt wird, jedoch Elemente zum Ein-/Ausschalten nicht funktionsfähig sind (wenn z. B. beim Klicken auf ein Erweiterungssymbol (+) nichts geschieht), prüfen Sie den Namen des Computers, der den Berichtsserver hostet. Wenn der Computername einen Unterstrich enthält, sind Elemente zum Ein-/Ausschalten nicht funktionsfähig. Dies ist ein bekanntes Problem. Dieses Problem kann nicht behoben werden.   
  
Für die Ausführung von Berichten mit Elemente zum Ein-/Ausschalten müssen Sie einen Computer verwenden, dessen Computername keine Unterstriche enthält.  
  
## <a name="images-and-charts-do-not-load-when-i-use-run-as-and-a-browser-to-run-my-report"></a>Bilder und Diagramme werden nicht geladen, wenn ich "Ausführen als" und einen Browser zum Ausführen meines Berichts verwende.  
Wenn Sie den Berichts-Manager in einem anderen Sicherheitskontext ausführen, werden möglicherweise nicht alle Berichtselemente in einem Bericht angezeigt.   
  
### <a name="insufficient-permissions-on-internet-temporary-file-folders"></a>Unzureichende Berechtigungen für Ordner mit temporären Internetdateien  
  
Wenn Sie den Berichts-Manager zum Anzeigen von veröffentlichten Berichten mit Diagrammen oder Bildern verwenden, werden diese in einigen Fällen eventuell nicht angezeigt. Wenn Sie beispielsweise den Microsoft Windows-Befehl **Ausführen als** verwenden, um einen Bericht unter Verwendung eines anderen Sicherheitskontexts anzuzeigen, verfügen Sie möglicherweise über keine Berechtigungen für den Ordner, in dem der Berichtsserver Diagramme und Bilder als temporäre Internetdateien zwischenspeichert.   
  
Überprüfen Sie, ob Sie über Berechtigungen für den Zugriff auf die Ordner verfügen, die die zwischengespeicherten Dateien enthalten.   
    
## <a name="see-also"></a>Weitere Informationen  
[Browser Support for Reporting Services and Power View (Browserunterstützung für Reporting Services und Power View)](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
[Fehler und Ereignisse (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
[Troubleshoot Data Retrieval issues with Reporting Services Reports (Problembehandlung: Probleme beim Abrufen von Daten in Reporting Services-Berichten)](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Troubleshoot Reporting Services Subscriptions and Delivery (Problembehandlung: Abonnements und Übermittlung in Reporting Services)](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

