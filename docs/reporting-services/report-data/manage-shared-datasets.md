---
title: Verwalten von freigegebenen Datasets | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie freigegebene Datasets in den Reporting Services verwalten, damit Sie eine Abfrage freigeben können, die Sie beim Bereitstellen konsistenter Datasets für mehrere Berichte unterstützt.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 2cbb1fa3-959e-4df6-9887-ebc93cc1b686
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: df22dbab5cf450981f53976fb2a09e6ff08797c8
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85808440"
---
# <a name="manage-shared-datasets"></a>Verwalten von freigegebenen Datasets
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]werden mit freigegebenen Datasets Daten aus freigegebenen Datenquellen abgerufen, die mit externen Datenquellen verbunden werden. Ein freigegebenes Dataset bietet die Möglichkeit, eine Abfrage freizugeben und so konsistente Daten für mehrere Berichte bereitzustellen. Die Datasetabfrage kann Datasetparameter enthalten. Sie können ein freigegebenes Dataset so konfigurieren, dass Abfrageergebnisse für bestimmte Parameterkombinationen bei der erstmaligen Verwendung oder nach einem angegebenen Zeitplan zwischengespeichert werden. Sie können das Zwischenspeichern freigegebener Datasets mit dem Zwischenspeichern von Berichten sowie mit Berichtsdatenfeeds kombinieren, um den Zugriff auf eine Datenquelle einfacher zu verwalten.  
  
 Freigegebene Datasets verwenden ausschließlich freigegebene Datenquellen, keine eingebetteten Datenquellen. Ein freigegebenes Dataset kann auf einer beliebigen Datenquelle für eine unterstützte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenerweiterung oder auf einem Berichtsmodell basieren.  
  
## <a name="creating-and-using-shared-datasets"></a>Erstellen und Verwenden von freigegebenen Datasets  
 Zum Erstellen eines freigegebenen Datasets müssen Sie eine Anwendung verwenden, durch die eine Datei für Definitionen freigegebener Datasets (.rsd) erstellt wird. Sie können mithilfe einer der folgenden Anwendungen ein freigegebenes Dataset erstellen:  
  
-   Berichts-Generator   Verwenden Sie den Entwurfsmodus für freigegebene Datasets, und speichern Sie das freigegebene Dataset auf einem Berichtsserver oder auf einer SharePoint-Website.  
  
-   Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]/Visual Studio zum Erstellen freigegebener Datasets im Ordner „Datasets“ im Projektmappen-Explorer. Um ein freigegebenes Dataset zu veröffentlichen, stellen Sie es auf einem Berichtsserver oder auf einer SharePoint-Website bereit.  
  
