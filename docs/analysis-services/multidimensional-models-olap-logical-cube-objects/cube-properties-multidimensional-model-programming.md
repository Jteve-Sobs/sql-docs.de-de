---
title: Cubeeigenschaften – mehrdimensionale Modellprogrammierung | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85453133ab9facd9f3ed56ad98fa2761ac527e40
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209370"
---
# <a name="cube-properties---multidimensional-model-programming"></a>Cubeeigenschaften – Mehrdimensionale Modellprogrammierung
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Cubes verfügen über eine Reihe von Eigenschaften, die Sie festlegen können und die sich auf das cubeweite Verhalten auswirken. Diese Eigenschaften sind in der folgenden Tabelle zusammengefasst.  
  
> [!NOTE]  
>  Manche Eigenschaften werden beim Erstellen des Cubes automatisch festgelegt und können nicht geändert werden.  
  
 Weitere Informationen über das Festlegen von Cubeeigenschaften finden Sie unter [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**AggregationPrefix**|Gibt das für Aggregationsnamen verwendete gemeinsame Präfix an.|  
|**Sortierung**|Gibt den Gebietsschemabezeichner (LCID) und das Vergleichsflag, durch einen Unterstrich voneinander getrennt, an, wie z. B. Latin1_General_C1_AS.|  
|**DefaultMeasure**|Enthält einen mehrdimensionalen Ausdruck (Multidimensional Expression, MDX), der das Standardmeasure für den Cube definiert.|  
|**Beschreibung**|Stellt eine Beschreibung des Cubes bereit, die in Clientanwendungen verwendet werden kann.|  
|**ErrorConfiguration**|Enthält konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|**EstimatedRows**|Gibt die Anzahl der geschätzten Zeilen im Cube an.|  
|**ID**|Enthält den eindeutigen Bezeichner (ID) des Cubes.|  
|**Sprache**|Gibt den Standardsprachbezeichner für den Cube an.|  
|**Name**|Gibt den benutzerfreundlichen Namen des Attributs an.|  
|**ProactiveCaching**|Definiert die Einstellungen für den Cube für die proaktive Zwischenspeicherung.|  
|**ProcessingMode**|Gibt an, ob während oder nach der Verarbeitung indiziert und aggregiert werden soll. Optionen sind **regulären** oder **lazy**.|  
|**ProcessingPriority**|Legt die Verarbeitungspriorität des Cubes bei Hintergrundvorgängen wie z. B. verzögerte Aggregationen und Indizierungen fest. Der Standardwert ist **0**.|  
|**ScriptCacheProcessingMode**|Gibt an, ob der Skriptcache während oder nach der Verarbeitung erstellt werden soll. Optionen sind **regulären** und **lazy**.|  
|**ScriptErrorHandlingMode**|Bestimmt die Fehlerbehandlung. Optionen sind **' ignorenone '** oder **' ignoreall '**|  
|**Quelle**|Zeigt die für den Cube verwendete Datenquellensicht.|  
|**StorageLocation**|Gibt den Speicherort des Dateisystems für den Cube an. Wenn kein Speicherort angegeben ist, wird er von der Datenbank geerbt, die das Cubeobjekt enthält.|  
|**StorageMode**|Gibt den Speichermodus für den Cube an. Werte sind **MOLAP**, **ROLAP**, oder **HOLAP**.|  
|**Visible**|Bestimmt die Sichtbarkeit des Cubes.|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die ErrorConfiguration-Eigenschaft, bei der Arbeit mit null-Werte und andere Probleme mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Siehe auch  
 [Proaktives Zwischenspeichern &#40;Partitionen&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
