---
title: Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2c505bf78acc4293e68f0f2222dd9fbf7f9e01e2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62900136"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen)
  Mithilfe des Dialogfelds **Abgeleitete Dimensionselemente** können Sie Optionen für das Verwenden von abgeleiteten Elementen angeben. Abgeleitete Elemente sind vorhanden, wenn eine Faktentabelle auf noch nicht geladene Dimensionselemente verweist. Wenn für das abgeleitete Element Daten geladen sind, können Sie den vorhandenen Datensatz aktualisieren, aber keinen neuen erstellen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Unterstützung für abgeleitete Elemente aktivieren**  
 Wenn Sie abgeleitete Elemente aktivieren, müssen Sie eine der beiden folgenden Optionen auswählen.  
  
 **Alle Spalten mit einem Änderungstyp weisen den Wert NULL auf**  
 Gibt an, dass in allen Spalten des neuen Datensatzes des abgeleiteten Elements, die einen Änderungstyp aufweisen, NULL-Werte eingetragen werden.  
  
 **Mithilfe einer booleschen Spalte anzeigen, ob der aktuelle Datensatz ein abgeleitetes Element ist**  
 Gibt an, dass eine vorhandene boolesche Spalte verwendet wird, um anzuzeigen, dass der aktuelle Datensatz ein abgeleitetes Element ist.  
  
 **Indikator für abgeleitetes Element**  
 Wenn eine boolesche Spalte verwendet wird, um abgeleitete Elemente wie oben beschrieben anzuzeigen, wählen Sie die Spalte aus der Liste aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
