---
title: Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10054250-d915-4bcb-8a1d-26837db4e932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80d59759befa0a6d7b601509a99c7cc6e22fbf0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66107755"
---
# <a name="print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs"></a>Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS)
  Ein Browser ist zwar die am häufigsten verwendete Clientanwendung zum Anzeigen von Berichten, die Druckfunktionen des Browsers sind jedoch für das Drucken von Berichten nicht ideal. Die Druckfunktionen eines Browsers sind zum Drucken von Webseiten konzipiert. In der Regel enthalten die von einem Browser gedruckten Seiten alle visuellen Elemente einer Webseite, dazu Kopf- und Fußzeileninformationen zur Identifikation der Seite oder Website. Beim Drucken über einen Browser wird der Inhalt des aktuellen Fensters gedruckt. Bei mehrseitigen Berichten wird maximal die erste Seite gedruckt, möglicherweise sogar weniger, wenn die Berichtsseite die Dimensionen der gedruckten Seite übersteigt.  
  
 Wenn Sie die Druckqualität der in einem Browser angezeigten Berichte verbessern und mehrere Seiten drucken möchten, können Sie die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]bereitgestellte clientseitige Druckfunktionalität verwenden. Die clientseitige Druckfunktion stellt ein Standarddialogfeld **Drucken** bereit, das zum Auswählen eines Druckers, Angeben von Seiten und Rändern sowie zum Anzeigen einer Vorschau des Berichts vor dem Drucken verwendet wird. Verwenden Sie die clientseitige Druckfunktion anstelle des Befehls **Drucken** im Menü **Datei** des Browsers. Beim Verwenden dieser Funktion wird der Bericht gemäß seines Entwurfs gedruckt, ohne zusätzliche Elemente, die im Ausdruck einer Webseite zu finden sind.  
  
 Für den clientseitigen Druck müssen Sie ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] -ActiveX-Steuerelement installieren. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="print-options"></a>Druckoptionen  
 Sie können Druckeigenschaften für Ihren Bericht konfigurieren, indem Sie im Dialogfeld **Drucken** auf die Schaltfläche **Eigenschaften** klicken. Der Wert für**Papierformat** wird durch die Standardhöhe und -breite der Berichtsseitengröße gemäß Berichtsdefinition bestimmt. Die verfügbaren Werte sind vom Druckertyp und seinen Funktionen abhängig. Für Breite und Höhe werden Standardwerte angezeigt, die durch die auf dem Computer konfigurierten Druckertreiber bestimmt werden. Nach dem Ändern dieser Werte wird der Bericht mit den neuen Abmessungen gedruckt. Die Seitenbreite und -höhe wird durch **Ausrichtung**bestimmt. Mögliche Werte sind **Hochformat** oder **Querformat**. Die angezeigte Standardausrichtung ist von der Seitenbreite und Seitenhöhe des Berichts abhängig.  
  
> [!NOTE]  
>  Das Dialogfeld **Drucken** und die Standarddruckereinstellungen für Breite, Höhe und Seitenausrichtung werden von der Berichtsdefinition bestimmt.  
  
### <a name="print-preview"></a>Seitenansicht  
 Sie können die Vorschau eines Berichts anzeigen, indem Sie im Dialogfeld **Drucken** auf die Schaltfläche **Vorschau** klicken. Durch Klicken auf Vorschau wird die erste Seite des Berichts in einem separaten Vorschaufenster geöffnet. Weitere Seiten werden beim Rendern des Berichts auf dem Berichtsserver verfügbar. Ein als Vorschau angezeigter Bericht wird im EMF-Format gerendert. Sie können zur vorherigen oder nächsten Seite navigieren, bis die letzte Seite erreicht ist. Dann ist die Schaltfläche **Weiter** deaktiviert.  
  
### <a name="adjusting-print-margins"></a>Anpassen der Druckränder  
 Sie können die Druckränder im gerenderten EMF-Bericht vor dem Drucken des Berichts ändern. Klicken Sie hierzu im Dialogfeld **Drucken** auf die Schaltfläche **Vorschau** . Klicken Sie oben auf der Vorschauseite auf die Schaltfläche **Ränder** . Das Dialogfeld Ränder wird angezeigt. Konfigurieren Sie bei Bedarf den oberen, unteren, rechten und linken Rand. [!INCLUDE[clickOK](../../includes/clickok-md.md)] Das Dialogfeld wird geschlossen, und die Einstellungen werden für die Renderingvorschau und den Druckvorgang gespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](print-reports-report-builder-and-ssrs.md)   
 [Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;](print-a-report-report-builder-and-ssrs.md)  
  
  
