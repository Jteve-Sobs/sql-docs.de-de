---
title: Filtern veröffentlichter Daten für die Mergereplikation| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fdfd7525ade2500ee144bb57c030350a532ded64
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901249"
---
# <a name="filter-published-data-for-merge-replication"></a>Filtern veröffentlichter Daten für die Mergereplikation
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Abgesehen von den statischen Zeilenfiltern und Spaltenfiltern, die Sie auch bei anderen Replikationstypen definieren können, ermöglicht die Mergereplikation die Verwendung von parametrisierten Zeilenfiltern und Joinfiltern. Weitere Informationen zu statischen Zeilenfiltern und Spaltenfiltern finden Sie unter [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 Die Mergereplikation wird in vielen Anwendungen zur Unterstützung mobiler Benutzer verwendet. Bei diesem Anwendungen gibt es meist eine große Zahl Abonnements, wobei jedes Abonnement ein eindeutiges Dataset empfängt. Parametrisierte Filter in Kombination mit Joinfiltern ermöglichen es einem Administrator, eine Veröffentlichung einzurichten (oder maximal eine kleine Zahl von Veröffentlichungen) und dabei verschiede Datasets bereitzustellen. Dadurch wird der Verwaltungsaufwand reduziert, der durch das Erstellen mehrerer Veröffentlichungen entsteht.  
  
-   Mit parametrisierten Filtern können verschiedene Partitionen von Daten an verschiedene Abonnenten gesendet werden, ohne dass mehrere Veröffentlichungen erstellt werden müssen. Eine Tabelle kann z. B. so gefiltert werden, dass Daten für einen bestimmten Vertriebsmitarbeiter tatsächlich nur für diesen Vertriebsmitarbeiter repliziert werden. Parametrisierte Filter bieten eine Vielzahl von Optionen, mit deren Hilfe Sie Filter zur Optimierung der Leistung und Ihren Daten- und Anwendungsanforderungen entsprechend perfekt anpassen können. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
-   Joinfilter werden in der Regel in Verbindung mit parametrisierten Filtern verwendet, um die Filterung auf verknüpfte Tabellen auszuweiten (sie können auch zusammen mit statischen Filtern verwendet werden). Der Vertriebsmitarbeiter benötigt z. B. meist auch Daten aus anderen Tabellen (z. B. Kunden oder Aufträge). Diese Daten können so gefiltert werden, dass der Vertriebsmitarbeiter nur die Daten zu seinen Kunden und Kundenaufträgen erhält. Weitere Informationen finden Sie unter [Join Filters](../../../relational-databases/replication/merge/join-filters.md).  
  
 Ein Filter muss die von der Replikation verwendete **rowguidcol** nicht einschließen, um Zeilen zu identifizieren. Standardmäßig ist dies die Spalte, die zum Zeitpunkt hinzugefügt wurde, als Sie die Mergereplikation eingerichtet haben, und sie heißt **rowguid**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