-   Hochladen einer Definitionsdatei für freigegebene Datasets (.rsd) Sie können eine Datei auf den Berichtsserver oder auf eine SharePoint-Website hochladen. Auf einer SharePoint-Website. Eine hochgeladene Datei wird erst anhand des Schemas überprüft, wenn das freigegebene Dataset zwischengespeichert oder in einem Bericht verwendet wird.  
  
 Die Definition für freigegebene Datasets enthält eine Abfrage, Datasetparameter einschließlich Standardwerten, Datenoptionen wie die Berücksichtigung der Groß-/Kleinschreibung und Datasetfilter. Die in der Definition festgelegten Werte werden angewendet, sobald das freigegebene Dataset in einem Bericht verwendet wird.  
  
 Öffnen Sie zur Verwendung eines freigegebenen Datasets in einem Bericht eine Anwendung wie den Berichts-Generator, wechseln Sie zum Berichtsserver oder zur SharePoint-Website, und wählen Sie das freigegebene Dataset aus. Dadurch wird dem Bericht eine Instanz des freigegebenen Datasets hinzugefügt. Die Abfrage oder die freigegebene Datenquelle für das freigegebene Dataset kann im Bericht weder angezeigt noch geändert werden. Sie können zusätzliche Dataseteigenschaftswerte angeben, die auf die Instanz im Bericht angewendet werden. Sie können z. B. einen Filter hinzufügen oder Datenoptionen wie die Berücksichtigung der Groß-/Kleinschreibung ändern. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="managing-shared-datasets"></a>Verwalten freigegebener Datasets  
 Zum Verwalten der Eigenschaften eines veröffentlichten freigegebenen Datasets verwenden Sie das Webportal, wenn der Berichtsserver im einheitlichen Modus ausgeführt wird, oder Anwendungsseiten auf einer SharePoint-Website, wenn der Berichtsserver im integrierten SharePoint-Modus bereitgestellt wird. Welche Tasks für ein freigegebenes Dataset ausgeführt werden können, hängt von Ihren Rollenzuweisungen und den Berechtigungen auf Website- und auf Elementebene ab, einschließlich der Berechtigungen für den Ordner, wenn die Vererbung von Berechtigungen aktiviert ist. Bei der Sicherheit auf Elementebene für freigegebene Datasets gilt das gleiche Modell wie bei der Sicherheit auf Elementebene für Berichte. Weitere Informationen finden Sie unter [Sichern von freigegebenen Datasetelementen](../../reporting-services/security/secure-shared-dataset-items.md).  
  
 Sie können die Eigenschaften freigegebener Datasetelemente, einschließlich der zu verwendenden freigegebenen Datenquelle, unabhängig von dem Bericht verwalten, der das freigegebene Dataset oder die freigegebene Datenquelle verwendet, von dem bzw. der er abhängig ist. Um die Abfrage oder andere Dataseteigenschaften zu ändern, die Teil der Definition des freigegebenen Datasets sind, müssen Sie die Definition bearbeiten.  
  
### <a name="manage-shared-dataset-item-properties"></a>Verwalten der Eigenschaften freigegebener Datasetelemente  
 In der folgenden Tabelle sind die Elementeigenschaften aufgeführt, die Sie für ein freigegebenes Datasetelement ändern können.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------|-----------|  
|Namen bearbeiten|Ändern Sie den Namen des freigegebenen Datasets. Alle Verweise von abhängigen Elementen sind weiterhin funktionsfähig.|  
|Beschreibung bearbeiten|Ändern Sie die Beschreibung des freigegebenen Datasets.|  
|Timeout für Abfrageausführung bearbeiten|Legen Sie das Timeout für die Abfrageausführung in Sekunden fest. 0 (null) Sekunden bedeutet kein Timeout. Bestimmt die Anzahl von Sekunden, nach denen ein Timeout bei der Datasetabfrage eintritt. Um keinen Timeoutwert anzugeben, verwenden Sie 0. Weitere Informationen finden Sie unter [Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets (SSRS)](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md).|  
|Abhängige Elemente anzeigen|Zeigen Sie die Elemente an, die dieses freigegebene Dataset verwenden: veröffentlichte Berichtsteile, freigegebene Datenquellen und Berichte.|  
  
 Die folgenden zusätzlichen Eigenschaften für freigegebene Datasets werden automatisch konfiguriert:  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|HasDataSourceCredentials|Gibt an, ob die zugeordnete freigegebene Datenquelle über gespeicherte Anmeldeinformationen auf dem Berichtsserver verfügt.|  
|HasUserProfileDependencies|Gibt an, ob der Bericht in der Abfrage oder in Filterausdrücken über einen Verweis auf die globale User-Auflistung verfügt.|  
  
## <a name="viewing-or-changing-the-shared-dataset-definition"></a>Anzeigen oder Ändern der Definition eines freigegebenen Datasets  
 Eigenschaften freigegebener Datasets, einschließlich der Abfrage, Datasetparameter, Standardwerte, Datasetfilter und Datenoptionen z. B. zur Sortierung und Berücksichtigung der Groß-/Kleinschreibung, werden in der Definition des freigegebenen Datasets gespeichert. Sofern Sie über ausreichende Berechtigungen verfügen, können Sie die Definition anzeigen und ändern.  
  
 Zum Anzeigen oder Ändern der Definition des freigegebenen Datasets bearbeiten Sie das freigegebene Dataset in einer Anwendung wie dem Berichts-Generator im Entwurfsmodus für freigegebene Datasets. Nachdem Sie Änderungen vorgenommen haben, speichern Sie die Definition des freigegebenen Datasets wieder auf dem Server oder der Website.  
  
 Eine weitere Möglichkeit, die Definition des freigegebenen Datasets in XML anzuzeigen, besteht darin, die URL-Zugriffssyntax im Webportal zu verwenden. Zum Anzeigen der Standardwerte für die einzelnen Datasetparameter können Sie z. B. den folgenden URL-Zugriffsbefehl verwenden, um eine Definition für ein freigegebenes Dataset mit dem Namen DataSet1 vom Berichtsserver anzuzeigen:  
  
