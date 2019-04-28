---
title: Transformations-Editor (Spaltenseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 63410531bcb0af8a254b2d2a5c6c650423cb9a1b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890516"
---
# <a name="lookup-transformation-editor-columns-page"></a>Transformations-Editor für Suche (Seite 'Spalten')
  Auf der Seite **Spalten** des Dialogfelds **Transformations-Editor für Suche** können Sie den Join zwischen der Quell- und der Verweistabelle angeben sowie Suchspalten aus der Verweistabelle auswählen.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Verfügbare Eingabespalten**  
 Zeigt die Liste der verfügbaren Eingabespalten an. Die Eingabespalten sind die Spalten im Datenfluss aus einer verbundenen Quelle. Die Datentypen der Eingabe- und Suchspalte müssen übereinstimmen.  
  
 Mithilfe eines Drag-und-Drop-Vorgangs können Sie verfügbare Eingabespalten bestimmten Suchspalten zuordnen.  
  
 Sie können auch mithilfe der Tastatur Eingabespalten bestimmten Suchspalten zuordnen. Dazu heben Sie eine Spalte in der Tabelle **Verfügbare Eingabespalten** hervor, drücken die Anwendungstaste und klicken dann auf **Zuordnungen bearbeiten**.  
  
 **Verfügbare Suchspalten**  
 Zeigt die Liste der Suchspalten an. Die Suchspalten sind Spalten in der Verweistabelle, in denen nach Werten gesucht werden soll, die mit den Eingabespalten übereinstimmen.  
  
 Mithilfe eines Drag-und-Drop-Vorgangs können Sie verfügbare Suchspalten bestimmten Eingabespalten zuordnen.  
  
 Wählen Sie mithilfe der Kontrollkästchen die Suchspalten in der Verweistabelle aus, für die die Suchvorgänge ausgeführt werden sollen.  
  
 Sie können auch mithilfe der Tastatur Suchspalten bestimmten Eingabespalten zuordnen. Dazu heben Sie eine Spalte in der Tabelle **Verfügbare Suchspalten** hervor, drücken die Anwendungstaste und klicken dann auf **Zuordnungen bearbeiten**.  
  
 **Suchspalte**  
 Zeigt die Liste der ausgewählten Suchspalten an. Die Auswahl wird entsprechend in der Auswahl der Kontrollkästchen in der Tabelle **Verfügbare Suchspalten** deutlich.  
  
 **Suchvorgang**  
 Wählen Sie in der Liste einen Suchvorgang aus, der für die Suchspalte ausgeführt werden soll.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für die Ausgabe der einzelnen Suchspalten ein. Standardmäßig wird der Name der Suchspalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Transformations-Editor für Suche &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Transformations-Editor für Suche &#40;Seite „Verbindung“&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Erweitert“&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Transformation für Fuzzysuche](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
