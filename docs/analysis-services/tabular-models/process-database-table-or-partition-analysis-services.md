---
title: Verarbeiten von Datenbank, Tabelle oder Partition (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3fbaa230d4db635b5c3f6c232fa50ae0cf88aec1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207524"
---
# <a name="process-database-table-or-partition-analysis-services"></a>Verarbeiten von Datenbank, Tabelle oder Partition (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Die Aufgaben in diesem Thema wird beschrieben, wie tabellarische modelldatenbanken, Tabellen oder Partitionen mithilfe von manuell verarbeitet die **Prozess \<Objekt >** im Dialogfeld [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Weitere Informationen zur Verarbeitung von tabellarischen Modellen finden Sie unter [Verarbeitungsdaten](../../analysis-services/tabular-models/process-data-ssas-tabular.md).  
  
##  <a name="bkmk_process_tasks"></a> Aufgaben  
  
###  <a name="bkmk_process_db"></a> So verarbeiten Sie eine Datenbank  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf die Datenbank, die Sie verarbeiten möchten, und klicken Sie anschließend auf **Datenbank verarbeiten**.  
  
2.  Wählen Sie im Dialogfeld **Datenbank verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Modus|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus von Datenbankobjekten und führt die Verarbeitung durch, mit der nicht verarbeitete oder teilweise verarbeitete Objekte in den vollständig verarbeiteten Status versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet eine Datenbank und alle in ihr enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde. Diese Option erfordert die meisten Ressourcen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus Datenbankobjekten.|  
    |**Neuberechnung verarbeiten**|Aktualisiert und berechnet Hierarchien, Beziehungen und berechnete Spalten neu.|  
  
3.  Wählen Sie in der Spalte der Kontrollkästchen unter **Verarbeiten** die Partitionen aus, die im ausgewählten Modus verarbeitet werden sollen, und klicken Sie dann auf **OK**.  
  
###  <a name="bkmk_process_table"></a> So verarbeiten Sie eine Tabelle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in der tabellarischen Modelldatenbank, die die zu verarbeitende Tabelle enthält, den Knoten **Tabellen** , klicken Sie mit der rechten Maustaste auf die zu verarbeitende Tabelle, und klicken Sie anschließend auf **Tabelle verarbeiten**.  
  
2.  Wählen Sie im Dialogfeld **Tabelle verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Modus|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Tabellenobjekts und führt die Verarbeitung durch, die nicht verarbeitete oder teilweise verarbeitete Objekte in den Status Vollständig verarbeitet bringt. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet ein Tabellenobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde. Diese Option erfordert die meisten Ressourcen.|  
    |**Daten verarbeiten**|Lädt Daten in eine Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Tabelle und vorhandenen Tabellenpartitionen.|  
    |**Defragmentierung verarbeiten**|Defragmentiert die Indizes der Erweiterungstabellen.|  
  
3.  Überprüfen Sie in der Spalte der Kontrollkästchen die Tabelle und wählen Sie optional zusätzlich zu verarbeitende Tabellen aus, und klicken Sie dann auf **OK**.  
  
###  <a name="bkmk_process_partition"></a> So verarbeiten Sie eine oder mehrere Partitionen  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf die Tabelle, die die zu verarbeitenden Partitionen enthält, und klicken Sie anschließend auf **Partitionen**.  
  
2.  Klicken Sie im Dialogfeld **Partitionen** unter den Partitionen auf die Schaltfläche **Verarbeiten**.  
  
3.  Wählen Sie im Dialogfeld **Partition verarbeiten** im Listenfeld **Modus** einen der folgenden Verarbeitungsmodi aus:  
  
    |Modus|Beschreibung|  
    |----------|-----------------|  
    |**Standard verarbeiten**|Erkennt den Verarbeitungsstatus eines Partitionsobjekts und führt die Verarbeitung durch, durch die nicht oder teilweise verarbeitete Partitionsobjekte in den Status "Vollständig verarbeitet" versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt (neu berechnet).|  
    |**Vollständig verarbeiten**|Verarbeitet ein Partitionsobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde.|  
    |**Verarbeiten von Daten**|Lädt Daten in eine Partition oder Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
    |**Löschung verarbeiten**|Entfernt alle Daten aus einer Partition.|  
    |**Hinzufügung verarbeiten**|Aktualisiert die Partition inkrementell mit neuen Daten.|  
  
4.  Wählen Sie in der Spalte der Kontrollkästchen unter **Verarbeiten** die Partitionen aus, die im ausgewählten Modus verarbeitet werden sollen, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenmodellpartitionen](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Erstellen und Verwalten von Tabellenmodellpartitionen](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