## <a name="controlling-access-to-the-shared-dataset-definition"></a>Steuern des Zugriffs auf die Definition für freigegebene Datasets  
 Die folgenden Tasks beziehen sich standardmäßig auf Vorgänge für freigegebene Datasets.  
  
-   **Berichte anzeigen** Anzeigen freigegebener Datasetelemente und Elementeigenschaften.  
  
-   **Berichte lesen** Lesen von Definitionen für freigegebene Datasets.  
  
-   **Berichte verwalten** Erstellen und Löschen freigegebener Datasets und Bearbeiten der Eigenschaften freigegebener Datasets.  
  
-   **Sicherheit für einzelne Elemente festlegen** Anzeigen und Ändern der Sicherheitseinstellungen für freigegebene Datasets.  
  
 Weitere Informationen darüber, welche Tasks und Berechtigungen den Zugriff auf Datenquelleigenschaften auf einem im einheitlichen Modus ausgeführten Berichtsserver steuern, finden Sie unter [Sichern von freigegebenen Datasetelementen](../../reporting-services/security/secure-shared-dataset-items.md).  
  
 Berechtigungen zum Anzeigen und Bearbeiten von Eigenschaften für Elemente in einer SharePoint-Bibliothek werden vom Websiteadministrator zugeteilt. Weitere Informationen finden Sie unter [Referenz zu SharePoint Website- und Listenberechtigungen für Berichtsserverelemente](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).  
  
## <a name="how-to-work-with-shared-dataset-properties-on-a-report-server"></a>Arbeiten mit Eigenschaften freigegebener Datasets auf Berichtsservern  
 Es stehen zahlreiche Tools für die Arbeit mit freigegebenen Datasets zur Verfügung. In der folgenden Tabelle sind die verschiedenen Methoden und Tools zusammengefasst. Ein Link führt zu weiteren Anweisungen.  
  
|Aufgabe      |Tool      |Link      |  
|----------|----------|----------|  
|Hinzufügen eines freigegebenen Datasets oder Ändern der Eigenschaften der Definition eines freigegebenen Datasets.|Speichern im Berichts-Generator.<br /><br /> Bereitstellen im Berichts-Designer.<br /><br /> Hochladen einer RSD-Datei im Webportal|[Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)]<br /><br /> [Hochladen einer Datei oder eines Berichts auf den Berichtsserver](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)<br /><br /> Wenn Sie ein freigegebenes Dataset hochladen, bevor die freigegebene Datenquelle, von der das Dataset abhängig ist, veröffentlicht wird, müssen Sie das freigegebene Dataset manuell an die freigegebene Datenquelle binden. Weitere Informationen finden Sie unter [Arbeiten mit freigegebenen Datasets (Webportal)](../work-with-shared-datasets-web-portal.md).|  
|Ändern der Eigenschaften freigegebener Datasetelemente|Webportal|[Arbeiten mit freigegebenen Datasets – Webportal](../../reporting-services/work-with-shared-datasets-web-portal.md)|  
|Angeben zusätzlicher Eigenschaften für freigegebene Datasets für die Instanz eines freigegebenen Datasets in einem Bericht.|Berichts-Generator, Berichts-Designer|[Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator)](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md)|  
|Binden an eine andere freigegebene Datenquelle für ein freigegebenes Dataset.|Webportal|[Konfigurieren von Datenquelleneigenschaften für einen paginierten Bericht – SSRS](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)|  
|Überprüfen der Standardwerte für Datasetparameter.|Öffnen im Berichts-Generator oder Verwenden von URL-Zugriffssyntax.|Beispiel:<br /><br /> `https://localhost/reportserver/?/Datasets/Dataset1&rs:command=GetShareddatasetDefinition`
|Aktivieren der Zwischenspeicherung|Webportal|[Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](../../reporting-services/report-server/cache-shared-datasets-ssrs.md)|  
|Erstellen oder Bearbeiten eines Cacheaktualisierungsplans|Webportal|[Cache a Shared Dataset (Zwischenspeichern eines freigegebenen Datasets)](../../reporting-services/report-server/cache-a-shared-dataset.md)|  
|Synchronisieren der Definition eines freigegebenen Datasets zwischen dem Berichtsserver und der SharePoint-Website im integrierten SharePoint-Modus|SharePoint-Anwendungsseiten|Ändern der Eigenschaften freigegebener Datasetelemente<br /><br /> Ändern von Cacheoptionen<br /><br /> Ändern der freigegebenen Datenquelle|  
  
