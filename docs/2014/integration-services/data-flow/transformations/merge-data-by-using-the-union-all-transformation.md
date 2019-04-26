---
title: Zusammenführen von Daten mithilfe der Transformation für UNION ALL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f5504c6f58d7ff5254d081ea479ca30ed6ca705
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770339"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a>Zusammenführen von Daten mithilfe der Transformation für UNION ALL
  Das Paket muss bereits mindestens einen Datenflusstask und zwei Datenquellen enthalten, damit Sie eine Transformation für UNION ALL hinzufügen und konfigurieren können.  
  
 Die Transformation für UNION ALL kombiniert mehrere Eingaben. Die erste Eingabe, die mit der Transformation verbunden wird, ist die Verweiseingabe, und die nachfolgend verbundenen Eingaben sind die sekundären Eingaben. Die Ausgabe enthält die Spalten in der Verweiseingabe.  
  
### <a name="to-combine-inputs-in-a-data-flow"></a>So kombinieren Sie Eingaben in einem Datenfluss  
  
1.  Doppelklicken Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]im Projektmappen-Explorer auf das Paket, um es im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu öffnen, und klicken Sie dann auf die Registerkarte **Datenfluss** .  
  
2.  Ziehen Sie aus **Toolbox**die Transformation für UNION ALL auf die Entwurfsoberfläche der Registerkarte **Datenfluss** .  
  
3.  Verbinden Sie die Transformation für UNION ALL mit dem Datenfluss, indem Sie einen Konnektor von der Datenquelle oder einer vorherigen Transformation auf die Transformation für UNION ALL ziehen.  
  
4.  Doppelklicken Sie auf die Transformation für UNION ALL.  
  
5.  Ordnen Sie im **Transformations-Editor für UNION ALL**eine Spalte aus einer Eingabe einer Spalte in der Liste **Name der Ausgabespalte** zu. Klicken Sie dazu auf eine Zeile, und wählen Sie dann eine Spalte in der Eingabeliste aus. Wählen Sie in der Eingabeliste **\<ignorieren>** aus, um das Zuordnen der Spalte zu überspringen.  
  
    > [!NOTE]  
    >  Für die Zuordnung von zwei Spalten müssen die Metadaten der Spalten übereinstimmen.  
  
    > [!NOTE]  
    >  Für Spalten in einer sekundären Eingabe, die keinen Verweisspalten zugeordnet sind, werden in der Ausgabe NULL-Werte festgelegt.  
  
6.  Ändern Sie optional die Namen von Spalten in der **Name der Ausgabespalte** -Spalte.  
  
7.  Wiederholen Sie die Schritte 5 und 6 für jede Spalte in jeder Eingabe.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Union All Transformation](union-all-transformation.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [Datenflusstask](../../control-flow/data-flow-task.md)  
  
  
