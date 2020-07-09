---
title: Optimieren der Leistung durch bedingte Nachverfolgung von Löschvorgängen (Merge)
description: Hier erfahren Sie, wie Sie die Mergereplikationsleistung durch die bedingte Nachverfolgung von Löschvorgängen für SQL Server optimieren.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 28c20a2bd60c2f0ce557d2cd4d3776c393af82b2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882272"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a>Optimieren der Mergereplikationsleistung durch bedingtes Nachverfolgen von Löschvorgängen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Bei der Mergereplikation können Sie angeben, dass Löschvorgänge für einen oder mehrere Artikel nicht von Replikationstriggern oder in Systemtabellen nachverfolgt werden sollen. Wenn Sie diese Option für einen Artikel angeben, werden Löschvorgänge weder nachverfolgt, noch vom Verleger oder den Abonnenten repliziert. Diese Option steht zur Unterstützung verschiedener Anwendungsszenarien zur Verfügung, und soll dort zur Leistungsoptimierung beitragen, wo die Replikation von Löschvorgängen weder nötig noch wünschenswert ist. Die Leistung wird auf drei verschiedene Arten optimiert: die Metadaten der Löschvorgänge werden nicht gespeichert; die Löschvorgänge werden während der Synchronisierung nicht aufgezählt; die Löschvorgänge werden nicht auf dem Abonnenten repliziert oder angewendet.  
  
> [!NOTE]  
>  Damit nur herunterladbare Artikel verwendet werden können, muss die Veröffentlichung mindestens einen Kompatibilitätsgrad von 90RTM aufweisen.  
  
 Diese Option kann beim Erstellen einer Veröffentlichung angegeben werden, oder ein- bzw. ausgeschaltet werden, wenn eine Anwendung erfordert, dass bestimmte Löschvorgänge repliziert werden, andere jedoch nicht (z. B. Batchlöschvorgänge). In den folgenden Beispielen wird veranschaulicht, wie diese Option in einer Anwendung verwendet werden kann:  
  
-   In einer Anwendung für den Außendienst eines Unternehmens gibt es in der Regel Spalten wie **SalesOrderHeader**, **SalesOrderDetail** und **Product**. Die Bestellungen (Orders) werden auf dem Abonnenten eingegeben und auf den Verleger repliziert, welcher die Daten meistens an ein Fulfillment-System weitergibt. Viele Mitarbeiter im Außendienst benutzen Handheld-PCs mit begrenztem Speicherplatz; nachdem der Verleger die Bestellung erhalten hat, kann sie auf dem Abonnenten gelöscht werden. Der Löschvorgang wird nicht an den Verleger weitergegeben, da die Bestellung weiterhin im System aktiv bleiben soll.  
  
     In diesem Szenario würden die Löschvorgänge für die Tabellen **SalesOrderHeader** und **SalesOrderDetail** nicht nachverfolgt werden. Sie müssten jedoch für die **Product** -Tabelle nachverfolgt werden, denn sollte ein Produkt auf dem Verleger gelöscht werden, müsste dieser Löschvorgang an den Abonnenten gesendet werden, damit dessen Produktliste aktuell bleibt.  
  
-   Eine Anwendung könnte z. B. Vergangenheitsdaten in einer **TransactionHistory**-Tabelle speichern, aus der in regelmäßigen Abständen alle Datensätze gelöscht werden, die älter als ein Jahr sind. Die Tabelle könnte nun so gefiltert werden, dass Abonnenten nur Daten zu Transaktionen des laufenden Monats erhalten. Die monatlichen Batchlöschvorgänge zum Löschen älterer Daten auf dem Verleger sind für die Abonnenten irrelevant, würden jedoch trotzdem standardmäßig nachverfolgt und aufgelistet werden.  
  
     In diesem Szenario könnte die Aktivität auf dem System vor der Batchverarbeitung angehalten werden, damit die Anwendung die Nachverfolgung der Löschvorgänge deaktivieren kann. Ist die Batchverarbeitung abgeschlossen, kann die Nachverfolgung erneut aktiviert werden.  
  
> [!IMPORTANT]  
>  Wenn andere Prozesse weiterhin auf dem Verleger aktiv sind, müssen Sie sicherstellen, dass keine Löschvorgänge erfolgen, die an Abonnenten weitergegeben werden sollen, solange die Nachverfolgung deaktiviert ist.  
  
 **So geben Sie an, dass Löschvorgänge nicht nachverfolgt werden**  
  
-   Replikationsprogrammierung ([!INCLUDE[tsql](../../../includes/tsql-md.md)]): [Specify Merge Replication properties (Angeben von Mergereplikationseigenschaften)](../../../relational-databases/replication/merge/specify-merge-replication-properties.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Article Options for Merge Replication](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