## <a name="comparing-shared-datasets-with-other-report-server-items"></a>Vergleichen von freigegebenen Datasets und anderen Berichtsserverelementen  
 Wenn Sie mehrere Elementtypen auf einem Berichtsserver verwalten, ist es hilfreich, zu verstehen, in welcher Weise sich Elemente ähneln und wie sie sich von anderen Berichtsserverelementen unterscheiden.  
  
 Freigegebene Datasets und freigegebene Datenquellen und Berichte sind in folgenden Punkten vergleichbar:  
  
-   Genauso wie freigegebene Datenquellen werden freigegebene Datasets unabhängig von den Berichten verwaltet, in denen sie verwendet werden. Ein Aspekt bei der Verwaltung eines freigegebenen Datasets auf einem Berichtsserver ist die Fähigkeit, die freigegebene Datenquelle, von der das Dataset abhängig ist, zu ändern, ohne die Definition des freigegebenen Datasets zu bearbeiten.  
  
-   Freigegebene Datasets können wie Berichte zwischengespeichert werden. Die für die Datenquelle erforderlichen Anmeldeinformationen müssen den Einschränkungen für das Zwischenspeichern entsprechen, und für jeden Parameter müssen Standardwerte angegeben werden. Weitere Informationen finden Sie unter [Zwischenspeichern von freigegebenen Datasets (SSRS)](../../reporting-services/report-server/cache-shared-datasets-ssrs.md).  
  
-   Bei jeder Verarbeitung wird die aktuelle Definition des Elements auf dem Berichtsserver verwendet, was auch auf Berichte zutrifft. Wenn Sie Änderungen an einem freigegebenen Dataset vornehmen, wird für jeden Bericht, der das Dataset verwendet, bei der Berichtsverarbeitung die aktuelle Definition auf dem Berichtsserver verwendet. Wenn die Zwischenspeicherung für das freigegebene Dataset aktiviert ist und Sie Änderungen an der Definition des freigegebenen Datasets vornehmen, werden die Änderungen erst verwendet, nachdem die Daten im Cache nicht mehr gültig sind. Sie können Cacheaktualisierungspläne verwenden, um konsistente Daten für mehrere Berichte bereitzustellen.  
  
 Freigegebene Datasets unterscheiden sich in folgendem Punkt von veröffentlichten Berichtsteilen:  
  
-   Im Gegensatz zu veröffentlichten Berichtsteilen lösen Änderungen an der Definition eines freigegebenen Datasets auf einem Berichtsserver keine Updatebenachrichtigungen aus, wenn der Bericht in einem Berichterstellungsclient geöffnet wird. Wenn Sie den Bericht ausführen, werden die Daten aus der aktuellen Definition des freigegebenen Datasets auf dem Berichtsserver verwendet.  
  
 Freigegebene Datasets sind in folgenden Punkten mit Abonnements vergleichbar:  
  
-   Freigegebene Datasets können elementspezifische und freigegebene Zeitpläne zum Zwischenspeichern verwenden.  
  
-   Für freigegebene Datasets gelten die gleichen Regeln zum Angeben von Parameterwerten wie für Abonnements.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
