---
title: Dialogfeld "Vorlage" (Analysis Services – mehrdimensionale Daten) zur ebenenbenennung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37afa05887059607edc257c3957495a8db335d3c
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144768"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Vorlage zur Ebenenbenennung' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Vorlage zur Ebenenbenennung** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie eine Vorlage zur Ebenenbenennung für ein übergeordnetes Attribut in einer Dimension erstellen. Weitere Informationen über Vorlagen zur Ebenenbenennung finden Sie unter [NamingTemplate Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Sie können anzeigen, die **Vorlage zur Ebenenbenennung** Dialogfeld durch Klicken auf die Schaltfläche mit den Auslassungspunkten (**...** ) auf die `NamingTemplate` -Wert einer Übersetzung für ein Attribut in der **Übersetzungsdetails** im Bereich der **Übersetzungen** Registerkarte **Dimensions-Designer**.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Ebenenvorlage definieren**|Zeigt ein Raster an, in dem Sie die Hierarchie der Ebenen in dem übergeordneten Attribut gestalten können. Das Raster enthält die folgenden Spalten:<br /><br /> **Ebene**: Zeigt die Ordnungsposition der Ebene für die der Name, in angegeben **Namen** verwendet wird. Wählen Sie die Option **Name** in der Zeile aus, die ein Sternchen (\*) unter **Ebene**enthält, um eine neue Vorlage für die Benennung einer Ebene hinzuzufügen.<br /><br /> **Namen**: enthält die Vorlage zur Benennung der Ebene, die **Ebene**. Als Platzhalter für die Ordnungsposition der Ebene in der Vorlage zur Benennung fügen Sie ein einzelnes Sternchen (*) hinzu. Um ein Sternchen als Teil des Namens, der von der benennungsvorlage erstellt hinzuzufügen, fügen Sie zwei Sternchen (\*\*).|  
|**Auswahl aufheben**|Entfernt alle Zeilen unter **Ebenenvorlage definieren**.|  
|**Ergebnis**|Zeigt die im Dialogfeld erstellte Vorlage zur Ebenenbenennung an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
