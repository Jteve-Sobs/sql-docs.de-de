---
title: Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cde312f2bfad67c6cfe61a9b8379973c1f59a56c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178517"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent verwendet die JSON-Ausgabedateien aus generiert eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt als Eingabedateien. Diese Eingabedateien können problemlos geändert werden, um die Bereitstellung eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts anzupassen. Anschließend kann das generierte Bereitstellungsskript entweder sofort ausgeführt oder für eine spätere Bereitstellung gespeichert werden.  

> [!NOTE]
> Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistenten/Bereitstellungshilfsprogramm wird mit installiert [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) (SSMS). Achten Sie darauf, dass Sie die neueste Version verwenden. Wenn von der Eingabeaufforderung ausgeführt wird, wird standardmäßig ist die neueste Version des Assistenten zum Bereitstellen der C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio installiert. 
  
 Sie können die Bereitstellung mithilfe des Assistenten wie hier beschrieben durchführen. Sie können die Bereitstellung auch automatisieren oder die Synchronisierungsfunktion verwenden. Wenn die bereitgestellte Datenbank groß ist, sollten Sie die Verwendung von Partitionen auf den Zielsystemen in Erwägung ziehen. Sie können die partitionserstellung und-Auffüllung automatisieren, mit der Tabular Object Model (TOM) Tabular Model Scriting Language (TMSL) und Analysis Management Objects (AMO).  
  
> [!IMPORTANT]  
>  Weder die Ausgabedateien noch das Bereitstellungsskript wird der Benutzer-Id oder das Kennwort enthalten, wenn diese in der Verbindungszeichenfolge für eine Datenquelle oder für Identitätswechsel angegeben sind. Da diese Informationen zum Verarbeiten in diesem Szenario erforderlich sind, müssen Sie sie manuell hinzufügen. Wenn die Bereitstellung keine Verarbeitung umfasst, können Sie die Verbindungs- und Identitätswechselinformationen bei Bedarf nach der Bereitstellung hinzufügen. Wenn die Bereitstellung die Verarbeitung umfasst, können Sie diese Informationen nach dem Speichern entweder innerhalb des Assistenten oder im Bereitstellungsskript hinzufügen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen wird beschrieben, wie Sie mit dem Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , den Eingabedateien und dem Bereitstellungsskript arbeiten:  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Ausführen des Bereitstellungs-Assistenten für Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Beschreibt die verschiedenen Möglichkeiten zum Ausführen des Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|Beschreibt, welche Dateien der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] als Eingabewerte verwendet und was jede dieser Dateien enthält. Stellt außerdem Links zu Themen bereit, in denen beschrieben wird, wie Sie die Werte in den einzelnen Eingabedateien ändern können.|  
|[Grundlegendes zum Analysis Services-Bereitstellungsskript](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Beschreibt den Inhalt des Bereitstellungsskripts und wie das Skript ausgeführt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Modelllösungen mit XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Synchronisieren von Analysis Services-Datenbanken](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
