---
title: Transformation für Zeilenanzahl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 53f14b78dcf3c8f0ee986b8ef0fde14b58254f07
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784972"
---
# <a name="row-count-transformation"></a>Transformation für Zeilenanzahl
  Die Transformation für Zeilenanzahl zählt die Zeilen in einem Datenfluss und speichert die endgültige Anzahl in einer Variablen.  
  
 A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Paket können mithilfe der Zeilenanzahl die in Skripts, Ausdrücken und Eigenschaftsausdrücken verwendeten Variablen aktualisiert werden. (Beispielsweise kann mit der Variablen, die die Zeilenanzahl speichert, der Nachrichtentext in einer E-Mail-Nachricht aktualisiert und um die Zeilenanzahl ergänzt werden.) Die von der Transformation für Zeilenanzahl verwendete Variable muss bereits vorhanden sein, und zwar im Bereich des Datenflusstasks, zu dem der Datenfluss mit der Transformation für Zeilenanzahl gehört.  
  
 Die Transformation speichert den Zeilenanzahlwert erst dann in der Variablen, nachdem die letzte Zeile die Transformation durchlaufen hat. Daher wird der Wert der Variablen nicht rechtzeitig aktualisiert, um den aktualisierten Wert im Datenfluss zu verwenden, der die Transformation für die Zeilenanzahl enthält. Sie können die aktualisierte Variable in einem separaten Datenfluss verwenden.  
  
 Diese Transformation weist je eine Eingabe und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Konfiguration der Transformation für Zeilenanzahl  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften dieser Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services-ssis-variables.md)   
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
