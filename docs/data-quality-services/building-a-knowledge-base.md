---
title: Aufbau einer Wissensdatenbank
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 895dcfdd5acaa580b8ee719a3edac67d7308f605
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897555"
---
# <a name="building-a-knowledge-base"></a>Aufbau einer Wissensdatenbank

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Eine Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ist ein Repository des Wissens zu den Daten. Sie ermöglicht es Ihnen, die Daten zu verstehen und ihre Integrität aufrechtzuerhalten. Eine Wissensdatenbank besteht aus Domänen, die jeweils die Daten in einem Datenfeld darstellen. Die Wissensdatenbank wird von DQS zur Datenbereinigung und Deduplizierung in einer Datenbank verwendet. Um die Wissensdatenbank für die Datenbereinigung vorzubereiten, können Sie eine computergestützte Analyse eines Datenbeispiels ausführen und die Werte in den Domänen interaktiv verwalten. Mithilfe von DQS können Sie Wissen importieren, Regeln und Beziehungen erstellen, Datenwerte direkt ändern und eine Standarddatenbank verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Sie können die folgenden Vorgänge in der Wissensdatenbank ausführen:  
  
|||  
|-|-|  
|Sie können eine neue Wissensdatenbank von Grund auf, aus einer vorhandenen Wissensdatenbank oder aus einer DQS-Datendatei erstellen.|[Erstellen einer Wissensdatenbank](../data-quality-services/create-a-knowledge-base.md)|  
|Sie können eine vorhandene Wissensdatenbank öffnen, um die Wissensermittlung oder Domänenverwaltung durchzuführen oder eine Abgleichsrichtlinie hinzuzufügen.|[Öffnen einer Wissensdatenbank](../data-quality-services/open-a-knowledge-base.md)|  
|Sie können Verwaltungsaktionen in einer Wissensdatenbank durchführen, z. B. die Wissensdatenbank öffnen, entsperren, umbenennen oder löschen, vorgenommene Anpassungen verwerfen oder die Eigenschaften der Wissensdatenbank anzeigen.|[Verwalten einer Wissensdatenbank](../data-quality-services/manage-a-knowledge-base.md)|  
|Sie können Wissen zur Wissensdatenbank wie folgt hinzufügen: durch die Wissensermittlung oder Domänenwertverwaltung, durch das Hinzufügen einer Abgleichsrichtlinie, durch das Importieren von Wissen, Domänen oder Werten oder indem Sie die Standardwissensdatenbank, DQS-Daten, verwenden.|[Hinzufügen von Wissen zur Wissensdatenbank](../data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|Sie können ein Datenbeispiel in Bezug auf Kriterien, die für die Qualität der Daten gelten, analysieren.|[Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Importieren von Wissen in oder Exportieren von Wissen aus einer Wissensdatenbank.|[Importieren und Exportieren von Wissen](../data-quality-services/importing-and-exporting-knowledge.md)|  
|Erstellen einer einzelnen Domäne und Hinzufügen von Wissen zur Domäne.|[Verwalten einer Domäne](../data-quality-services/managing-a-domain.md)|  
|Erstellen einer Verbunddomäne und Hinzufügen von Wissen zur Domäne.|[Verwalten einer Verbunddomäne](../data-quality-services/managing-a-composite-domain.md)|  
  
  
