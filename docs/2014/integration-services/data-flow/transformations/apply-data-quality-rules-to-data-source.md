---
title: Anwenden von Datenqualitätsregeln auf eine Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 381b3ea1567b6d626953586cb1ce3b82c67ff809
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815232"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Anwenden von Datenqualitätsregeln auf eine Datenquelle
  Sie können mit Data Quality Services (DQS) Daten im Paketdatenfluss korrigieren, indem Sie eine Verbindung zwischen der DQS-Bereinigungstransformation und der Datenquelle herstellen. Weitere Informationen zu DQS finden Sie unter [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Weitere Informationen zu der Transformation finden Sie unter [DQS Cleansing Transformation](dqs-cleansing-transformation.md).  
  
 Wenn Sie Daten mit der DQS-Bereinigungstransformation verarbeiten, wird ein Data Quality-Projekt auf dem Data Quality-Server erstellt. Das Projekt wird mit dem Data Quality Client verwaltet. Weitere Informationen finden Sie unter [Verwalten von Data Quality-Projekten &#40;Öffnen, Entsperren, Umbenennen, Löschen&#41;](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>So korrigieren Sie Daten im Datenfluss  
  
1.  Erstellen eines Pakets.  
  
2.  Fügen Sie die DQS-Bereinigungstransformation hinzu, und konfigurieren Sie sie. Weitere Informationen finden Sie unter [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Verbinden Sie die DQS-Bereinigungstransformation mit einer Datenquelle.  
  
  
