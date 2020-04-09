---
title: Behandlung von Problemen in Reporting Services
description: In diesem Artikel erfahren Sie, wie Sie Probleme beim Berichtsentwurf diagnostizieren und beheben, die beim Erstellen des Berichtslayouts in der Designansicht in einer Berichtserstellungsanwendung auftreten können.
ms.date: 02/27/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
ms.assetid: a0d103da-5a3e-475c-a71a-9e23476095e2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: dd38603a00c01187c131c2f515c2a4c6c1cb858e
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662813"
---
# <a name="troubleshoot-report-design-issues-with-reporting-services"></a>Behandlung von Problemen in Reporting Services
Probleme bei der Berichtserstellung können auftreten, wenn Sie das Berichtslayout in der Entwurfsansicht in einer Berichterstellungsanwendung erstellen. Dieses Thema soll Ihnen beim Behandeln der folgenden Probleme helfen.   
  
## <a name="why-does-my-text-box-show-only-a-single-value-and-not-repeat-for-every-row"></a>Warum wird in einem Textfeld nur ein einzelner Wert angezeigt und nicht in jeder Zeile wiederholt?  
Ein Textfeld mit einem Verweis auf ein Datasetfeld wird nur einmal gerendert und zeigt den ersten Wert im Dataset an.   
  
**Übergeordnetes Element des Textfelds ist der Hauptteil des Berichts**  
  
  
In einem Textfeld, das der Entwurfsoberfläche direkt hinzugefügt wird, kann nur ein Aggregatwert für ein Dataset angezeigt werden.  
  
Wenn Sie den übergeordneten Container eines Textfelds überprüfen möchten, wählen Sie das Textfeld aus, und führen Sie im Eigenschaftenbereich einen Bildlauf zu **Übergeordnet**aus.   
  
Wenn Sie Textfelder benötigen, in denen jeder Wert in einem Dataset angezeigt wird, verwenden Sie einen Datumsbereich, z. B. eine Tabelle oder eine Matrix. Jede Zelle in einer Tabelle oder Matrix enthält standardmäßig ein Textfeld. Ziehen Sie Datasetfelder in jede Zelle.   
  
## <a name="why-cant-i-add-total-pages-to-my-report"></a>Warum kann ich meinem Bericht keine Gesamtseitenanzahl hinzufügen?  
Die integrierten Felder `[&PageNumber]` und `[&TotalPages]` sind im Hauptteil des Berichts nicht gültig.   
  
PageNumber und TotalPages sind nur im Seitenkopf und Seitenfuß gültig.  
  
  
Die integrierten Felder [&PageNumber] und [&TotalPages] sind nur im Seitenkopf und Seitenfuß gültig.   
  
Wenn Sie [&PageNumber] oder [&TotalPages] in einem Bericht hinzufügen möchten, müssen Sie zuerst einen Seitenkopf oder einen Seitenfuß hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen eines Seitenkopfs](../../reporting-services/report-design/add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md).  
  
> [!NOTE]  
> Das Einschließen von [&TotalPages] im Seitenkopf oder Seitenfuß kann Auswirkungen auf die Verarbeitung des Berichts haben. Weitere Informationen finden Sie im Artikel zur Problembehandlung bei Berichten: In ein bestimmtes Dateiformat exportierte Berichte.  
[Problembehandlung bei der Verarbeitung von Reporting Services-Berichten](../../reporting-services/troubleshooting/troubleshoot-processing-of-reporting-services-reports.md).  
  
## <a name="how-do-i-design-two-tables-or-a-chart-and-a-table-to-display-side-by-side"></a>Wie entwerfe ich zwei Tabellen oder ein Diagramm und eine Tabelle so, dass sie nebeneinander angezeigt werden?  
Das Entwerfen eines Berichts erfolgt nicht in einer WYSIWYG-Umgebung. Der Berichtsprozessor kombiniert Daten, Berichtselemente, Informationen zum Berichtslayout (z. B. Leerraum), Container und Ausdrücke, um einen kompilierten Bericht zu erstellen, der dann an einen Berichtsrenderer übergeben wird. Dieser bestimmt das Layout des Berichts für die angegebene Anzeigeumgebung: interaktiv für einen HTML-Browser oder als Dateiformat. Mit den automatischen Layoutalgorithmen wird möglicherweise ein Bericht erzeugt, den Sie ändern möchten.   
  
### <a name="rendering-rules-use-page-size-containers-peer-objects-relative-placement-and-white-space-to-determine-layout"></a>Renderingregeln bestimmen das Layout mithilfe von Seitengröße, Containern, Peerobjekten, relativer Platzierung und Leerraum  
Im Allgemeinen wird ein Bericht größer, um die Daten aufzunehmen. Dabei werden andere Berichtselemente zur Seite gedrängt.   
  
Wenn mehrere Datenbereiche oder Berichtselemente gemeinsam gruppiert werden sollen, platzieren Sie sie im gleichen übergeordneten Container. Platzieren Sie z. B. ein Diagramm und eine Tabelle in einem rechteckigen Container, und richten sie die oberen Ränder so aus, dass sie nebeneinander angezeigt werden. Weitere Informationen finden Sie unter [Renderingverhalten im Berichts-Generator](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Troubleshoot Data Retrieval issues with Reporting Services Reports (Problembehandlung: Probleme beim Abrufen von Daten in Reporting Services-Berichten)](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Troubleshoot Reporting Services Subscriptions and Delivery (Problembehandlung: Abonnements und Übermittlung in Reporting Services)](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

