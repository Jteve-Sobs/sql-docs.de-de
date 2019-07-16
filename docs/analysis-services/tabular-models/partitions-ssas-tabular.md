---
title: Partitionen in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d26b1b1558ca546fb47660488b15dc777c5ad87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162719"
---
# <a name="partitions"></a>Partitionen
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Durch Partitionen wird eine Tabelle logisch unterteilt. Jede Partition kann unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden. Mit dem Dialogfeld "Partitionen" in SSDT während der Modellerstellung erstellte Partitionen gelten für die arbeitsbereichsdatenbank des Modells. Beim Bereitstellen des Modells werden die für die Arbeitsbereichsdatenbank des Modells definierten Partitionen in der bereitgestellten Modelldatenbank dupliziert. Sie können weitere erstellen und Verwalten von Partitionen für eine bereitgestellte Modelldatenbank in SSMS im Dialogfeld Partitionen mit.  In diesem Thema werden Partitionen beschrieben erstellt haben, während der Modellerstellung mithilfe des Dialogfelds Partitions-Manager, klicken Sie in SSDT. Informationen zum Erstellen und Verwalten von Partitionen für ein bereitgestelltes Modell finden Sie unter [erstellen und Verwalten von Tabellenmodellpartitionen](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_benefits"></a> Vorteile  
 Durch Partitionen in tabellarischen Modellen werden Tabellen in logische Partitionsobjekte unterteilt. Anschließend kann jede Partition unabhängig von anderen Partitionen verarbeitet werden. Eine Tabelle kann z. B. bestimmte Rowsets mit Daten enthalten, die selten geändert werden, während andere Rowsets Daten enthalten, die häufig geändert werden. In diesen Fällen ist es nicht erforderlich, sämtliche Daten zu verarbeiten, wenn tatsächlich nur ein Teil der Daten verarbeitet werden soll. Mit Partitionen können Daten, die häufig verarbeitet werden müssen, und Daten, die weniger häufig verarbeitet werden müssen, voneinander getrennt werden.  
  
 Bei einem effizienten Modellentwurf werden Partitionen genutzt, um unnötige Verarbeitungsschritte und die daraus resultierende Belastung der Analysis Services-Serverprozessoren zu eliminieren und gleichzeitig sicherzustellen, dass bestimmte Daten so häufig verarbeitet und aktualisiert werden, dass immer die neuesten Daten aus den Datenquellen bereitgestellt werden. Die Implementierung und Verwendung von Partitionen während der Modellerstellung kann sich erheblich von der Implementierung und Verwendung von Partitionen für bereitgestellte Modelle unterscheiden. Sie sollten bedenken, dass Sie während der Modellerstellungsphase möglicherweise nur mit einem Bruchteil der Daten arbeiten, die letztendlich im bereitgestellten Modell enthalten sind.  
  
### <a name="processing-partitions"></a>Verarbeitung von Partitionen  
 Wird der bereitgestellte Modelle mithilfe von SSMS oder durch Ausführen eines Skripts die enthält den Verarbeitungsbefehl sowie Verarbeitungsoptionen und-Einstellungen verarbeitet. Beim Erstellen von Modellen mithilfe von SSDT können Sie Verarbeitungsvorgänge mithilfe des Befehls verarbeiten das Menü "Modell" oder die Symbolleiste ausführen. Ein Verarbeitungsvorgang kann für eine Partition, eine Tabelle oder beides angegeben werden.  
  
 Beim Ausführen eines Verarbeitungsvorgangs wird unter Verwendung der Datenverbindung eine Verbindung mit der Datenquelle hergestellt. In die Modelltabellen werden neue Daten importiert, es werden Beziehungen und Hierarchien für die einzelnen Tabellen neu erstellt, und Berechnungen in berechneten Spalten und Measures werden neu berechnet.  
  
 Indem Sie eine Tabelle weiter in logische Partitionen unterteilen, können Sie selektiv bestimmen, welche Daten in den einzelnen Partitionen, wann und wie verarbeitet werden. Wenn Sie ein Modell bereitstellen, Verarbeitung der Partitionen kann abgeschlossen werden, manuell mithilfe des Dialogfelds "Partitionen" in SSMS oder mithilfe eines Skripts, das einen Verarbeitungsbefehl ausführt.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Partitionen in der Arbeitsbereichsdatenbank des Modells  
 Sie können neue Partitionen erstellen, bearbeiten, Zusammenführen oder Löschen von Partitionen, die mit dem Partitions-Manager in SSDT. Abhängig von der Kompatibilitätsgrad des Modells, die Sie erstellen werden, werden die Partitions-Manager zwei Modi für die Auswahl von Tabellen, Zeilen und Spalten für eine Partition: Für tabellarische Modelle mit Kompatibilitätsgrad 1400 Partitionen werden mit einer M-Abfrage definiert, oder können Sie im Entwurfsmodus des um Abfrage-Editor zu öffnen. Für tabellarisches 1100 verwenden 1103, 1200-Modelle, Sie den Tabellenvorschaumodus und SQL-Abfragemodus. 
  
### <a name="partitions-in-a-deployed-model-database"></a>Partitionen in der Datenbank eines bereitgestellten Modells  
 Wenn Sie ein Modell bereitstellen, werden die Partitionen für die bereitgestellte Modelldatenbank als Datenbankobjekte in SSMS angezeigt. Sie können zu erstellen, bearbeiten, Zusammenführen und Löschen von Partitionen für ein bereitgestelltes Modell mit dem Dialogfeld "Partitionen" in SSMS. Verwalten von Partitionen für ein bereitgestelltes Modell in SSMS ist außerhalb des Bereichs der in diesem Thema. Informationen zum Verwalten von Partitionen in SSMS finden Sie unter [erstellen und Verwalten von Tabellenmodellpartitionen](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen und Verwalten von Partitionen in der Arbeitsbereichsdatenbank](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|Beschreibt das Erstellen und Verwalten von Partitionen in der arbeitsbereichsdatenbank des Modells mit der Partitions-Manager in SSDT.|  
|[Verarbeiten von Partitionen in der Arbeitsbereichsdatenbank](../../analysis-services/tabular-models/process-partitions-in-the-workspace-database-ssas-tabular.md)|Beschreibt, wie Partitionen in der Arbeitsbereichsdatenbank des Modells verarbeitet (aktualisiert) werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Verarbeiten von Daten](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
