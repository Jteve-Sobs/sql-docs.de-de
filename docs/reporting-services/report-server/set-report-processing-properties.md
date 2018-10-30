---
title: Festlegen von Berichtsverarbeitungseigenschaften | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- on-demand reports
- report processing [Reporting Services], execution properties
- snapshots [Reporting Services], running reports from
- cached reports [Reporting Services]
- report snapshots [Reporting Services], running reports from
- report execution snapshots [Reporting Services]
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3b0f9d441db188551b1b2073e968c8f000b21107
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50031769"
---
# <a name="set-report-processing-properties"></a>Festlegen von Berichtsverarbeitungseigenschaften
  Durch Eigenschaften zur Berichtsausführung wird die Verarbeitung von Berichten gesteuert. Ausführungseigenschaften müssen für jeden Bericht separat festgelegt werden.  
  
 Um Eigenschaften zur Berichtsausführung festzulegen, öffnen Sie den Bericht im Berichts-Manager, und navigieren Sie dann zur Ausführungseigenschaftenseite. Weitere Informationen finden Sie unter [Verarbeitungsoptionen (Eigenschaftenseite) (Berichts-Manager)](https://msdn.microsoft.com/library/28f07c70-7132-4d15-9505-4fdf31dc9cc0). Sie können auch mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Eigenschaften festlegen. Weitere Informationen finden Sie unter [Verarbeitungsoptionen (Eigenschaftenseite) (Berichts-Manager)](https://msdn.microsoft.com/library/28f07c70-7132-4d15-9505-4fdf31dc9cc0).  
  
## <a name="report-execution-modes"></a>Berichtsausführungsmodi  
 Ein Bericht kann bei Bedarf oder als Momentaufnahme ausgeführt werden. Die beiden Vorgehensweisen werden im nächsten Abschnitt beschrieben.  
  
### <a name="running-reports-on-demand"></a>Ausführen von Berichten bei Bedarf  
 Sie können angeben, dass ein Bericht eine Datenquelle jedes Mal abfragt, wenn ein Benutzer den Bericht ausführt. Das Ergebnis sind bedarfsgesteuerte Berichte, die die aktuellsten Daten enthalten. Eine neue Instanz des Berichts wird für jeden Benutzer erstellt, der den Bericht öffnet oder anfordert. Jede neue Instanz enthält die Ergebnisse einer neuen Abfrage. Wenn bei dieser Vorgehensweise zehn Benutzer gleichzeitig den Bericht öffnen, werden zehn Abfragen zur Verarbeitung an die Datenquelle gesendet.  
  
### <a name="running-reports-on-demand-from-cache"></a>Bedarfsgesteuerte Ausführung von Berichten aus dem Cache  
 Um die Leistung zu verbessern, können Sie angeben, dass ein Bericht (und Daten) vorübergehend zwischengespeichert wird, wenn ein Benutzer den Bericht ausführt. Die zwischengespeicherte Kopie ist dann später für andere Benutzer verfügbar, die auf denselben Bericht zugreifen. Wenn bei dieser Vorgehensweise zehn Benutzer den Bericht öffnen, führt nur die erste Anforderung zu einer Verarbeitung des Berichts. Der Bericht wird dann zwischengespeichert, und für die restlichen neun Benutzer wird der aus dem Cache abgerufene Bericht angezeigt.  
  
 Zwischengespeicherte Berichte werden in den von Ihnen definierten Intervallen aus dem Cache entfernt. Sie können Intervalle in Minuten angeben oder aber einen bestimmten Zeitpunkt (Datum und Uhrzeit) zum Leeren des Caches festlegen. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
### <a name="running-reports-from-snapshots"></a>Ausführen von Berichten von Momentaufnahmen  
 Eine Berichtsmomentaufnahme ist ein Bericht, der Layoutinformationen und Daten enthält, die zu einem bestimmten Zeitpunkt abgerufen werden. Sie können einen Bericht als Berichtsmomentaufnahme ausführen, um zu verhindern, dass der Bericht zu willkürlichen Zeiten ausgeführt wird (z. B. während einer geplanten Sicherung). Eine Berichtsmomentaufnahme wird gewöhnlich gemäß einem Zeitplan erstellt und später aktualisiert. Auf diese Weise können Sie genau planen, wann der Bericht und die Daten verarbeitet werden. Falls ein Bericht auf Abfragen basiert, deren Ausführung viel Zeit in Anspruch nimmt oder die Daten von einer Datenquelle verwenden, auf die während eines bestimmten Zeitraums kein Benutzer Zugriff haben soll, sollten Sie den Bericht als Momentaufnahme ausführen.  
  
 Eine Berichtsmomentaufnahme wird in einer Berichtsserver-Datenbank gespeichert, von wo er später abgerufen wird, wenn ein Benutzer oder Prozess (z. B. ein Abonnement) den Bericht anfordert. Wenn eine Berichtsmomentaufnahme aktualisiert wird, wird sie durch eine neue Instanz überschrieben. Der Berichtsserver speichert nur dann vorherige Versionen eines Berichtsmomentaufnahmen, wenn Sie ausdrücklich in den Optionen festlegen, dass sie dem Berichtsverlauf hinzugefügt werden sollen. Weitere Informationen finden Sie unter [Erstellen, Ändern und Löschen von Momentaufnahmen im Berichtsverlauf](../../reporting-services/report-server/create-modify-and-delete-snapshots-in-report-history.md).  
  
 Nicht alle Berichte können für das Ausführen als Momentaufnahme konfiguriert werden. Sie können beispielsweise keine Momentaufnahme für einen Bericht erstellen, der Benutzer zur Eingabe von Anmeldeinformationen auffordert oder die integrierte Sicherheit von Windows verwendet, um Daten für den Bericht abzurufen. Falls Sie einen parametrisierten Bericht als Momentaufnahme ausführen möchten, müssen Sie einen Standardparameter angeben, der beim Erstellen der Momentaufnahme verwendet werden soll. Anders als bei Berichten, die bei Bedarf ausgeführt werden, kann für eine Berichtsmomentaufnahme kein anderer Parameterwert mehr angegeben werden, sobald der Bericht geöffnet ist. Das Auswählen eines anderen Parameterwertes würde zur Folge haben, dass ein neuer Bericht die Anforderung verarbeitet, was nicht zulässig ist.  
  
 Wenn Sie einen bedarfsgesteuerten Bericht so konfigurieren, dass er als Momentaufnahme ausgeführt wird, kann dies dazu führen, dass Abonnements deaktiviert werden. Die folgende Bedingung bewirkt, dass ein Berichtsserver vorhandene Abonnements deaktiviert. Diese wurden definiert, als der Bericht für eine bedarfsgesteuerte Ausführung konfiguriert wurde:  
  
-   In dem Bericht werden Abfrageparameter verwendet. Um die Anforderungen zum Ausführen des Berichts als Momentaufnahme zu erfüllen, wählen Sie einen bestimmten Wert als Standardparameter aus.  
  
-   Vorhandene Abonnements werden so konfiguriert, dass sie Parameterwerte verwenden, die sich von dem für die Momentaufnahme angegebenen Standardparameterwert unterscheiden.  
  
 Bei dieser Bedingung deaktiviert der Berichtsserver das Abonnement zu dem Zeitpunkt, zu dem die nächste Ausführung des Abonnements geplant ist. Um das Abonnement erneut zu aktivieren, öffnen und speichern Sie das Abonnement. Beim Öffnen des Abonnements aktualisiert der Berichtsserver die für die Momentaufnahme definierten Werte für die Abonnementparameter. Weitere Informationen zu Abonnements finden Sie unter [Abonnements und Übermittlung (Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Festlegen von Verarbeitungsoptionen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Konfigurieren von Ausführungseigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)   
 [Konzepte von Reporting Services (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Vorgehensweise: Hinzufügen einer Momentaufnahme zum Berichtsverlauf](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Specify Credential and Connection Information for Report Data Sources (Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen)](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
