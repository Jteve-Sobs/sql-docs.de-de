---
title: Objektanzahl angeben (Verwendungsbasierte Optimierung-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e0503192c3c948110f8301c8eb375e1c8203e42f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068235"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>Objektanzahl angeben (Assistent für verwendungsbasierte Optimierung)
  Auf der Seite **Objektanzahl angeben** können Sie die Anzahl der Objekte im Cube automatisch berechnen lassen oder die geschätzte Anzahl manuell eingeben. Der Assistent für verwendungsbasierte Optimierung schätzt die Speicheranforderungen anhand der Objektanzahlen.  
  
## <a name="options"></a>Optionen  
 **Cubeobjekte**  
 Zeigt die Dimensionen und Attribute im Cube an. Nur die Attribute, die nicht ihre `AggregationUsage` -Eigenschaft festgelegt auf "None" in der **Aggregationsverwendung überprüfen** Seite des Assistenten werden angezeigt, da sind die einzigen Attribute, die Anzahl angegeben.  
  
 **Geschätzte Anzahl**  
 Zeigt die geschätzte Anzahl der Zeilen in der Measuregruppe sowie die geschätzte Anzahl der Attributelemente in den Datenbankdimensionen an. Sie können einen Wert eingeben, der als geschätzte Anzahl verwendet werden soll, oder die Werte für die geschätzte Anzahl berechnen. Geben Sie 0 in das Feld ein, und klicken Sie dann auf **Anzahl**, um die Anzahlwerte zu berechnen. Felder, in denen bereits eine Anzahl angezeigt wird, werden nicht aktualisiert.  
  
 **Anzahl von Partitionen**  
 (Optional) Geben Sie die geschätzte Anzahl der Zeilen in der Measuregruppe sowie die geschätzte Anzahl der Attributelemente in den Partitionen ein.  
  
 **Count**  
 Berechnet und füllt für alle leeren Felder die Werte in der Spalte **Geschätzte Anzahl** neu. Felder, in denen bereits eine Anzahl angezeigt wird, werden nicht aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregation Design-Assistent F1-Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services-Assistenten &#40;mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
