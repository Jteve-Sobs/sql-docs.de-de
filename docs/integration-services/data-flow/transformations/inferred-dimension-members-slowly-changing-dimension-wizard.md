---
title: Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumente
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c5354a97ac3f0e535f11256de5e0643bf4243255
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944245"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen)

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mithilfe des Dialogfelds **Abgeleitete Dimensionselemente** können Sie Optionen für das Verwenden von abgeleiteten Elementen angeben. Abgeleitete Elemente sind vorhanden, wenn eine Faktentabelle auf noch nicht geladene Dimensionselemente verweist. Wenn für das abgeleitete Element Daten geladen sind, können Sie den vorhandenen Datensatz aktualisieren, aber keinen neuen erstellen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>enthalten  
 **Unterstützung für abgeleitete Elemente aktivieren**  
 Wenn Sie abgeleitete Elemente aktivieren, müssen Sie eine der beiden folgenden Optionen auswählen.  
  
 **Alle Spalten mit einem Änderungstyp weisen den Wert NULL auf**  
 Gibt an, dass in allen Spalten des neuen Datensatzes des abgeleiteten Elements, die einen Änderungstyp aufweisen, NULL-Werte eingetragen werden.  
  
 **Mithilfe einer booleschen Spalte anzeigen, ob der aktuelle Datensatz ein abgeleitetes Element ist**  
 Gibt an, dass eine vorhandene boolesche Spalte verwendet wird, um anzuzeigen, dass der aktuelle Datensatz ein abgeleitetes Element ist.  
  
 **Indikator für abgeleitetes Element**  
 Wenn eine boolesche Spalte verwendet wird, um abgeleitete Elemente wie oben beschrieben anzuzeigen, wählen Sie die Spalte aus der Liste aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
