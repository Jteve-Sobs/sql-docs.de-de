---
title: Article Options for Transactional Replication | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 61e8bad960da0ff90f77e0253f39c6257ddb9c2c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86904014"
---
# <a name="article-options-for-transactional-replication"></a>Artikeloptionen für die Transaktionsreplikation
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Für Artikel in Transaktionsveröffentlichungen stehen eine Reihe von Optionen zur Verfügung. Bei der Transaktionsreplikation haben Sie folgende Möglichkeiten:  
  
-   Sie können angeben, wie Änderungen vom Verleger an Abonnenten weitergegeben werden. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Sie können angeben, dass die Ausführung einer gespeicherten Prozedur repliziert wird. Dies ist bei der Replikation der Ergebnisse von wartungsorientierten gespeicherten Prozeduren hilfreich, die sich möglicherweise auf große Datenmengen auswirken. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Sie können Schemaoptionen angeben, beispielsweise ob Einschränkungen und Trigger auf den Abonnenten kopiert werden. Weitere Informationen finden Sie unter [Angeben von Schemaoptionen](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Sie können Zeilenfilter und Spaltenfilter verwenden. Das Filtern von Tabellenartikeln ermöglicht es Ihnen, Datenpartitionen zu erstellen, die veröffentlicht werden können. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
